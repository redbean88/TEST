{
    "type": "message",
    "attachments": [
        {
            "contentType": "application/vnd.microsoft.card.adaptive",
            "content": {
                "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
                "type": "AdaptiveCard",
                "version": "1.5",
                "body": [
                    {
                        "type": "Container",
                        "items": [
                            {
                                "type": "TextBlock",
                                "text": "제목",
                                "weight" : "Bolder",
                                "size" : "ExtraLarge"
                            }
                        ]
                    },
                    {
                        "type": "Container",
                        "items": [
                            {
                                "type": "TextBlock",
                                "text": "2022년 6월 13일(월) 10:29:59",
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
                                                "size": "Large",
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
                                                        "value": "127 원"
                                                    },
                                                    {
                                                        "title": "출금액",
                                                        "value": "129 원"
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
                                "url": "https://inside.linkhub.kr/Point/V2/Settle/DashBoard",
                                "title": "결제관리 이동",
                                "tooltip": "인사이드 결제관리 화면으로 이동합니다.",
                                "isEnabled": false
                            }
                        ]
                    }
                ]
            }
        }
    ]
}
