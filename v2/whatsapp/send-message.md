# Whatsapp For Business API

## Channel Info

```
{
	"channels": [{
		"name": "whatsapp",
		"from": "91901912xxxx",
        "meta" : {
            "foreign_id":"your-custom-id"
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
      "status": "queued",
      "foreign_id": "your-message-id"
    }
  ]
}
```

#### PARAMETERS

| Name      | Description                                                 | type                | Required                       |
| --------- | ----------------------------------------------------------- | ------------------- | ------------------------------ |
| channels  | This block contains information related messaging channel   | N/A                 | Yes                            |
| name      | Name of Messaging Channel. Ex: `whatsapp`                   | `string`            | Yes                            |
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

#### Example Request With Text Message

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
| payload | Message Payload section                     | N/A                 | Yes      |
| to      | Destination mobile number with country code | NA                  | Yes      |
| text    | Message Content you want to send            | Max 4096 Characters | Yes      |

## Sending Template Message
#include "_include/endpoint.md"

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
			"namespace": "",
			"language": "en",
			"body_params": ["223344", "10"],
			"components": []
		}
	}
}'
```

#### Example Request With Template "HSM" (Highly Structured Message)

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
			"namespace": "",
			"language": "en",
			"components": [{
					"type": "header",
					"parameters": [{
						"type": "text",
						"text": "replacement_text"
					}]
				},
				{
					"type": "body",
					"parameters": [{
							"type": "text",
							"text": "replacement_text"
						},
						{
							"type": "currency",
							"currency": {
								"fallback_value": "$100.99",
								"code": "USD",
								"amount_1000": 100990
							}
						},
						{
							"type": "date_time",
							"date_time": {
								"fallback_value": "February 25, 1977",
								"day_of_week": 5,
								"day_of_month": 25,
								"year": 1977,
								"month": 2,
								"hour": 15,
								"minute": 33
							}
						},
						{
							"...": "..."
						}
					]
				},
				{
					"type": "button",
					"sub_type": "quick_reply",
					"index": "0",
					"parameters": [{
						"type": "payload",
						"payload": "aGlzIHRoaXMgaXMgY29vZHNhc2phZHdpcXdlMGZoIGFTIEZISUQgV1FEV0RT"
					}]
				},
				{
					"type": "button",
					"sub_type": "url",
					"index": "1",
					"parameters": [{
						"type": "text",
						"text": "9rwnB8RbYmPF5t2Mn09x4h"
					}]
				},
				{
					"type": "button",
					"sub_type": "url",
					"index": "2",
					"parameters": [{
						"type": "text",
						"text": "ticket.pdf"
					}]
				}
			]
		}
	}
}'
```

#### Example Product Shipment Request With Template

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
			"name": "oculus_shipment_update",
			"namespace": "88b39973_f0d5_54e1_29cf_e80f1e3da4f2",
			"language": "en",
			"components": "components": [{
				"type": "header",
				"parameters": [{
					"type": "image",
					"image": {
						"link": "link-to-your-image"
					}
				}]
			},
			{
				"type": "body",
				"parameters": [{
						"type": "text",
						"text": "Anand"
					},
					{
						"type": "text",
						"text": "Quest"
					},
					{
						"type": "text",
						"text": "113-0921387"
					},
					{
						"type": "date_time",
						"date_time": {
							"fallback_value": "23rd Nov 2019",
							"day_of_month": "20",
							"year": "2019",
							"month": "9"
						}
					}
				]
			},
			{
				"type": "button",
				"index": "0",
				"sub_type": "url",
				"parameters": [{
					"type": "text",
					"text": "1Z999AA10123456784"
				}]
			}
		]
		}
	}
}'
```

#### PARAMETERS

| Name        | Description                                                                                                                                                                                         | Limits                                                                | Required                                               |
| ----------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------- | ------------------------------------------------------ |
| name        | Template Alias Name                                                                                                                                                                                 | N/A                                                                   | yes                                                    |
| namespace   | Namespace of the template                                                                                                                                                                           | N/A                                                                   | yes                                                    |
| language    | Language to send the template in. Default `en`                                                                                                                                                      | N/A                                                                   | No                                                     |
| body_params | Up to 1024 characters for all parameters that are predefined template text.                                                                                                                         | Up to 1024 characters for all parameters and predefined template text | Yes incase only template contains body with no headers |
| components  | This block contains header, body, footer sections payload as per predefined template.                                                                                                               | Up to 1024 characters for all parameters and predefined template text | Yes incase Template contains headers and footers       |
| ttl         | Time to live of the template message. If the receiver has not opened the template message before the time to live expires, the message will be deleted. Default 30 Days. Need to specify in Seconds | Can be more than 1 day i.e 86400 sec                                  | No                                                     |

## Send Image Message
#include "_include/endpoint.md"

We can send Images as attachment using below API. The maximum image size is limited to 64 MB.

```
{endpoint}whatsapp/message/send
```

#### Example Request With Image Message

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
			"url": "https://www.buildquickbots.com/whatsapp/media/sample/jpg/sample01.jpg",
			"caption": "some caption for image",
            "filename": ""
		}
	}
}'
```

#### PARAMETERS

| Name     | Description                                                                                                                                                                      | Limits | Required |
| -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------ | -------- |
| url      | Public url of the image file. Either HTTP/HTTPS link.                                                                                                                            | 5 MB   | Yes      |
| type     | `image/jpg`, `image/jpeg` and `image/png`                                                                                                                                        | YES    | YES      |
| caption  | some text for image caption                                                                                                                                                      | N/A    | No       |
| filename | Media file name                                                                                                                                                                  | N/A    | No       |
| pixels   | vertically crops images with the 1:91:1 aspect ratio: 800×418 pixels. To communicate effectively, design the image such that the crux information is at the center of the image. | YES    | YES      |

## Send Document Message
#include "_include/endpoint.md"

We can send Document which is having valid MIME-type as attachment using below API. The maximum document size is limited to 64 MB. So anything not image, audio or video will be transmitted as document message.

```
{endpoint}whatsapp/message/send
```

#### Example Request With Document Message

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
			"url": "https://www.buildquickbots.com/whatsapp/media/sample/pdf/sample01.pdf",
			"caption": "some caption for document",
			"filename": ""
		}
	}
}'
```

#### PARAMETERS

| Name     | Description                                                 | Limits              | Required |
| -------- | ----------------------------------------------------------- | ------------------- | -------- |
| url      | Public url of the document file. Either HTTP or HTTPS link. | Max File size 100MB | Yes      |
| type     | Any valid MIME-type                                         | N/A                 | No       |
| caption  | some text for document caption                              | N/A                 | No       |
| filename | Media file name                                             | N/A                 | No       |

## Send Audio Message
#include "_include/endpoint.md"

We can send Audio clips as attachment using below API. The maximum audio file size is limited to max 64 MB.

```
{endpoint}whatsapp/message/send
```

#### Example Request With Audio Message

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
			"url": "https://www.buildquickbots.com/whatsapp/media/sample/audio/sample02.mp3",
			"caption": "some caption for document",
			"filename": ""
		}
	}
}'
```

#### PARAMETERS

| Name     | Description                                                                                             | Limits    | Required |
| -------- | ------------------------------------------------------------------------------------------------------- | --------- | -------- |
| url      | Public url of the audio file. Either HTTP or HTTPS link.                                                | Upto 16MB | Yes      |
| type     | `audio/aac, audio/mp4, audio/amr, audio/mpeg; codecs=opus.` (The base audio/ogg type is not supported.) | YES       | YES      |
| caption  | some text for audio caption                                                                             | N/A       | No       |
| filename | Media file name                                                                                         | N/A       | No       |

## Send Video Message
#include "_include/endpoint.md"

We can send Video clips as attachment using below API. The maximum audio file size is limited to 64 MB.

```
{endpoint}whatsapp/message/send
```

#### Example Request With Video Message

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
			"url": "https://www.buildquickbots.com/whatsapp/media/sample/video/sample01.mp4",
			"caption": "some caption for document",
			"filename": ""
		}
	}
}'
```

#### PARAMETERS

| Name     | Description                                                                            | Limits    | Required |
| -------- | -------------------------------------------------------------------------------------- | --------- | -------- |
| url      | Public url of the video file. Either HTTP or HTTPS link.                               | Upto 16MB | Yes      |
| type     | `video/mp4, video/3gpp` (Only `H.264` video codec and `AAC` audio codec is supported.) | YES       | Yes      |
| caption  | some text for audio caption                                                            | N/A       | No       |
| filename | Media file name                                                                        | N/A       | No       |

## Send Notification With Interactive Suggestions
#include "_include/endpoint.md"

```
{endpoint}whatsapp/message/send
```

#### Example Request With Interactive Reply Message

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
			"type": "reply",
			"header": {
				"type": "text",
				"payload": {
					"text": "Hello User,"
				}
			},
			"body": {
				"type": "text",
				"payload": {
					"text": "Do you like the whatsapp?"
				}
			},
			"footer": {
				"type": "text",
				"payload": {
					"text": "Thank you"
				}
			},
			"choices": [
				{
					"type": "reply",
					"payload": {
						"title": "Yes",
						"id": "1"
					}
				},
				{
					"type": "reply",
					"payload": {
						"title": "No",
						"id": "2"
					}
				}
			]
		}
	}
}'
```

#### Example Request With Interactive List Messages

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
			"type": "list",
			"header": {
				"type": "text",
				"payload": {
					"text": "Hello User,"
				}
			},
			"body": {
				"type": "text",
				"payload": {
					"text": "What is your favorite color?"
				}
			},
			"footer": {
				"type": "text",
				"payload": {
					"text": "Thank you"
				}
			},
			"choices": [
				{
					"type": "button",
					"payload": {
						"title": "Choose the option",
						"rows": [{
							"id": "15",
							"title": "Green",
							"description": "Yes, Green is my favorite"
						}]
					}
				},
				{
					"type": "section",
					"payload": {
						"title": "Section2 Title",
						"rows": [{
							"id": "16",
							"title": "Red",
							"description": "Yes, Red is my favorite"
						},
						{
							"id": "16",
							"title": "Black",
							"description": "Yes, Black is my favorite"
						},
						{
							"id": "16",
							"title": "Blue",
							"description": "Yes, Blue is my favorite"
						}]
					}
				}
			]
		}
	}
}'
```

#### PARAMETERS

| Name         | Description                                                                                                                                     | Limits | Required |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- | ------ | -------- |
| choices      | this block contains options list of the message                                                                                                 | N/A    | Yes      |
| payload.type | if reply message type value should be `reply`, or list message type value should be `list`                                                      | N/A    | Yes      |
| choices.type | if reply message type value should be `reply`, or list message type value first object should be `button` and second object should be `section` | N/A    | Yes      |

## Send Vcard / Contacts Message
#include "_include/endpoint.md"

We can send location using below API. The maximum audio file size is limited to 64 MB.

```
{endpoint}whatsapp/message/send
```

#### Example Request With Vcard Message

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
		"payload": {
			"addresses": [{
				"city": "Bangalore",
				"country": "India",
				"countryCode": "in",
				"state": "KA",
				"type": "Office",
				"zip": "560078"
			}],
			"name": {
				"firstName": "MOB",
				"lastName": "Texting"
				"formattedName": "MOB Texting",
			},
			"phones": [{
				"phone": "91901xxxxxxx",
				"type": "WORK"
			}],
			"org": {
                "company": "MOBTexting",
                "department": "Product",
                "title": "Manager"
            },
			"birthday": "1993-08-18",
			"emails": [{
				"email": "hello@domain-name.com",
				"type": "WORK"
			}],
			"urls": [{
				"url": "https://www.domin-name.com",
				"type": "WORK"
			}]
		}
	}
}'
```

#### PARAMETERS

| Name     | Description                         | Limits | Required |
| -------- | ----------------------------------- | ------ | -------- |
| phone    | Mobile numbers saved in mobile      | N/A    | Yes      |
| name     | Person name                         | N/A    | Yes      |
| address  | Address details of the contact      | N/A    | Yes      |
| org      | Organization details of the contact | N/A    | Yes      |
| emails   | emails details of the contact       | N/A    | Yes      |
| urls     | urls details of the contact         | N/A    | Yes      |
| birthday | birthday details of the contact     | N/A    | No       |

## Send Location Message
#include "_include/endpoint.md"

We can send location using below API. The maximum audio file size is limited to 64 MB.

```
{endpoint}whatsapp/message/send
```

#### Example Request With Location Message

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
| latitude  | Latitude of the location coordinates  | N/A    | No       |
| name      | Address name                          | N/A    | No       |
| address   | Textual representation of location    | N/A    | No       |
