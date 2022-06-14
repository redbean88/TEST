{
    "type": "AdaptiveCard",
    "body": [
        {
            "type": "TextBlock",
            "weight": "Bolder",
            "text": "${title}",
            "wrap": true,
            "size": "ExtraLarge"
        },
        {
            "type": "TextBlock",
            "wrap": true,
            "isSubtle": true,
            "text": "Created {{DATE(${string(createdUtc)}, SHORT)}}",
            "spacing": "None"
        },
        {
            "type": "ColumnSet",
            "columns": [
                {
                    "type": "Column",
                    "items": [
                        {
                            "type": "FactSet",
                            "facts": [
                                {
                                    "$data": "${partners}",
                                    "title": "${key}",
                                    "value": "${value}"
                                }
                            ]
                        }
                    ],
                    "width": "stretch",
                    "horizontalAlignment": "Left"
                }
            ]
        },
        {
            "type": "TextBlock",
            "wrap": true,
            "text": "${subtitle}",
            "weight": "Default",
            "spacing": "Medium",
            "separator": true,
            "size": "Large"
        },
        {
            "type": "FactSet",
            "facts": [
                {
                    "$data": "${properties}",
                    "title": "${key}",
                    "value": "${value}"
                }
            ]
        }
    ],
    "actions": [
        {
            "type": "Action.OpenUrl",
            "title": "View",
            "url": "${viewUrl}"
        }
    ],
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "version": "1.3"
}
