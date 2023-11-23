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
{endpoint}rcs/send/template
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
        "name": "MKT",
        "email": "1234XXXXXXX",
        "message":"89XXXXXXXXXXX"
    },
    "meta": {
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

#### OPTIONAL PARAMETERS

| Name       | Descriptions                                                                                                                                                            |
| ---------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- 
|
meta      | This block contains all the optional parameters                                                                                                                                             |
| webhook_id | The `id` of the webhook created in Webhook Section for which the response to be sent after delivery report from operator. [read more](/docs/{version}/rcs/webhooks) |                                                                                         |
| foreign_id     | Custom id for reference from customer.|

#### Example Request

#code "{version}/_code/rcs/send_template.json"

#### Example Response

```json
{
    "status": "OK",
    "message": "Messages queued successfully",
    "data": [
        {
            "id": "bd14332d-4315-42d3-a27e-b21fd40xxxxx",
            "channel": "rcs",
            "from": "ce7c551a-c65a-4a07-a33a-cbe6afxxxxxx",
            "recipient": "9189195xxxxx",
            "credits": 0,
            "created_at": "2023-01-24T09:46:09.939286Z",
            "foreign_id": null,
            "status": "notallowed"
        },
        {
            "id": "723d3daf-0f4d-4b26-97c5-3de009xxxxxx",
            "channel": "rcs",
            "from": "ce7c559a-c65a-4a07-a33a-cbe6afxxxxxx",
            "recipient": "9189196xxxxx",
            "credits": 0,
            "created_at": "2023-01-24T09:46:09.955824Z",
            "foreign_id": null,
            "status": "notallowed"
        }
    ]
}
```
