# Template API

Now you can send message using template alias name or template id of the predefined template created in your account.

Example template as follows:

Dear @{{name}}, Thanks for registering with us. Your details as follows @{{email}}, @{{phone}}.

While sending message we need to pass the data in the data payload then content will be replaced automatically in the template as below.

Ex: 
```
"data": {
          "name": "Demo",
          "email": "demoxxxx@gmail.com",
          "phone":"89XXXXXXXX",
        }
```
Output Message: 

```Dear Demo, Thanks for regisitering with us. Your details as follows demoxxxx@gmail.com, 9189XXXXXXXX.```

## Send Message
#include "_include/endpoint.md"

#### POST

```
{endpoint}viber/send/template
```

You can send template message using `POST` method content in body.

#### BODY

```json
{
    "alias": "template-name",
    "recipient": {
        "group_id": "{segment_id}",
        "to": ["91XXXXXX", "91XXXXXX"]
    },
    "data": {
        "name": "name",
        "email": "1234XXXXXXX",
        "message":"89XXXXXXXXXXX"
    },
    "meta": {
        "from": "700969ca-0cb2-11ec-a2cxxxx",
        "webhook_id": "0798d163-7ca2-4mb6-8c16-c62866xxxxxxx",
        "tags": ["tag1", "tag2"]
    }
}
```

#### MANDATORY PARAMETERS

| Name        | Descriptions                                                                                           |
| ----------- | ------------------------------------------------------------------------------------------------------ |
| alias       | alias of the registered template. (Required if `id` not present)                                         |
| id          | id of the registered template. (Required if `alias` not present)                                         |
| recipient   |	This block contains contacts informations                                                                |
| group_id    |	Segment id which contain list of phone numbers (Required if `to` param not present)                      |
| to	        | Receiver mobile numbers (Required if `group_id` param not present)                                             |
| data        | Variable values for replacing in template content                                                       |
| meta        | This block contains commercial account/sender information                                                         |
| from        | Commercial account/sender ID                                                       |

#### OPTIONAL PARAMETERS

| Name       | Descriptions                                                                                                                                                            |
| ---------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- 
| webhook_id | The `id` of the webhook created in Webhook Section for which the response to be sent after delivery report from operator. [read more](/docs/{version}/viber/webhooks) |                                                                                         |
| foreign_id     | Custom id for reference from customer.|

#### Example Request

```
  curl -X POST \
    '{endpoint}viber/send/template' \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 38e896f55670311982434e929559bxxxx' \
    -H 'content-type: application/json' \
    -d '{
      "alias": "template-name",
      "recipient": {
        "to": ["9189195xxxx","9189196xxxx"]
      },
      "data" : {
        "name" : "Demo",
        "email" : "Demo@gmail.com",
        "phone" : "8123xxxxxxx"
      },
      "meta": {
        "from": "700969ca-0cb2-11ec-a2cxxxx",
        "tags": ["tag1", "tag2"]
      }
    }'
```

#### Example Response

```json
{
    "status": "OK",
    "message": "Messages queued successfully",
    "data": [
        {
            "id": "883137c2-7b9c-4e72-8454-1059f06xxxxx",
            "channel": "viber",
            "from": "700969ca-0cb2-11ec-a2cxxxx",
            "recipient": "9189195xxxx",
            "credits": 0,
            "created_at": "2023-01-26T07:24:25.532476Z",
            "foreign_id": null,
            "status": "notallowed"
        },
        {
            "id": "5ec99a11-ca18-44ad-a0fa-3250e36b8a20",
            "channel": "viber",
            "from": "700969ca-0cb2-11ec-a2cxxxx",
            "recipient": "9189196xxxx",
            "credits": "0.2500",
            "created_at": "2023-08-22T11:38:21.089049Z",
            "foreign_id": null,
            "status": "queued"
        }
    ]
}
```
