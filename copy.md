{
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.5",
    "body": [
        {
            "type": "Container",
            "items": [
                {
                    "type": "TextBlock",
                    "text": "{{DATE(2019-05-03T20:00:00+00:00, SHORT)}} {{TIME(2019-05-03T20:00:00+00:00)}}",
                    "wrap": true
                }
            ]
        },
        {
            "type": "Container",
            "spacing": "None",
            "items": [
                {
                    "type": "ColumnSet",
                    "columns": [
                        {
                            "type": "Column",
                            "width": "stretch",
                            "items": [
                                {
                                    "type": "TextBlock",
                                    "text": "[대기 -> 완료]",
                                    "size": "ExtraLarge",
                                    "wrap": true
                                },
                                {
                                    "type": "TextBlock",
                                    "text": "입금자 : 홍길동",
                                    "spacing": "None",
                                    "wrap": true
                                }
                            ]
                        },
                        {
                            "type": "Column",
                            "width": "auto",
                            "items": [
                                {
                                    "type": "FactSet",
                                    "facts": [
                                        {
                                            "title": "입금액",
                                            "value": "127.42 원"
                                        },
                                        {
                                            "title": "출금액",
                                            "value": "129.43 원"
                                        },
                                        {
                                            "title": "잔액",
                                            "value": "1,000,000 원"
                                        }
                                    ]
                                }
                            ]
                        }
                    ]
                }
            ]
        },
        {
            "type": "ActionSet",
            "actions": [
                {
                    "type": "Action.OpenUrl",
                    "style": "positive",
                    "url": "http://www.nmaver.com",
                    "title": "결제관리",
                    "tooltip": "인사이드 결제관리 화면으로 이동합니다.",
                    "isEnabled": false
                }
            ]
        }
    ]
