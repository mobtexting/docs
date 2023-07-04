# Send Notification Using SMS Channel

#### HTTP Methods

`POST` - When you send a POST request with the end user's phone number to the messaging subresource, We sends the SMS message you specify.

> Country code is mandatory to be included in the `to` paramenter.

## Channel Info

```
{
	"channels": [{
		"name": "sms",
		"from": "SENDER",
		"meta": {
			"service": "MKT",
			"template_id": "1234XXXXXXX",
			"entity_id":"89XXXXXXXXXXX",
			"foreign_id":"your-custom-id",
			"type":"U"
		}
	}],
	"recipient": {
		"group_id": "{segment_id}",
		"to": ["91XXXXXX", "91XXXXXX"]
	}
}
```

#### Example Response

```json
{
  "status": "OK",
  "message": "Message Queued successfully",
  "data": [
    {
      "id": "a418d672-9781-4d97-b517-a56f7d95ad8a",
      "channel": "sms",
      "from": "SENDER",
      "to": "9190199xxxxx",
      "credits": 1,
      "created_at": "2021-06-18 14:48:06",
      "status": "AWAITING-DLR",
      "foreign_id": "your-message-id"
    }
  ]
}
```

#### PARAMETERS

| Name        | Description                                                                   | type                | Required                               |
| ----------- | ----------------------------------------------------------------------------- | ------------------- | -------------------------------------- |
| channels    | This block contains information realted messaging channel                     | `array`             | Yes                                    |
| name        | Name of Messaging Channel. Ex: `sms`                                          | `string`            | Yes                                    |
| from        | Sender or From Number                                                         | `number`            | Yes                                    |
| meta        | This block contains additional information related to messaging channel       | `map`               | Yes                                    |
| service     | Sms Service Name. Default takes the first enabled sms service.                | `string`            | Yes                                    |
| foreign_id  | Custom id for reference from customer.                                        | `string`            | No                                     |
| type        | The SMS to be sent is Unicode, Normal or Auto detect. (value “U”, “N” or “A”) | `string`            | No                                     |
| recipient   | This block contains contacts information related to channel                   | `list`              | Yes                                    |
| group_id    | Segment id which contain list of phone numbers                                | `string` or `array` | Yes if `to` param not present          |
| to          | Receiver mobile numbers : `text`                                              | `array`             | Yes, if `group_id` not present         |
| template_id | DLT registered template id.                                                   | `int`               | No (applicable for indian routes only) |
| entity_id   | DLT registered entity id.                                                     | `int`               | No (applicable for indian routes only) |
| max_units   | The maximum number of units to be sent in the message ex:(value 2 or 3)       | `int`               | No                                     |

`Note` : The `recipient` block inside channel is related to particular communication channel and it is optional. The outside `recipient` channel contain common recipients for every channel.

#### HTTP Methods

It will support only `POST` requests.
#include "_include/endpoint.md"

## Sending Text Message

```
{endpoint}sms/message/send
```

#### Example Request With Text Message

#include "{version}/_samples/sms/send.md"

#### PARAMETERS

| Name    | Description                                 | Limits              | Required |
| ------- | ------------------------------------------- | ------------------- | -------- |
| payload | Messaage Payload section                    | N/A                 | Yes      |
| to      | Destination mobile number with country code | NA                  | Yes      |
| text    | Message Content you want to send            | Max 4096 Characters | Yes      |

## Sending Template Message
#include "_include/endpoint.md"

```
{endpoint}sms/message/send
```

#### Example Request With Template

```
curl -X POST \
  '{endpoint}sms/message/send' \
  -H 'authorization: Bearer d9e1cac3812186b353c5022xxxxx' \
  -H 'content-type: application/json' \
  -d '{
	"channels": [{
		"name": "sms",
		"from": "SENDER"
	}],
	"recipient": {
		"to": "91XXXXXX"
	},
	"message": {
        "type": "template",
		"payload": {
			"name": "otp",
			"body_params": ["223344", "10"]
		}
	}
}'
```

#### PARAMETERS

| Name        | Description                                                                                            | Required                             |
| ----------- | ------------------------------------------------------------------------------------------------------ | ------------------------------------ |
| name        | Template Name                                                                                          | yes                                  |
| body_params | Varible values for replacing in template content (need to send as array) Ex:[“name”,“891919XXX”,“new”] | yes if variables present in template |
