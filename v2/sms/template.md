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

`Dear Demo, Thanks for regisitering with us. Your details as follows demoxxxx@gmail.com, 9189XXXXXXXX.`

## Send Message

#include "_include/endpoint.md"

#### POST

```
{endpoint}sms/send/template
```

You can send template message using `POST` method content in body.

#### BODY

```json
{
  "alias": "template-name",
  "recipient": {
    "to": ["9189195xxxxx", "9189196xxxxx"]
  },
  "data": {
    "name": "MKT",
    "email": "demoxxxx@gmail.com",
    "phone": "89XXXXXXXX"
  },
  "meta": {
    "webhook_id": "0798d163-7ca2-4mb6-8c16-c62866xxxxxxx",
    "tags": ["tag1", "tag2"]
  }
}
```

#### MANDATORY PARAMETERS

| Name      | Descriptions                                                                        |
| --------- | ----------------------------------------------------------------------------------- |
| alias     | alias of the registered template. (Required if `id` not present)                    |
| id        | id of the registered template. (Required if `alias` not present)                    |
| recipient | This block contains contacts informations                                           |
| group_id  | Segment id which contain list of phone numbers (Required if `to` param not present) |
| to        | Receiver mobile numbers (Required if `group_id` param not present)                  |
| data      | Variable values for replacing in template content                                   |

#### OPTIONAL PARAMETERS

| Name | Descriptions |
| ---- | ------------ |

|
meta | This block contains all the optional parameters |
| webhook_id | The `id` of the webhook created in Webhook Section for which the SMS response to be sent after delivery report from operator. [read more](/docs/{version}/sms/webhook) | |
| foreign_id | Custom id for reference from customer.|

#### Example Request

#code "{version}/_code/sms/send_template.json"

#### Example Response

```json
{
  "status": "OK",
  "message": "Message(s) Queued successfully",
  "data": [
    {
      "id": "71968588-9f20-456c-bdfa-1acc7b4xxxxx:1",
      "channel": "sms",
      "from": "sender_name",
      "to": "9189196xxxxx",
      "credits": "1",
      "created_at": "2020-09-24 15:42:56",
      "status": "AWAITING-DLR",
      "foreign_id": ""
    },
    {
      "id": "71968588-9f20-456c-bdfa-1acc7b4xxxxx:2",
      "channel": "sms",
      "from": "sender_name",
      "to": "9189196xxxxx",
      "credits": "1",
      "created_at": "2020-09-24 15:42:56",
      "status": "AWAITING-DLR",
      "foreign_id": ""
    }
  ]
}
```
