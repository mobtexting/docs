# Rcs Template

## API Endpoint

```
{domain}/api/{version}/
```

## View Template

View all the Templates list.

#### GET

```
{endpoint}rcs/templates
```

#### PARAMETERS

| name           | optional | value                                           |
| -------------- | -------- | ----------------------------------------------- |
| filter[id]     | Yes      | The id is template id                           |
| filter[name]   | Yes      | The name is template name                       |
| filter[type]   | Yes      | The type is template type  (template)           |
| filter[status] | Yes      | (0 is Draft), (1 is Approved) ,(2 is Pending)   |

#### Example Request

#code "{version}/_code/rcs/templates/view.json"

Kindly replace the token with your respective access_token and other params.

#### Example Response

```json
{
    "status": "OK",
    "code": 200,
    "message": "Templates List",
    "data": [
        {
            "id": "2cf9e59f-d4f1-47ba-81d3-a288f31ca164",
            "name": "text_template",
            "number": "91861xxxxxxx",
            "type": "text",
            "category": "Account",
            "language": "English",
            "payload": "{\"type\":\"text\",\"payload\":
            {\"text\":\"Hi,This is Rcs text template message.\",\"language\":\"en\"}}",
            "status": 1,
            "is_conversation": 1,
            "created_at": "2023-20-08T10:41:30.000000Z",
            "updated_at": "2023-20-08T10:41:30.000000Z"
        }
    ],
    "links": {
        "first": "{endpoint}rcs/templates?page=1",
        "last": "{endpoint}rcs/templates?page=1",
        "prev": null,
        "next": null
    },
    "meta": {
        "current_page": 1,
        "from": 1,
        "last_page": 1,
        "links": [
            {
                "url": null,
                "label": "&laquo; Previous",
                "active": false
            },
            {
                "url": "{endpoint}rcs/templates?page=1",
                "label": "1",
                "active": true
            },
            {
                "url": null,
                "label": "Next &raquo;",
                "active": false
            }
        ],
        "path": "{endpoint}rcs/templates",
        "per_page": 15,
        "to": 1,
        "total": 1
    }
}
```

## Show Template

Show the Template list.

#### GET

```
{endpoint}rcs/templates/{template_id}
```

#### Example Request

#code "{version}/_code/rcs/templates/show.json"

Kindly replace the template_id.

### Example Response

```json
{
    "status": "OK",
    "code": 200,
    "message": "Templates List",
    "data": {
        "id": "2cf9e59f-d4f1-47ba-81d3-a288f31ca164",
        "name": "text_template",
        "number": "91861xxxxxxx",
        "type": "text",
        "category": "Account",
        "language": "English",
        "payload": "{\"type\":\"text\",\"payload\":
        {\"text\":\"Hi,This is Rcs text template message.\",
        \"language\":\"en\"}}",
        "status": 1,
        "is_conversation": 1,
        "created_at": "2023-20-08T10:41:30.000000Z",
        "updated_at": "2023-20-08T10:41:30.000000Z"
    }
}
```

## Create Templates

#### POST

```
{endpoint}rcs/templates
```

#### REQUIRED PARAMETERS

| name            | description                                                     | Type                  | Required |
| --------------- | --------------------------------------------------------------- | --------------------- | -------- |
| type            | value should be `template`                                      | `string`              | Yes      |
| name            | name should be a alphanumeric                                   | `string`,`integer`    | Yes      |
| category        | template category names(`text_message`,`rich_card`,`carousel`)  | `string`              | Yes      |
| language        | Example : `eu`, `en_US`                                         | `string`              | Yes      |
| number          | agent number Ex:(91861xxxxxxxx)                                 | `string` or `integer` | Yes      |
| is_conversation | value is (1 auto approve) or (0 admin will approve), default(0) | `integer`             | Yes      |

**_NOTE:_** Pass variables in `@{{}}` variables name should be different ex: `{{name}}`, `@{{email}}` and should be `alphabetic` or `alphanumeric`

## Text Type

#### PARAMETERS

| name                | description                                                 | Type     | Required |
| ------------------- | ----------------------------------------------------------- | -------- | -------- |
| payload.text        | content message with variables(optional) like @{{name}} . . | `string` | Yes      |
| payload.body_params | replaces the variables values Ex: ['name']                  | `array`  | No       |

### Example Request

#code "{version}/_code/rcs/templates/create.json"

### Example Response

```
{
    "status": "OK",
    "code": 200,
    "message": "Template created successfully.",
    "data": {
        "id": "3b58b499-e184-4cdf-9226-8ddae27e0821",
        "name": "text123",
        "number": "91861xxxxxxx",
        "alias": "text123",
        "type": "template",
        "category": "TEXT_MESSAGE",
        "language": "English",
        "payload": "{\"type\":\"template\",\"payload\":{\"body\":{\"type\":\"text\",\"payload\":{\"text\":\"do you like rcs?\"}}}}",
        "status": 1,
        "is_conversation": 1,
        "created_at": "2023-02-23T05:56:58.000000Z",
        "updated_at": "2023-02-23T05:56:58.000000Z"
    }
}
```

## Interactive Type

#### PARAMETERS

| name                    | description       | Type     | Required |
| ----------------------- | ----------------- | -------- | -------- |
| payload.body            | body text message | `object` | Yes      |
| payload.header          | optional          | `object` | No       |
| payload.footer          | optional          | `object` | No       |
| payload.choices         | optional          | `object` | No       |
| payload.choices.replies | optional          | `object` | Yes      |

### Example Request

```
curl -X POST \
  '{endpoint}rcs/templates' \
  -H 'authorization: Bearer 5b02112fb7xxxxxxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "type": "template",
    "name": "text12311",
    "language": "en",
    "category": "text_message",
    "number": "91861xxxxxxx",
    "payload": {
        "header": {
            "type": "text",
            "payload": {
                "text": "header text"
            }
        },
        "body": {
            "type": "text",
            "payload": {
                "text": "do you like rcs?"
            }
        },
        "footer": {
            "type": "text",
            "payload": {
                "text": "footer text"
            }
        },
        "choices": {
            "replies": [
                {
                    "type": "text",
                    "payload": {
                        "text": "yes",
                        "content": "yes"
                    }
                },
                {
                    "type": "text",
                    "payload": {
                        "text": "no",
                        "content": "No"
                    }
                }
            ]
        }
    }
}'
```

### Example Response

```
{
    "status": "OK",
    "code": 200,
    "message": "Template created successfully.",
    "data": {
        "id": "232b8245-17f4-4808-acf9-6f43dc7f3af2",
        "name": "text12311",
        "number": "91861xxxxxxx",
        "alias": "text12311",
        "type": "template",
        "category": "TEXT_MESSAGE",
        "language": "English",
        "payload": "{\"type\":\"template\",\"payload\":
        {\"header\":{\"type\":\"text\",\"payload\":{\"text\":\"header text\"}},
        \"body\":{\"type\":\"text\",\"payload\":{\"text\":\"do you like rcs?\"}},
        \"footer\":{\"type\":\"text\",\"payload\":{\"text\":\"footer text\"}},
        \"choices\":{\"replies\":
        [{\"type\":\"text\",\"payload\":{\"text\":\"yes\",\"content\":\"yes\"}},
        {\"type\":\"text\",\"payload\":{\"text\":\"no\",\"content\":\"No\"}}]}}}",
        "status": 1,
        "created_at": "2023-02-23T05:58:34.000000Z",
        "updated_at": "2023-02-23T05:58:34.000000Z"
    }
}
```

## Media Type

#### PARAMETERS

| name                     | description                             | Type     | Required |
| ------------------------ | --------------------------------------- | -------- | -------- |
| payload.type             | `image`, `video`, `audio` or `document` | `string` | Yes      |
| payload.payload          | payload object                          | `object` | Yes      |
| payload.payload.url      | proper link url                         | `string` | Yes      |
| payload.payload.filename | optional                                | `string` | No       |
| payload.payload.caption  | optional                                | `string` | No       |

### Example Request

```
curl -X POST \
  '{endpoint}rcs/templates' \
  -H 'authorization: Bearer 5b02112fb7xxxxxxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "type": "template",
    "name": "media123",
    "language": "en",
    "category": "rich_card",
    "number": "91861xxxxxxx",
    "payload": {
        "type": "image",
        "payload": {
            "url": "https://picsum.photos/id/237/200/300",
            "filename": "filename",
            "height": "MEDIUM_HEIGHT"
        }
    }
}'
```

### Example Response

```
{
    "status": "OK",
    "code": 200,
    "message": "Template created successfully.",
    "data": {
        "id": "9f57036a-475b-4d25-8434-bdf23b7e680b",
        "name": "media123",
        "number": "91861xxxxxxx",
        "alias": "media123-1",
        "type": "template",
        "category": "RICH_CARD",
        "language": "English",
        "payload": "{\"type\":\"template\",\"payload\":
        {\"url\":\"https:\\/\\/picsum.photos\\/id\\/237\\/200\\/300\",
        \"filename\":\"filename\",\"height\":\"MEDIUM_HEIGHT\"}}",
        "status": 1,
        "created_at": "2023-02-23T06:01:03.000000Z",
        "updated_at": "2023-02-23T06:01:03.000000Z"
    }
}
```

## Card Type

#### PARAMETERS

| name                        | description                                                      | Type     | Required |
| --------------------------- | ---------------------------------------------------------------- | -------- | -------- |
| payload.title               | cart title                                                       | `string` | Yes      |
| payload.description         | cart description                                                 | `string` | Yes      |
| payload.body                | card body                                                        | `object` | Yes      |
| payload.body.type           | only type value is `image`                                       | `string` | Yes      |
| payload.body.payload        | payload object                                                   | `object` | No       |
| payload.body.payload.url    | proper link url                                                  | `string` | Yes      |
| payload.body.payload.height | Height of the card SHORT [112 DP], MEDIUM [168 DP], TALL[264 DP] | `string` | Yes      |
| payload.choices             | optional                                                         | `object` | No       |
| payload.choices.replies     | optional                                                         | `object` | No       |
| payload.choices.actions     | optional                                                         | `object` | No       |

### Example Request

```
curl -X POST \
  '{endpoint}rcs/templates' \
  -H 'authorization: Bearer 5b02112fb7xxxxxxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "type": "template",
    "name": "card_demo",
    "language": "en",
    "category": "rich_card",
    "number": "91861xxxxxxx",
    "payload": {
        "title": "This is the card title",
        "description": "This is the card description",
        "body": {
            "type": "video",
            "payload": {
                "url": "https://domain-name.com/your_content_path.mp4",
                "height": "MEDIUM_HEIGHT"
            }
        },
        "choices": {
            "replies": [
                {
                    "type": "text",
                    "payload": {
                        "text": "yes",
                        "content": "yes"
                    }
                },
                {
                    "type": "text",
                    "payload": {
                        "text": "No",
                        "content": "no"
                    }
                }
            ],
            "actions": [
                {
                    "type": "url",
                    "payload": {
                        "title": "Click Here",
						"url": "https://example.com"
                    }
                },
                {
                    "type": "dial",
                    "payload": {
                        "title": "Click Here",
						"phone_number": "+91901995xxxx"
                    }
                },
                {
                    "type": "location",
                    "payload": {
                        "latitude": 12.912985,
						"longitude": 77.599505
                    }
                }
            ]
        }
    }
}'
```

### Example Response

```
{
    "status": "OK",
    "code": 200,
    "message": "Template created successfully.",
    "data": {
        "id": "5565ef13-8843-4f02-94f2-9a510140dadd",
        "name": "card_demo",
        "number": "91861xxxxxxx",
        "alias": "card-demo",
        "type": "template",
        "category": "RICH_CARD",
        "language": "English",
        "payload": "{\"type\":\"template\",\"payload\":
        {\"title\":\"This is the card title\",
        \"description\":\"This is the card description\",\"body\":{\"type\":\"video\",\"payload\":
        {\"url\":\"https:\\/\\/domain-name.com\\/your_content_path.mp4\",
        \"height\":\"MEDIUM_HEIGHT\"}},\"choices\":{\"replies\":[{\"type\":\"text\",\"payload\":
        {\"text\":\"yes\",\"content\":\"yes\"}},
        {\"type\":\"text\",\"payload\":{\"text\":\"No\",\"content\":\"no\"}}],
        \"actions\":[{\"type\":\"url\",\"payload\":{\"title\":\"Click Here\",\"url\":
        \"https:\\/\\/example.com\"}},{\"type\":\"dial\",\"payload\":
        {\"title\":\"Click Here\",\"phone_number\":\"+91901995xxxx\"}},
        {\"type\":\"location\",\"payload\":{\"latitude\":12.912985,\"longitude\":77.599505}}]}}}",
        "status": 1,
        "created_at": "2023-02-23T06:02:38.000000Z",
        "updated_at": "2023-02-23T06:02:38.000000Z"
    }
}
```

## Carousel Type

#### PARAMETERS

| name          | description     | Type     | Required |
| ------------- | --------------- | -------- | -------- |
| payload.cards | cards id values | `string` | Yes      |

### Example Request

```
curl -X POST \
  '{endpoint}rcs/templates' \
  -H 'authorization: Bearer 5b02112fb7xxxxxxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "type": "template",
    "name": "carousel_demo",
    "language": "en",
    "category": "carousel",
    "number": "91861xxxxxxx",
    "payload": {
        "cards": [
            {
                "title": "This is the first card title",
                "description": "This is the first card description",
                "body": {
                    "type": "video",
                    "payload": {
                        "url": "http://commondatastorage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4",
                        "filename": "BigBuckBunny.mp4",
                        "height": "TALL"
                    }
                },
                "choices": {
                    "replies": [
                        {
                            "type": "text first",
                            "payload": {
                                "text": "yes",
                                "content": "yes"
                            }
                        },
                        {
                            "type": "text first2",
                            "payload": {
                                "text": "no",
                                "content": "No"
                            }
                        }
                    ],
                    "actions": [
                        {
                            "type": "url",
                            "payload": {
                                "title": "Click Here",
                                "url": "https://example.com"
                            }
                        },
                        {
                            "type": "dial",
                            "payload": {
                                "title": "Click Here",
                                "phone_number": "+9178990XXXX"
                            }
                        },
                        {
                            "type": "location",
                            "payload": {
                                "latitude": 12.912985,
                                "longitude": 77.599505
                            }
                        }
                    ]
                }
            },
            {
                "title": "This is the second card title",
                "description": "This is the second card description",
                "body": {
                    "type": "image",
                    "payload": {
                        "url": "https://www.domain.com/app/uploads/domain-logo.png",
                        "height": "TALL"
                    }
                },
                "choices": {
                    "replies": [
                        {
                            "type": "text second",
                            "payload": {
                                "text": "yes",
                                "content": "yes"
                            }
                        },
                        {
                            "type": "text second2",
                            "payload": {
                                "text": "no",
                                "content": "No"
                            }
                        }
                    ],
                    "actions": [
                        {
                            "type": "url",
                            "payload": {
                                "title": "Click Here",
                                "url": "https://example.com"
                            }
                        },
                        {
                            "type": "dial",
                            "payload": {
                                "title": "Click Here",
                                "phone_number": "+9178990XXXXX"
                            }
                        },
                        {
                            "type": "location",
                            "payload": {
                                "latitude": 12.912985,
                                "longitude": 77.599505
                            }
                        }
                    ]
                }
            }
        ]
    }
}'
```

### Example Response

```
{
    "status": "OK",
    "code": 200,
    "message": "Template created successfully.",
    "data": {
        "id": "2e84cd9e-9ee1-453b-9a73-a7caf8c29ff2",
        "name": "carousel_demo",
        "number": "91861xxxxxxx",
        "alias": "carousel-demo",
        "type": "template",
        "category": "carousel",
        "language": "English",
        "payload": "{\"type\":\"template\",\"payload\":{\"cards\":[{\"title\":\"This is the first card title\",\"description\":\"This is the first card description\",\"body\":{\"type\":\"video\",\"payload\":{\"url\":\"http:\\/\\/commondatastorage.googleapis.com\\/gtv-videos-bucket\\/sample\\/BigBuckBunny.mp4\",\"filename\":\"BigBuckBunny.mp4\",\"height\":\"TALL\"}},\"choices\":{\"replies\":[{\"type\":\"text first\",\"payload\":{\"text\":\"yes\",\"content\":\"yes\"}},{\"type\":\"text first2\",\"payload\":{\"text\":\"no\",\"content\":\"No\"}}],\"actions\":[{\"type\":\"url\",\"payload\":{\"title\":\"Click Here\",\"url\":\"https:\\/\\/example.com\"}},{\"type\":\"dial\",\"payload\":{\"title\":\"Click Here\",\"phone_number\":\"+9178990XXXX\"}},{\"type\":\"location\",\"payload\":{\"latitude\":12.912985000000001,\"longitude\":77.599504999999994}}]}},{\"title\":\"This is the second card title\",\"description\":\"This is the second card description\",\"body\":{\"type\":\"image\",\"payload\":{\"url\":\"https:\\/\\/www.domain.com\\/app\\/uploads\\/domain-logo.png\",\"height\":\"TALL\"}},\"choices\":{\"replies\":[{\"type\":\"text second\",\"payload\":{\"text\":\"yes\",\"content\":\"yes\"}},{\"type\":\"text second2\",\"payload\":{\"text\":\"no\",\"content\":\"No\"}}],\"actions\":[{\"type\":\"url\",\"payload\":{\"title\":\"Click Here\",\"url\":\"https:\\/\\/example.com\"}},{\"type\":\"dial\",\"payload\":{\"title\":\"Click Here\",\"phone_number\":\"+9178990XXXXX\"}},{\"type\":\"location\",\"payload\":{\"latitude\":12.912985000000001,\"longitude\":77.599504999999994}}]}}]}}",
        "status": 1,
        "created_at": "2023-02-23T06:08:46.000000Z",
        "updated_at": "2023-02-23T06:08:46.000000Z"
    }
}
```

## Update Templates

#### PUT

```
{endpoint}rcs/templates/{template_id}
```

#### PARAMETERS

| name        | description                                        | Type                  | Required |
| ----------- | -------------------------------------------------- | --------------------- | -------- |
| template id | created template id                                | `string`              | Yes      |
| type        | value should be  `template`                                  | `string`              | Yes      |
| name        | created template name (can not be change)          | `string`              | Yes      |
| category    | template category (`text_message`,`rich_card`,`carousel`)                  | `string`              | Yes      |
| language    | example : `eu`, `en_US` (can be change)            | `string`              | Yes      |
| number      | agent number Ex:(91861xxxxxxxx) (can be change)    | `string` or `integer` | Yes      |
| payload     | payload content (can be change)                    | `object`              | Yes      |

### Example Request

#code "{version}/_code/rcs/templates/edit.json"

### Example Response

```
{
    "status": "OK",
    "code": 200,
    "message": "Template updated successfully.",
    "data": {
        "id": "3b58b499-e184-4cdf-9226-8ddae27e0821",
        "name": "text123",
        "number": "91861xxxxxxx",
        "alias": "text123",
        "type": "template",
        "category": "TEXT_MESSAGE",
        "language": "English",
        "payload": "{\"type\":\"template\",\"payload\":{\"body\":{\"type\":\"text\",\"payload\":{\"text\":\"do you like rcs?\"}}}}",
        "status": 1,
        "created_at": "2023-02-23T05:56:58.000000Z",
        "updated_at": "2023-02-23T06:27:29.000000Z"
    }
}
```

## Delete Templates

#### DELETE

```
{endpoint}rcs/templates/{id}
```

Replace the {id} with the actual id of the template that you would like to delete.

#### Example Request

#code "{version}/_code/rcs/templates/delete.json"

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Template Successfully Deleted",
  "data": []
}
```
