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

#code "{version}/_code/whatsapp/templates/list.json"

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
| payload.header.payload.text         | yes      | The header content, header contain only one variable incase type is `text`. (It accepts only `60 chars`.)                        |
| payload.header.params               | yes      | if type is `text`, support only one variable replacement.                                           |
| payload.header.payload.url          | No       | if header types `image`, `video` or `document`, link url                                            |
| payload.body                        | No       | Body content is mandatory                                                                           |
| payload.body.type                   | No       | `text`                                                                                              |
| payload.body.payload.text           | No       | The body content, body contains multiple variables (one variable is required if category `utility`) (It accepts only `1024 chars`.) |
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

**_NOTE:_** Pass variables in `@{{}}` variables name should be different ex: `{{name}}`, `@{{email}}` and should be `alphabetic` or `alphanumeric`

### With Button

### Example Request

#### Type Text

#code "{version}/_code/whatsapp/templates/button/text_type.json"

#### Type Image

#code "{version}/_code/whatsapp/templates/button/image_type.json"

#### Type Video

#code "{version}/_code/whatsapp/templates/button/video_type.json"

#### Type Document

#code "{version}/_code/whatsapp/templates/button/document_type.json"

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

#code "{version}/_code/whatsapp/templates/reply/text_type.json"

#### Type Image

#code "{version}/_code/whatsapp/templates/reply/image_type.json"

#### Type Video

#code "{version}/_code/whatsapp/templates/reply/video_type.json"

#### Type Document

#code "{version}/_code/whatsapp/templates/reply/document_type.json"

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
| choices.type.otp.text     | No       | value button text ex: copy your code        |
| choices.security          | No       | true, false                                 |
| choices.code_expire       | No       | min 1 and max 90 minutes (Code expiry time) |

## Type copy_code

### Example Request

#code "{version}/_code/whatsapp/templates/copy_code.json"

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

#code "{version}/_code/whatsapp/templates/create_text.json"

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

#code "{version}/_code/whatsapp/templates/create_json.json"

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
            "url": "https://www.buildquickbots.com/whatsapp/media/sample/jpg/sample01.jpg",
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

#code "{version}/_code/whatsapp/templates/delete.json"

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Template Successfully Deleted",
  "data": []
}
```
