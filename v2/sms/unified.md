# Send Message Using SMS Channel

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

`Note` : The `recipient` block inside channel is related to particular communication channel and it is optional. The outside `recipient` channel contain common recipients for every channel.

#### HTTP Methods

It will support only `POST` requests.

#### API Endpoint

```
{domain}/api/{version}/
```

## Sending Text Message

```
{endpoint}sms/message/send
```

#### Example Request With Text Message

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
        "type": "text",
		"payload": {
			"text": "This is a simple text message from sms channel"
		}
	}
}'
```

#### PARAMETERS

| Name    | Description                                 | Limits              | Required |
| ------- | ------------------------------------------- | ------------------- | -------- |
| payload | Messaage Payload section                    | N/A                 | Yes      |
| to      | Destination mobile number with country code | NA                  | Yes      |
| text    | Message Content you want to send            | Max 4096 Characters | Yes      |

## Sending Template Message

#### API Endpoint

```
{domain}/api/{version}/
```

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
            "namespace: "",
			"language": "en",
			"header_params": ["Replacement Text"],
			"body_params": ["223344", "10"]
		}
	}
}'
```

#### PARAMETERS

| Name          | Description                                                                                                                                    | Limits                                                                     | Required |
| ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------- |
| name          | Template Name                                                                                                                                  | N/A                                                                        | yes      |
| namespace     | Namespace of the template                                                                                                                      | N/A                                                                        | yes      |
| language      | Language to send the template in. Default `en`                                                                                                 | N/A                                                                        | No       |
| header_params | Can only used when there is a header of type text in the template. Up to 60 characters for all parameters and predefined template header text. | Up to 60 characters for all parameters and predefined template header text | No       |
| body_params   | Up to 1024 characters for all parameters and predefined template text.                                                                         | Up to 1024 characters for all parameters and predefined template text      | No       |
