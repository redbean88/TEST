package com.amqp;

import java.util.Arrays;
import java.util.HashMap;
import java.util.List;
import java.util.Map;

import javax.annotation.PostConstruct;

import org.springframework.amqp.AmqpRejectAndDontRequeueException;
import org.springframework.amqp.core.AmqpAdmin;
import org.springframework.amqp.core.Binding;
import org.springframework.amqp.core.BindingBuilder;
import org.springframework.amqp.core.DirectExchange;
import org.springframework.amqp.core.Message;
import org.springframework.amqp.core.Queue;
import org.springframework.amqp.core.QueueBuilder;
import org.springframework.amqp.rabbit.annotation.RabbitListener;
import org.springframework.amqp.rabbit.config.RetryInterceptorBuilder;
import org.springframework.amqp.rabbit.config.SimpleRabbitListenerContainerFactory;
import org.springframework.amqp.rabbit.connection.CachingConnectionFactory;
import org.springframework.amqp.rabbit.connection.ConnectionFactory;
import org.springframework.amqp.rabbit.core.RabbitAdmin;
import org.springframework.amqp.rabbit.core.RabbitTemplate;
import org.springframework.amqp.rabbit.listener.ConditionalRejectingErrorHandler;
import org.springframework.amqp.rabbit.listener.RabbitListenerEndpointRegistry;
import org.springframework.amqp.rabbit.retry.MessageRecoverer;
import org.springframework.amqp.rabbit.retry.RejectAndDontRequeueRecoverer;
import org.springframework.amqp.support.converter.Jackson2JsonMessageConverter;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.classify.BinaryExceptionClassifier;
import org.springframework.context.ConfigurableApplicationContext;
import org.springframework.context.annotation.Bean;
import org.springframework.messaging.handler.annotation.Header;
import org.springframework.messaging.handler.annotation.Payload;
import org.springframework.retry.RetryContext;
import org.springframework.retry.backoff.BackOffPolicy;
import org.springframework.retry.backoff.ExponentialBackOffPolicy;
import org.springframework.retry.policy.SimpleRetryPolicy;
import org.springframework.util.ErrorHandler;

import com.fasterxml.jackson.databind.ObjectMapper;
import com.fasterxml.jackson.datatype.jsonorg.JsonOrgModule;

import lombok.extern.slf4j.Slf4j;

@SpringBootApplication
@Slf4j
public class AmqpApplication
{

    protected static final String X_ATTEMPTS_HEADER = "x-attempts";
    protected static final String X_LAST_ATTEMPT_DATE_HEADER = "x-last-attempt-date";

    public static void main(String[] args) throws InterruptedException
    {
        ConfigurableApplicationContext context = SpringApplication.run(AmqpApplication.class, args);
        context.close();
        System.exit(0);
    }

    private String host = "localhost";

    private Integer port = 5672;

    private String vhost = "/";

    private String username = "guest";

    private String password = "guest";

    private String exchangeName = "common-exchange";

    @Autowired
    private RabbitTemplate rabbitTemplate;

    @Bean
    public SimpleRabbitListenerContainerFactory rabbitListenerContainerFactory()
    {
        SimpleRabbitListenerContainerFactory factory = new SimpleRabbitListenerContainerFactory();
        factory.setConnectionFactory(connectionFactory());
        factory.setAdviceChain(retryOperationsInterceptor().build());
        factory.setErrorHandler(new ConditionalRejectingErrorHandler());
        factory.setAutoStartup(true);
        factory.setMessageConverter(new MessageConverter());
        return factory;
    }

    /**
     * Configures the connection factory using the configured values
     * 
     * @return Connection factory to use to connect to rabbitmq and send events
     **/
    private ConnectionFactory connectionFactory()
    {
        CachingConnectionFactory factory = new CachingConnectionFactory(host, port);

        factory.setRequestedHeartBeat(30);
        factory.setConnectionTimeout(30000);
        factory.setChannelCacheSize(10);

        factory.setVirtualHost(vhost);
        factory.setUsername(username);
        factory.setPassword(password);
        return factory;
    }

    @Bean
    public RetryInterceptorBuilder<?> retryOperationsInterceptor()
    {
        RetryInterceptorBuilder<?> builder = RetryInterceptorBuilder.stateless();
        builder.retryPolicy(new MyRetryPolicy(3, retryableClassifier()));
        builder.backOffPolicy(backoffPolicy());

        MessageRecoverer recoverer = new RejectAndDontRequeueRecoverer();
        builder.recoverer(recoverer);
        return builder;
    }

    @Bean
    public BackOffPolicy backoffPolicy()
    {
        ExponentialBackOffPolicy backoffPolicy = new ExponentialBackOffPolicy();
        backoffPolicy.setInitialInterval(1000);
        backoffPolicy.setMaxInterval(10000);
        backoffPolicy.setMultiplier(1.5);
        return backoffPolicy;
    }

    @Bean
    public Map<Class<? extends Throwable>, Boolean> retryableClassifier()
    {
        Map<Class<? extends Throwable>, Boolean> retryableClassifier = new HashMap<>();
        retryableClassifier.put(AmqpRejectAndDontRequeueException.class, false);
        retryableClassifier.put(Exception.class, true);
        return retryableClassifier;
    }

    @Bean
    public Queue queueA()
    {
        return QueueBuilder.durable("a").withArgument("x-dead-letter-exchange", "a")
                .withArgument("x-dead-letter-routing-key", "a-dead-letter").build();
    }

    @Bean
    public Queue queueB()
    {
        return QueueBuilder.durable("b").withArgument("x-dead-letter-exchange", "b")
                .withArgument("x-dead-letter-routing-key", "b-dead-letter").build();
    }

    @Bean
    Queue DeadLetterQueueA()
    {
        return QueueBuilder.durable("a-dead-letter").build();
    }

    @Bean
    Queue DeadLetterQueueB()
    {
        return QueueBuilder.durable("b-dead-letter").build();
    }

    /**
     * Required for executing adminstration functions against an AMQP Broker
     */
    @Bean
    public AmqpAdmin amqpAdmin(RabbitListenerEndpointRegistry registry,
            SimpleRabbitListenerContainerFactory rabbitListenerContainerFactory)
    {
        //@// @formatter:off
        RabbitAdmin admin = new RabbitAdmin(connectionFactory());
        admin.declareQueue(queueA());
        admin.declareQueue(queueB());
        registry.start();
        return admin;
    }

    /**
     * The following is a complete declaration of an exchange, a queue and a
     * exchange-queue binding
     */
    @Bean
    public DirectExchange directExchange()
    {
        return new DirectExchange(exchangeName, true, false);
    }

    @Bean
    public List<Binding> exchangeBinding()
    {
        // Important part is the routing key -- this is just an example
        return Arrays.asList(
                BindingBuilder.bind(queueA()).to(directExchange()).with("a"),
                BindingBuilder.bind(DeadLetterQueueA()).to(directExchange())
                        .with("a"),
                        BindingBuilder.bind(queueB()).to(directExchange()).with("b"),
                        BindingBuilder.bind(DeadLetterQueueB()).to(directExchange())
                                .with("b"));
    }



    @Bean
    public RabbitTemplate rabbitTemplate()
    {
        // Add the object mapper to the converter
        ObjectMapper objectMapper = new ObjectMapper();
        objectMapper.registerModule(new JsonOrgModule());

        // Add the object mapper to the converter
        RabbitTemplate template = new RabbitTemplate(connectionFactory());
        template.setMessageConverter(new Jackson2JsonMessageConverter(objectMapper));

        template.setExchange(exchangeName);

        return template;
    }

    @PostConstruct
    public void sendMessages() throws InterruptedException
    {
        rabbitTemplate.convertAndSend(exchangeName, "a", new BeanObject().setName("a"));
        rabbitTemplate.convertAndSend(exchangeName, "b", new BeanObject().setName("b"));
    }

    @RabbitListener(queues = "a")
    public void aListener(@Payload BeanObject payload, Message message,
            @Header(required = false, name = X_ATTEMPTS_HEADER, defaultValue = "0") Integer attempts)
    {
        beforeProcessing(payload,message,attempts);
        throw new RuntimeException();
    }

    @RabbitListener(queues = "b")
    public void bListener(@Payload BeanObject payload, Message message,
            @Header(required = false, name = X_ATTEMPTS_HEADER, defaultValue = "0") Integer attempts)
    {
        beforeProcessing(payload,message,attempts);
        throw new AmqpRejectAndDontRequeueException("");
    }

    private void beforeProcessing(BeanObject payload, Message message,
            @Header(required = false, name = X_ATTEMPTS_HEADER, defaultValue = "0") Integer attemptNo)
    {

        //// @formatter:off
        attemptNo++;// Increment

        message.getMessageProperties().getHeaders().put(X_ATTEMPTS_HEADER, attemptNo);//update attempts header
     // @formatter:on
        log.info(
                "bean: {}, attemptNo: {}",
                payload, attemptNo);
    }

    private static class MyRetryPolicy extends SimpleRetryPolicy
    {

        private BinaryExceptionClassifier retryableClassifier;
        private int maxAttempts;

        @Override
        public boolean canRetry(RetryContext context)
        {
            Throwable t = context.getLastThrowable();
            return (t == null || retryForException(t.getCause())) && context.getRetryCount() < maxAttempts;
        }

        public MyRetryPolicy(int maxAttempts, Map<Class<? extends Throwable>, Boolean> retryableExceptions)
        {
            this.maxAttempts = maxAttempts;
            this.retryableClassifier = new BinaryExceptionClassifier(retryableExceptions, false);
        }

        private boolean retryForException(Throwable ex)
        {
            return this.retryableClassifier.classify(ex);
        }
    }

    public static class MyErrorHandler implements ErrorHandler
    {

        @Override
        public void handleError(Throwable t)
        {
            if (!this.causeChainContainsARADRE(t))
            {
                throw new AmqpRejectAndDontRequeueException("Error Handler converted exception to fatal", t);
            }
        }

        private boolean causeChainContainsARADRE(Throwable t)
        {
            Throwable cause = t.getCause();
            while (cause != null)
            {
                if (cause instanceof AmqpRejectAndDontRequeueException)
                {
                    return true;
                }
                cause = cause.getCause();
            }
            return false;
        }

    }

}
