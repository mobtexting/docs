# Unified API

## Channel Info

```
{
	"channels": [{
		"name": "whatsapp",
		"from": "919019120xxx",
        "meta" : {
            "foreign_id":"your-custom-id"
        },
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
      "channel": "whatsapp",
      "from": "919019120xxx",
      "to": "9190199xxxxx",
      "credits": 1,
      "created_at": "2021-06-18T14:48:06.886358Z",
      "status": "queued"
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
{endpoint}whatsapp/message/send
```

#### Example Request With Text Messgae

```
curl -X POST \
  '{endpoint}whatsapp/message/send' \
  -H 'authorization: Bearer d9e1cac3812186b353c5022xxxxx' \
  -H 'content-type: application/json' \
  -d '{
	"channels": [{
		"name": "whatsapp",
		"from": "919019120xxx"
	}],
	"recipient": {
		"to": "91XXXXXX"
	},
	"message": {
        "type": "text",
		"payload": {
			"text": "This is a simple text message from whatsapp channel"
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

#### Example Response

```json
{
  "status": "OK",
  "message": "Message Queued successfully",
  "data": [
    {
      "id": "a418d672-9781-4d97-b517-a56f7d95ad8a",
      "channel": "whatsapp",
      "from": "919019120xxx",
      "to": "9190199xxxxx",
      "credits": 1,
      "created_at": "2021-06-18T14:48:06.886358Z",
      "status": "SENT"
    }
  ]
}
```

## Sending Template Message

#include "_include/endpoint.md"

Template message is the way of sending dynamic content using variables.

```
Example of the template looks as follows :

Otp For verifying your account is @{{1}} code: @{{2}}. Valid for @{{3}} minutes.

```

Here @{{1}}, @{{2}}, @{{3}} are replacement variables which is different for each message. Same needs to be for `params` or `body_params` parameters.

```
{endpoint}whatsapp/message/send
```

#### Example Request With Template

```
curl -X POST \
  '{endpoint}whatsapp/message/send' \
  -H 'authorization: Bearer d9e1cac3812186b353c5022xxxxx' \
  -H 'content-type: application/json' \
  -d '{
	"channels": [{
		"name": "whatsapp",
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

## Send Image Message

#include "_include/endpoint.md"

We can send Images as attachment using below API. The maximum image size is limited to 64 MB.

```
{endpoint}whatsapp/message/send
```

#### Example Request With Image Messgae

```
curl -X POST \
  '{endpoint}whatsapp/message/send' \
  -H 'authorization: Bearer d9e1cac3812186b353c5022xxxxx' \
  -H 'content-type: application/json' \
  -d '{
	"channels": [{
		"name": "whatsapp",
		"from": "919019120xxx"
	}],
	"recipient": {
		"to": "91XXXXXX"
	},
	"message": {
		"type": "image",
		"payload": {
			"url": "https://domin-name.com/your_image_path.png",
			"caption": "some caption for image",
            "filename": ""
		}
	}
}'
```

#### PARAMETERS

| Name     | Description                                           | Limits | Required |
| -------- | ----------------------------------------------------- | ------ | -------- |
| url      | Public url of the image file. Either HTTP/HTTPS link. | 64 MB  | Yes      |
| caption  | some text for image caption                           | N/A    | No       |
| filename | Media file name                                       | N/A    | No       |

## Send Document Message

#include "_include/endpoint.md"

We can send Document which is having valid MIME-type as attachment using below API. The maximum document size is limited to 64 MB. So anything not image, audio or video will be transmitted as document message.

```
{endpoint}whatsapp/message/send
```

#### Example Request With Document Messgae

```
curl -X POST \
  '{endpoint}whatsapp/message/send' \
  -H 'authorization: Bearer d9e1cac3812186b353c5022xxxxx' \
  -H 'content-type: application/json' \
  -d '{
	"channels": [{
		"name": "whatsapp",
		"from": "919019120xxx"
	}],
	"recipient": {
		"to": "91XXXXXX"
	},
	"message": {
		"type": "document",
		"payload": {
			"url": "https://domin-name.com/docs/uploads/voice.pdf",
			"caption": "some caption for document",
			"filename": ""
		}
	}
}'
```

#### PARAMETERS

| Name     | Description                                                 | Limits             | Required |
| -------- | ----------------------------------------------------------- | ------------------ | -------- |
| url      | Public url of the document file. Either HTTP or HTTPS link. | Max File size 64MB | Yes      |
| caption  | some text for document caption                              | N/A                | No       |
| filename | Media file name                                             | N/A                | No       |

## Send Audio Message

#include "_include/endpoint.md"

We can send Audio clips as attachment using below API. The maximum audio file size is limited to max 64 MB.

```
{endpoint}whatsapp/message/send
```

#### Example Request With Audio Messgae

```
curl -X POST \
  '{endpoint}whatsapp/message/send' \
  -H 'authorization: Bearer d9e1cac3812186b353c5022xxxxx' \
  -H 'content-type: application/json' \
  -d '{
	"channels": [{
		"name": "whatsapp",
		"from": "919019120xxx"
	}],
	"recipient": {
		"to": "91XXXXXX"
	},
	"message": {
		"type": "audio",
		"payload": {
			"url": "https://domin-name.com/docs/uploads/voice.pdf",
			"caption": "some caption for document",
			"filename": ""
		}
	}
}'
```

#### PARAMETERS

| Name     | Description                                              | Limits    | Required |
| -------- | -------------------------------------------------------- | --------- | -------- |
| url      | Public url of the audio file. Either HTTP or HTTPS link. | Upto 64MB | Yes      |
| caption  | some text for audio caption                              | N/A       | No       |
| filename | Media file name                                          | N/A       | No       |

## Send Video Message

#include "_include/endpoint.md"

We can send Video clips as attachment using below API. The maximum audio file size is limited to 64 MB.

```
{endpoint}whatsapp/message/send
```

#### Example Request With Video Messgae

```
curl -X POST \
  '{endpoint}whatsapp/message/send' \
  -H 'authorization: Bearer d9e1cac3812186b353c5022xxxxx' \
  -H 'content-type: application/json' \
  -d '{
	"channels": [{
		"name": "whatsapp",
		"from": "919019120xxx"
	}],
	"recipient": {
		"to": "91XXXXXX"
	},
	"message": {
		"type": "video",
		"payload": {
			"url": "https://domin-name.com/docs/uploads/voice.mp4",
			"caption": "some caption for video",
			"filename": "myvideo",
            "cover": "https://domin-name.com/docs/uploads/cover.png"
		}
	}
}'
```

#### PARAMETERS

| Name     | Description                                              | Limits    | Required |
| -------- | -------------------------------------------------------- | --------- | -------- |
| url      | Public url of the audio file. Either HTTP or HTTPS link. | Upto 64MB | Yes      |
| caption  | some text for audio caption                              | N/A       | No       |
| filename | Media file name                                          | N/A       | No       |

## Send Notification With Interactive Suggestions

#include "_include/endpoint.md"

We can send Video clips as attachment using below API. The maximum audio file size is limited to 64 MB.

```
{endpoint}whatsapp/message/send
```

#### Example Request With Interactive Choice Messgae

```
curl -X POST \
  '{endpoint}whatsapp/message/send' \
  -H 'authorization: Bearer d9e1cac3812186b353c5022xxxxx' \
  -H 'content-type: application/json' \
  -d '{
	"channels": [{
		"name": "whatsapp",
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

## Send Vcard / Contacts Message

#include "_include/endpoint.md"

We can send location using below API. The maximum audio file size is limited to 64 MB.

```
{endpoint}whatsapp/message/send
```

#### Example Request With Vcard Messgae

```
curl -X POST \
  '{endpoint}whatsapp/message/send' \
  -H 'authorization: Bearer d9e1cac3812186b353c5022xxxxx' \
  -H 'content-type: application/json' \
  -d '{
	"channels": [{
		"name": "whatsapp",
		"from": "919019120xxx"
	}],
	"recipient": {
		"to": "91XXXXXX"
	},
	"message": {
		"type": "contacts",
		"payload": [{
			"addresses": [{
				"city": "Bangalore",
				"country": "India",
				"country_code": "in",
				"state": "KA",
				"type": "Office",
				"zip": "560078"
			}],
			"birthday": "1993-08-18",
			"emails": [{
				"email": "hello@domin-name.com",
				"type": "WORK"
			}],
			"name": {
				"first_name": "Laxman",
				"formatted_name": "Laxman Ka",
				"last_name": "Ka"
			},
			"phones": [{
				"phone": "919019120xxx",
				"type": "HOME"
			}],
			"urls": [{
				"url": "https://www.domin-name.com",
				"type": "WORK"
			}]
		}]
	}
}'
```

#### PARAMETERS

| Name    | Description                    | Limits | Required |
| ------- | ------------------------------ | ------ | -------- |
| phone   | Mobile numbers saved in mobile | N/A    | Yes      |
| name    | Person name                    | N/A    | No       |
| address | Address details of the contact | N/A    | No       |

## Send Location Message

#include "_include/endpoint.md"

We can send location using below API. The maximum audio file size is limited to 64 MB.

```
{endpoint}whatsapp/message/send
```

#### Example Request With Location Messgae

```
curl -X POST \
  '{endpoint}whatsapp/message/send' \
  -H 'authorization: Bearer d9e1cac3812186b353c5022xxxxx' \
  -H 'content-type: application/json' \
  -d '{
	"channels": [{
		"name": "whatsapp",
		"from": "919019120xxx"
	}],
	"recipient": {
		"to": "91XXXXXX"
	},
    "message" : {
        "type": "location",
        "payload" : {
            "longitude": 12.912985,
            "latitude": 77.599505,
            "name": "Company Pvt Ltd",
            "address": "JP Nagar, Mini forest"
        }
    }
}'
```

#### PARAMETERS

| Name      | Description                           | Limits | Required |
| --------- | ------------------------------------- | ------ | -------- |
| longitude | Longitude of the location coordinates | N/A    | Yes      |
| latitude  | Latitude of the location coordinates  | N/A    | Yes      |
| name      | Address name                          | N/A    | No       |
| address   | Textual representation of location    | N/A    | No       |

## Send Carousel Message

#include "_include/endpoint.md"

We can send Carousel using below API. The maximum audio file size is limited to 64 MB.

```
{endpoint}whatsapp/message/send
```

#### Example Request With Carousel Messgae

```
curl -X POST \
  '{endpoint}whatsapp/message/send' \
  -H 'authorization: Bearer d9e1cac3812186b353c5022xxxxx' \
  -H 'content-type: application/json' \
  -d '{
	"channels": [{
		"name": "whatsapp",
		"from": "919019120xxx"
	}],
	"recipient": {
		"to": "91XXXXXX"
	},
    "message" : {
        "payload" : {
            --Coming Soon ----
        }
    }
}'
```

## Send Card Message

#include "_include/endpoint.md"

We can send Carousel using below API. The maximum audio file size is limited to 64 MB.

```
{endpoint}whatsapp/message/send
```

#### Example Request With Card Messgae

```
curl -X POST \
  '{endpoint}whatsapp/message/send' \
  -H 'authorization: Bearer d9e1cac3812186b353c5022xxxxx' \
  -H 'content-type: application/json' \
  -d '{
	"channels": [{
		"name": "whatsapp",
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
