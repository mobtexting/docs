# Ip (mip) Messaging Service

## Channel Info

```
{
	"channels": [{
		"name": "mip",
		"from": "919019120xxx",
		"recipient": {
			"group_id": "{segment_id}",
			"to": ["9189195xxxx", "91886713xxxx"]
		}
	}]
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
      "channel": "mip",
      "from": "919019120xxx",
      "to": "9190199xxxxx",
      "credits": 1,
      "created_at": "2021-06-18T14:48:06.886358Z",
      "status": "queued",
      "foreign_id": "your-message-id"
    }
  ]
}
```

#### PARAMETERS

| Name      | Description                                                 | type                | Required                       |
| --------- | ----------------------------------------------------------- | ------------------- | ------------------------------ | -------- | --- |
| channels  | This block contains information realted messaging channel   | N/A                 | Yes                            |
| name      | Name of Messaging Channel. `whatsapp                        | rcs                 | ip_message`                    | `string` | Yes |
| from      | Sender or From Number                                       | `number`            | Yes                            |
| recipient | This block contains contacts information related to channel | N/A                 | Yes                            |
| group_id  | Segment id which contain list of phone numbers              | `string` or `array` | Yes if `to` param not present  |
| to        | Receiver mobile numbers : `text`                            | `array`             | Yes, if `group_id` not present |

`Note` : The `recipient` block inside channel is related to particular communication channel and it is optional. The outside `recipient` channel contain common recipients for every channel.

#### HTTP Methods

It will support only `POST` requests.
#include "_include/endpoint.md"

## Sending Text Message

```
{endpoint}mip/message/send
```

#### Example Request With Text Messgae

```
curl -X POST \
  '{endpoint}mip/message/send' \
  -H 'authorization: Bearer d9e1cac3812186b353c5022xxxxx' \
  -H 'content-type: application/json' \
  -d '{
	"channels": [{
		"name": "mip",
		"from": "919019120xxx"
	}],
	"recipient": {
		"to": "91XXXXXX"
	},
	"message": {
        "type": "text",
		"payload": {
			"text": "This is a simple text message from mip channel"
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
#include "_include/endpoint.md"

```
{endpoint}mip/message/send
```

#### Example Request With Template

```
curl -X POST \
  '{endpoint}mip/message/send' \
  -H 'authorization: Bearer d9e1cac3812186b353c5022xxxxx' \
  -H 'content-type: application/json' \
  -d '{
	"channels": [{
		"name": "mip",
		"from": "919019120xxx"
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
			"body_params": ["223344", "10"],
            "components": {

            }
		}
	}
}'
```

#### PARAMETERS

| Name          | Description                                                                                                                                                                                         | Limits                                                                     | Required |
| ------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------- |
| name          | Template Name                                                                                                                                                                                       | N/A                                                                        | yes      |
| namespace     | Namespace of the template                                                                                                                                                                           | N/A                                                                        | yes      |
| language      | Language to send the template in. Default `en`                                                                                                                                                      | N/A                                                                        | No       |
| header_params | Can only used when there is a header of type text in the template. Up to 60 characters for all parameters and predefined template header text.                                                      | Up to 60 characters for all parameters and predefined template header text | No       |
| body_params   | Up to 1024 characters for all parameters and predefined template text.                                                                                                                              | Up to 1024 characters for all parameters and predefined template text      | No       |
| ttl           | Time to live of the template message. If the receiver has not opened the template message before the time to live expires, the message will be deleted. Default 30 Days. Need to specify in Seconds | Can be more than 1 day i.e 86400 sec                                       | No       |

## Send Interactive Message
#include "_include/endpoint.md"

We can send Video clips as attachment using below API. The maximum audio file size is limited to 64 MB.

```
{endpoint}mip/message/send
```

#### Example Request With Interactive Choice Messgae

```
curl -X POST \
  '{endpoint}mip/message/send' \
  -H 'authorization: Bearer d9e1cac3812186b353c5022xxxxx' \
  -H 'content-type: application/json' \
  -d '{
	"channels": [{
		"name": "mip",
		"from": "919019120xxx"
	}],
	"recipient": {
		"to": "91XXXXXX"
	},
	"message": {
		"type": "interactive",
		"payload": {
            "category" : "",
			"header": {
				"type": "text",
				"payload": {
					"text": "header text"
				}
			},
			"body": {
				"type": "text",
				"payload": {
					"text": "header text"
				}
			},
			"footer": {
				"type": "text",
				"payload": {
					"text": "header text"
				}
			},
			"choices": [{
					"type": "url",
					"payload": {
						"url": "https://example.com",
						"title": "Click Here",
						"id": "unique-id"
					}
				},
				{
					"type": "text",
					"payload": {
						"title": "Click Here",
						"id": "unique-id"
					}
				},
				{
					"type": "reply",
					"payload": {
						"title": "Click Here",
						"id": "unique-id"
					}
				},
				{
					"type": "call",
					"payload": {
						"title": "Click Here",
						"phone_number": "+91901995xxxx",
						"id": "unique-id"
					}
				},
				{
					"type": "copy",
					"payload": {
						"title": "Click Here to copy",
						"content": "+91901995xxxx",
						"id": "unique-id"
					}
				},
				{
					"type": "calendar",
					"payload": {
						"title": "Add to Calendar",
						"event": {
                            "date": "2020-01-31",
                            "time": "23:30",
                            "title": "Title of the event",
                            "description": "Description of the event"
                        },
						"id": "unique-id"
					}
				},
				{
					"type": "section",
					"payload": {
						"title": "Click Here",
						"rows": [{
							"id": "unique-row-identifier-here",
							"title": "row-title-content-here",
							"description": "row-description-content-here"
						}]
					}
				}
			]
		}
	}
}'
```

#### PARAMETERS

| Name    | Description                                                | Limits | Required |
| ------- | ---------------------------------------------------------- | ------ | -------- |
| choices | this block contains actions for suggestions of the message | N/A    | Yes      |

## Send Card Message
#include "_include/endpoint.md"

We can send Carousel using below API. The maximum audio file size is limited to 64 MB.

```
{endpoint}mip/message/send
```

#### Example Request With Card Messgae

```
curl -X POST \
  '{endpoint}mip/message/send' \
  -H 'authorization: Bearer d9e1cac3812186b353c5022xxxxx' \
  -H 'content-type: application/json' \
  -d '{
	"channels": [{
		"name": "mip",
		"from": "919019120xxx"
	}],
	"recipient": {
		"to": "91XXXXXX"
	},
	"message": {
        "type": "card",
		"payload": {
			"title": "This is the card title",
			"description": "This is the card description",
			"body": {
                "type": "image",
                "payload": {
                    "url": "https://domin-name.com/your_image_path.png",
                    "caption": "some caption for image",
                    "filename": ""
                }
			},
            "choices": [
                {
					"type": "url",
					"payload": {
						"url": "https://example.com",
						"title": "Click Here",
						"id": "unique-id"
					}
				},
				{
					"type": "text",
					"payload": {
						"title": "Click Here",
						"id": "unique-id"
					}
				},
				{
					"type": "reply",
					"payload": {
						"title": "Click Here",
						"id": "unique-id"
					}
				},
				{
					"type": "call",
					"payload": {
						"title": "Click Here",
						"phone_number": "+91901995xxxx",
						"id": "unique-id"
					}
				},
				{
					"type": "copy",
					"payload": {
						"title": "Click Here to copy",
						"content": "+91901995xxxx",
						"id": "unique-id"
					}
				},
				{
					"type": "calendar",
					"payload": {
						"title": "Add to Calendar",
						"event": {
                            "date": "2020-01-31",
                            "time": "23:30",
                            "title": "Title of the event",
                            "description": "Description of the event"
                        },
						"id": "unique-id"
					}
				},
				{
					"type": "section",
					"payload": {
						"title": "Click Here",
						"rows": [{
							"id": "unique-row-identifier-here",
							"title": "row-title-content-here",
							"description": "row-description-content-here"
						}]
					}
				}
			]
		}
	}
}'
```

#### PARAMETERS

| Name | Description | Limits | Required |
| ---- | ----------- | ------ | -------- |
