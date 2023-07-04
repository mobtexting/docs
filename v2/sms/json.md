# Send SMS Using JSON object
#include "_include/endpoint.md"

#### POST

```
{endpoint}sms/send/json
```

You can send sms using `POST` method content in body.

All params in send sms will support in JSON also.

`root` entry holds the default values for each node. You can overwite the `root` values inside `nodes` value except `webhook_id`, `service` and `time`.

#### BODY

```json
{
  "root": {
    "type": "A",
    "flash": 0,
    "sender": "TXTSMS",
    "message": "global message",
    "service": "MKT",
    "webhook_id": "1234a-3444-34444-XXxx",
    "time": "",
    "entity_id": "222343XXXXXX",
    "template_id": "2290003XXXXXX"
  },
  "nodes": [
    {
      "to": "919019xxxx2",
      "custom": "346576-446565-45657-XFTR",
      "sender": "txtmes",
      "message": "Message from & json api node 1"
    },
    {
      "to": "9188xxxxxxxxxx",
      "custom": "34"
    }
  ]
}
```

#### MANDATORY PARAMETERS

| Name    | Descriptions                                                                                                                                |
| ------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| to      | Phone number to send with country prefix. (multiple numbers can be separated by comma.)                                                     |
| message | The content of the SMS                                                                                                                      |
| sender  | The registered and approved Sender-id                                                                                                       |
| service | The short code of the service name. ex: (MKT) [full list](/docs/{version}/#content-products) [full list](/docs/{version}/#content-products) |

#### OPTIONAL PARAMETERS

| Name        | Descriptions                                                                                                                                                            |
| ----------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| name        | Name of the campaign (`group_id` will be returned in response)                                                                                                          |
| webhook_id  | The `id` of the webhook created in Webhook Section for which the SMS response to be sent after delivery report from operator. [read more](/docs/{version}/sms-push-dlr) |
| time        | Schedule time (in format i.e,yyyy-mm-dd hh:mm:ss) at which the SMS has to be sent.                                                                                      |
| type        | The SMS to be sent is Unicode, Normal or Auto detect. (value "U", "N" or "A")                                                                                           |
| flash       | This parameter can be used to send flash sms via API ( Values 1 or 0.)                                                                                                  |
| custom      | Any customised parameters can be passed using this parameter                                                                                                            |
| port        | Port number to which SMS has to be sent                                                                                                                                 |
| entity_id   | Principal Entityid registered in DLT portal (applicable for indian routes only)                                                                                         |
| template_id | TemplateId registered in DLT portal (applicable for indian routes only)                                                                                                 |
| max_units | The maximum number of units to be sent in the message ex:(value 2 or 3) |

#### Example Request

```curl
curl --request POST \
  --url {endpoint}sms/send/json \
  -H 'Authorization: Bearer 209eccd40ee3a2e14af7fe45b21xxx'
  -H 'Content-Type: application/json' \
  --data '{
    "root": {
        "type": "A",
        "flash": 0,
        "sender": "TXTSMS",
        "message": "global message",
        "service": "MKT",
        "webhook_id": "1234-aabn13-23xxxxx",
        "time": "",
        "entity_id": "222343XXXXXX",
        "template_id": "2290003XXXXXX"
    },
    "nodes": [
        {
            "to": "919019xxxx2",
            "custom": "346576-446565-45657-XFTR",
            "sender": "txtmes",
            "message": "Message from & json api node 1"
        },
        {
            "to": "9188xxxxxxxxxx",
            "custom": "34"
        }
    ]
}'
```

#### Example Response

```json
{
  "status": 200,
  "message": "2 numbers accepted for delivery.",
  "data": [
    {
      "id": "b34e35ad-fe34-4a8b-977c-b21cd76cd7d6:1",
      "mobile": "919019xxxx2",
      "status": "AWAITING-DLR",
      "units": 1,
      "length": 7,
      "charges": 1,
      "customid": "346576-446565-45657-XFTR",
      "iso_code": null,
      "submitted_at": "2018-07-09 16:27:35"
    },
    {
      "id": "b34e35ad-fe34-4a8b-977c-b21cd76cd7d6:1",
      "mobile": "9188xxxxxxxxxx",
      "status": "AWAITING-DLR",
      "units": 1,
      "length": 7,
      "charges": 1,
      "customid": "34",
      "iso_code": null,
      "submitted_at": "2018-07-09 16:27:35"
    }
  ]
}
```

## Get GroupID In Response

You can get group_id of the SMS campaing when you sent `name` paramter in api as mentioned in below example.

#### Example Request

```curl
curl --request POST \
  --url {endpoint}sms/send/json \
  -H 'Authorization: Bearer 209eccd40ee3a2e14af7fe45b21xxx'
  -H 'Content-Type: application/json' \
  --data '{
    "root": {
        "name": "Name of the Campaing",
        "type": "A",
        "flash": 0,
        "sender": "TXTSMS",
        "message": "global message",
        "service": "MKT",
        "dlr_url": "http://www.domainname.com/dlr?status={status}",
        "time": "",
        "entity_id": "222343XXXXXX",
        "template_id": "2290003XXXXXX"
    },
    "nodes": [
        {
            "to": "919019xxxx2",
            "custom": "346576-446565-45657-XFTR",
            "sender": "txtmes",
            "message": "Message from & json api node 1"
        },
        {
            "to": "9188xxxxxxxxxx",
            "custom": "34"
        }
    ]
}'
```

#### Example Response With group_id

```json
{
  "status": 200,
  "message": "2 numbers accepted for delivery.",
  "group_id": "b34e35ad-fe34-4a8b-977c-b21cd76cd7d6",
  "data": [
    {
      "id": "b34e35ad-fe34-4a8b-977c-b21cd76cd7d6:1",
      "mobile": "919019xxxx2",
      "status": "AWAITING-DLR",
      "units": 1,
      "length": 7,
      "charges": 1,
      "customid": "346576-446565-45657-XFTR",
      "iso_code": null,
      "submitted_at": "2018-07-09 16:27:35"
    },
    {
      "id": "b34e35ad-fe34-4a8b-977c-b21cd76cd7d6:2",
      "mobile": "9188xxxxxxxxxx",
      "status": "AWAITING-DLR",
      "units": 1,
      "length": 7,
      "charges": 1,
      "customid": "34",
      "iso_code": null,
      "submitted_at": "2018-07-09 16:27:35"
    }
  ]
}
```
