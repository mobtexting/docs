# Whatsapp Template

## API Endpoint

```
{domain}/api/{version}/
```

## View Template

View all the Templates list.

#### GET

```
{endpoint}whatsapp/templates
```

#### Example Filter

```
{endpoint}whatsapp/templates?filter[name]=template_name
```

#### PARAMETERS

| name           | optional | value                                                |
| -------------- | -------- | ---------------------------------------------------- |
| filter[id]     | Yes      | The id is template id                                |
| filter[name]   | Yes      | The name is template name                            |
| filter[type]   | Yes      | The type is template type EX: (text, template)       |
| filter[status] | Yes      | (1 is Approved), (2 are Pending) and (3 is Rejected) |

#### Example Request

```
curl -X GET \
  '{endpoint}whatsapp/templates' \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 5b02112fb7xxxxxxxxx'
```

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
            "alias": "text-template",
            "number": "91861xxxxxxx",
            "type": "text",
            "category": "marketing",
            "language": "English",
            "body": "Hi,This is WhatsApp text template message.",
            "payload": "{\"type\":\"text\",\"payload\":{\"text\":\"Hi,This is WhatsApp text template message.\",\"language\":\"en\"}}",
            "status": "Pending",
            "created_at": "2023-02-08T10:41:30.000000Z",
            "updated_at": "2023-02-08T10:41:30.000000Z"
        }
    ],
    "links": {
        "first": "{endpoint}whatsapp/templates?page=1",
        "last": "{endpoint}whatsapp/templates?page=1",
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
                "url": "{endpoint}whatsapp/templates?page=1",
                "label": "1",
                "active": true
            },
            {
                "url": null,
                "label": "Next &raquo;",
                "active": false
            }
        ],
        "path": "{endpoint}whatsapp/templates",
        "per_page": 15,
        "to": 1,
        "total": 1
    }
  ],
  "links": {
    "first": "{endpoint}whatsapp/templates?page=1",
    "last": "{endpoint}whatsapp/templates?page=1",
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
        "url": "{endpoint}whatsapp/templates?page=1",
        "label": "1",
        "active": true
      },
      {
        "url": null,
        "label": "Next &raquo;",
        "active": false
      }
    ],
    "path": "{endpoint}whatsapp/templates",
    "per_page": 15,
    "to": 1,
    "total": 1
  }
}
```

## Create Templates

#### POST

```
{endpoint}whatsapp/templates
```

## Template Type

#### PARAMETERS

| name                                | optional | value                                                                                               |
| ----------------------------------- | -------- | --------------------------------------------------------------------------------------------------- |
| type                                | No       | `template`                                                                                          |
| name                                | No       | Template name without space ex: template_name                                                       |
| category                            | No       | `marketing`, `utility` or `authentication`                                                          |
| language                            | No       | prefer language ex: en, en_US                                                                       |
| is_conversation                     | No       | if `true`, approval not required from Meta                                                          |
| number                              | No       | business number Ex:(91861xxxxxxxx)                                                                  |
| payload.header.type                 | No       | `text`, `image`, `video` and `document`                                                             |
| payload.header.payload.text         | yes      | The header content, header contain only one variable incase type is `text`.                         |
| payload.header.params               | yes      | if type is `text`, support only one variable replacement.                                           |
| payload.header.payload.url          | No       | if header types `image`, `video` or `document`, link url                                            |
| payload.body                        | No       | Body content is mandatory                                                                           |
| payload.body.type                   | No       | `text`                                                                                              |
| payload.body.payload.text           | No       | The body content, body contains multiple variables (one variable is required if category `utility`) |
| payload.body.params                 | No       | if body content has variables provide the values for each variable                                  |
| payload.footer                      | Yes      | Footer is optional                                                                                  |
| payload.footer.type                 | Yes      | `text`                                                                                              |
| payload.footer.payload.text         | Yes      | The footer content is optional                                                                      |
| choices                             | Yes      | The choices buttons is optional                                                                     |
| choices.type                        | No       | `actions`                                                                                           |
| choices.actions                     | No       | expect the object at least one                                                                      |
| choices.actions.type                | No       | `phone_number`, `url`                                                                               |
| choices.actions.phone_number_text   | No       | max 20 characters                                                                                   |
| choices.actions.phone_number        | No       | country code prefix required Ex:(+91)                                                               |
| choices.actions.website_url_type    | No       | value is `Static`                                                                                   |
| choices.actions.website_button_text | No       | max 20 characters                                                                                   |
| choices.actions.website_url         | No       | should be url                                                                                       |

**_NOTE:_** Pass variables in `@{{}}` variables name should be different ex: `{{name}}`, `@{{email}}`

### With Button

### Example Request

#### Type Text

```
curl -X POST \
  '{endpoint}whatsapp/templates' \
  -H 'authorization: Bearer 5b02112fb7xxxxxxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "type": "template",
    "name": "template_name",
    "category": "marketing",
    "language": "en",
    "is_conversation": false,
    "number": "918736xxxxxx",
    "payload": {
        "header": {
            "type": "text",
            "payload": {
                "text": "Header text"
            },
            "params": []
        },
        "body": {
            "type": "text",
            "payload": {
                "text": "Any doubts please contact us"
            },
            "params": []
        },
        "footer": {
            "type": "text",
            "payload": {
                "text": "Thank you!"
            }
        },
        "choices": {
            "type": "actions",
            "actions": [
                {
                    "type": "phone_number",
                    "phone_number_text": "Any queries call",
                    "phone_number": "+918783xxxxxx"
                },
                {
                    "type": "url",
                    "website_url_type": "Static",
                    "website_button_text": "More info visit",
                    "website_url": "www.example.com"
                }
            ]
        }
    }
}'
```

#### Type Image

```
curl -X POST \
  '{endpoint}whatsapp/templates' \
  -H 'authorization: Bearer 5b02112fb7xxxxxxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "type": "template",
    "name": "template_name",
    "category": "marketing",
    "language": "en",
    "is_conversation": false,
    "number": "918736xxxxxx",
    "payload": {
        "header": {
            "type": "image",
            "payload": {
                "url": "https://www.pakainfo.com/wp-content/uploads/2021/09/image-url-for-testing.jpg"
            }
        },
        "body": {
            "type": "text",
            "payload": {
                "text": "Any doubts please contact us"
            },
            "params": []
        },
        "footer": {
            "type": "text",
            "payload": {
                "text": "Thank you!"
            }
        },
        "choices": {
            "type": "actions",
            "actions": [
                {
                    "type": "phone_number",
                    "phone_number_text": "Any queries call",
                    "phone_number": "+918783xxxxxx"
                },
                {
                    "type": "url",
                    "website_url_type": "Static",
                    "website_button_text": "More info visit",
                    "website_url": "www.example.com"
                }
            ]
        }
    }
}'

```

#### Type Video

```
curl -X POST \
  '{endpoint}whatsapp/templates' \
  -H 'authorization: Bearer 5b02112fb7xxxxxxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "type": "template",
    "name": "template_name",
    "category": "marketing",
    "language": "en",
    "is_conversation": false,
    "number": "918736xxxxxx",
    "payload": {
        "header": {
            "type": "video",
            "payload": {
                "url": "https://www.example/sample/video/sample.mp4"
            }
        },
        "body": {
            "type": "text",
            "payload": {
                "text": "Any doubts please contact us"
            },
            "params": []
        },
        "footer": {
            "type": "text",
            "payload": {
                "text": "Thank you!"
            }
        },
        "choices": {
            "type": "actions",
            "actions": [
                {
                    "type": "phone_number",
                    "phone_number_text": "Any queries call",
                    "phone_number": "+918783xxxxxx"
                },
                {
                    "type": "url",
                    "website_url_type": "Static",
                    "website_button_text": "More info visit",
                    "website_url": "www.example.com"
                }
            ]
        }
    }
}'
```

#### Type Document

```
curl -X POST \
  '{endpoint}whatsapp/templates' \
  -H 'authorization: Bearer 5b02112fb7xxxxxxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "type": "template",
    "name": "template_name",
    "category": "marketing",
    "language": "en",
    "is_conversation": false,
    "number": "918736xxxxxx",
    "payload": {
        "header": {
            "type": "document",
            "payload": {
                "url": "https://www.w3.org/WAI/ER/tests/xhtml/testfiles/resources/pdf/dummy.pdf"
            }
        },
        "body": {
            "type": "text",
            "payload": {
                "text": "Any doubts please contact us"
            },
            "params": []
        },
        "footer": {
            "type": "text",
            "payload": {
                "text": "Thank you!"
            }
        },
        "choices": {
            "type": "actions",
            "actions": [
                {
                    "type": "phone_number",
                    "phone_number_text": "Any queries call",
                    "phone_number": "+918736xxxxxx"
                },
                {
                    "type": "url",
                    "website_url_type": "Static",
                    "website_button_text": "More info visit",
                    "website_url": "www.example.com"
                }
            ]
        }
    }
}'
```

#### PARAMETERS

| name                       | optional | value                           |
| -------------------------- | -------- | ------------------------------- |
| choices                    | Yes      | The choices buttons is optional |
| choices.type               | No       | `reply`                         |
| choices.reply              | No       | object can not be empty         |
| choices.reply.type         | No       | `quick_reply`                   |
| choices.reply.quick_reply1 | No       | max 20 characters               |
| choices.reply.quick_reply2 | No       | max 20 characters               |
| choices.reply.quick_reply3 | Yes      | value is `Static`               |

### With Reply

### Example Request

#### Type Text

```
curl -X POST \
  '{endpoint}whatsapp/templates' \
  -H 'authorization: Bearer 5b02112fb7xxxxxxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "type": "template",
    "name": "template_name",
    "category": "marketing",
    "language": "en",
    "is_conversation": false,
    "number": "918736xxxxxx",
    "payload": {
        "header": {
            "type": "text",
            "payload": {
                "text": "Header text"
            },
            "params": []
        },
        "body": {
            "type": "text",
            "payload": {
                "text": "Any doubts please contact us"
            },
            "params": []
        },
        "footer": {
            "type": "text",
            "payload": {
                "text": "Thank you!"
            }
        },
        "choices": {
            "type": "reply",
            "reply": {
                "type": "quick_reply",
                "quick_reply1": "Yes",
                "quick_reply2": "No"
            }
        }
    }
}'
```

#### Type Image

```
curl -X POST \
  '{endpoint}whatsapp/templates' \
  -H 'authorization: Bearer 5b02112fb7xxxxxxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "type": "template",
    "name": "template_name_test",
    "category": "marketing",
    "language": "en",
    "is_conversation": false,
    "number": "918736xxxxxx",
    "payload": {
        "header": {
            "type": "image",
            "payload": {
                "url": "https://www.pakainfo.com/wp-content/uploads/2021/09/image-url-for-testing.jpg"
            }
        },
        "body": {
            "type": "text",
            "payload": {
                "text": "Any doubts please contact us"
            },
            "params": []
        },
        "footer": {
            "type": "text",
            "payload": {
                "text": "Thank you!"
            }
        },
        "choices": {
            "type": "reply",
            "reply": {
                "type": "quick_reply",
                "quick_reply1": "Yes",
                "quick_reply2": "No"
            }
        }
    }
}'

```

#### Type Video

```
curl -X POST \
  '{endpoint}whatsapp/templates' \
  -H 'authorization: Bearer 5b02112fb7xxxxxxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "type": "template",
    "name": "template_name",
    "category": "marketing",
    "language": "en",
    "is_conversation": false,
    "number": "918736xxxxxx",
    "payload": {
        "header": {
            "type": "video",
            "payload": {
                "url": "https://www.buildquickbots.com/media/sample/video/sample01.mp4"
            }
        },
        "body": {
            "type": "text",
            "payload": {
                "text": "Any doubts please contact us"
            },
            "params": []
        },
        "footer": {
            "type": "text",
            "payload": {
                "text": "Thank you!"
            }
        },
        "choices": {
            "type": "reply",
            "reply": {
                "type": "quick_reply",
                "quick_reply1": "Yes",
                "quick_reply2": "No"
            }
        }
    }
}'
```

#### Type Document

```
curl -X POST \
  '{endpoint}whatsapp/templates' \
  -H 'authorization: Bearer 5b02112fb7xxxxxxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "type": "template",
    "name": "template_name",
    "category": "marketing",
    "language": "en",
    "is_conversation": false,
    "number": "918736xxxxxx",
    "payload": {
        "header": {
            "type": "document",
            "payload": {
                "url": "https://www.orimi.com/pdf-test.pdf"
            }
        },
        "body": {
            "type": "text",
            "payload": {
                "text": "Any doubts please contact us"
            },
            "params": []
        },
        "footer": {
            "type": "text",
            "payload": {
                "text": "Thank you!"
            }
        },
        "choices": {
            "type": "reply",
            "reply": {
                "type": "quick_reply",
                "quick_reply1": "Yes",
                "quick_reply2": "No"
            }
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
        "id": "b6cda411-8fee-4918-beb2-fde30975383e",
        "name": "template_name",
        "category": "marketing",
        "language": "en",
        "status": "PENDING",
        "is_conversation": "false",
        "created_at": "2023-07-14T07:26:03.000000Z"
    }
}
```

### Authentication Category

#### PARAMETERS

| name                      | optional | value                                       |
| ------------------------- | -------- | ------------------------------------------- |
| category                  | No       | `authentication`                            |
| payload.body.type         | No       | `text`                                      |
| payload.body.payload.text | No       | Use defined content                         |
| payload.body.params       | No       | your verification code only one ex: 1287    |
| choices.type              | No       | value is `otp`                              |
| choices.type.otp.otp_type | No       | value is `copy_code` and `one_tap`          |
| choices.type.otp.otp_code | No       | value button text ex: copy your code        |
| choices.security          | No       | true, false                                 |
| choices.code_expire       | No       | min 1 and max 90 minutes (Code expiry time) |

## Type copy_code

### Example Request

```
curl -X POST \
  '{endpoint}whatsapp/templates' \
  -H 'authorization: Bearer 5b02112fb7xxxxxxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "type": "template",
    "name": "template_name",
    "category": "authentication",
    "language": "en",
    "is_conversation": false,
    "number": "918736xxxxxx",
    "payload": {
        "body": {
            "type": "text",
            "payload": {
                "text": "@{{code}} is your verification code."
            },
            "params": [
                "replacement_code"
            ]
        },
        "choices": {
            "type": "otp",
            "otp": {
                "otp_type": "copy_code",
                "text": "Copy your Code"
            },
            "code_expire": "5",
            "security": "true"
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
        "id": "b6cda411-8fee-4918-beb2-fde30975383e",
        "name": "template_name",
        "category": "authentication",
        "language": "en",
        "status": "PENDING",
        "is_conversation": "false",
        "created_at": "2023-07-14T07:26:03.000000Z"
    }
}
```

#### PARAMETERS

| name            | description                                | Type                  | Required |
| --------------- | ------------------------------------------ | --------------------- | -------- |
| type            | values are `text`, `JSON`, `media`         | `string`              | Yes      |
| name            | name should be a alphanumeric              | `string`              | Yes      |
| category        | `marketing`, `authentication` or `utility` | `string`              | Yes      |
| language        | Example : `en`, `en_US`                    | `string`              | Yes      |
| is_conversation | if `true` approval not required from Meta  | boolean               | Yes      |
| number          | business number Ex:(91861xxxxxxxx)         | `string` or `integer` | Yes      |

## Text Type

### Example Request

```
curl -X POST \
  '{endpoint}whatsapp/templates' \
  -H 'authorization: Bearer 5b02112fb7xxxxxxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "type": "text",
    "name": "new_text",
    "category": "marketing",
    "language": "en",
    "number": "91861xxxxxxxx",
    "is_conversation" : true,
    "payload": {
        "type": "text",
        "payload": {
            "text": "This is a simple text message"
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
        "id": "b6cda411-8fee-4918-beb2-fde30975383e",
        "name": "template_name",
        "category": "marketing",
        "language": "en",
        "status": "PENDING",
        "is_conversation": "false",
        "created_at": "2023-07-14T07:26:03.000000Z"
    }
}
```

## Json Type

In body content message should be json format.

### Example Request

```
curl -X POST \
  '{endpoint}whatsapp/templates' \
  -H 'authorization: Bearer 5b02112fb7xxxxxxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "type": "json",
    "name": "new_json",
    "category": "marketing",
    "language": "en",
    "number": "91861xxxxxxxx",
    "is_conversation" : false,
    "payload": {
        "type": "json",
        "payload" : {
            "text" : {"name" : "hlo"}
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
        "id": "b6cda411-8fee-4918-beb2-fde30975383e",
        "name": "template_name",
        "category": "marketing",
        "language": "en",
        "status": "PENDING",
        "is_conversation": "false",
        "created_at": "2023-07-14T07:26:03.000000Z"
    }
}
```

## Media Type

### Example Request

```
curl -X POST \
  '{endpoint}whatsapp/templates' \
  -H 'authorization: Bearer 5b02112fb7xxxxxxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "type": "media",
    "name": "new_media",
    "category": "marketing",
    "language": "en",
    "number": "91861xxxxxxxx",
    "is_conversation": true,
    "payload": {
        "type": "image",
        "payload": {
            "url": "https://www.buildquickbots.com/media/sample/jpg/sample01.jpg",
            "filename": "filename",
            "caption": "caption",
            "language": "en"
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
        "id": "b6cda411-8fee-4918-beb2-fde30975383e",
        "name": "template_name",
        "category": "marketing",
        "language": "en",
        "status": "PENDING",
        "is_conversation": "false",
        "created_at": "2023-07-14T07:26:03.000000Z"
    }
}
```

## Delete Templates

#### DELETE

```
{endpoint}whatsapp/templates/{id}
```

Replace the {id} with the actual id of the template that you would like to delete.

#### Example Request

```
curl -X DELETE \
  {endpoint}whatsapp/templates/7d77d0ef-63df-4ffb-83d6-xxxxxxxx \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 5b02112fb7xxxxxxxxx'
```

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Template Successfully Deleted",
  "data": []
}
```
