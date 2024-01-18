# Whatsapp For Business API

## Channel Info

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

#### HTTP Methods

It will support only `POST` requests.
#include "_include/endpoint.md"

## Sending Text Message

```
{endpoint}whatsapp/message/send
```

#### PARAMETERS

| Name    | Description                                 | Limits              | Required |
| ------- | ------------------------------------------- | ------------------- | -------- |
| to      | Destination mobile number with country code | NA                  | Yes      |
| payload | Message Payload section                     | N/A                 | Yes      |
| text    | Message Content you want to send            | Max 4096 Characters | Yes      |

#### Example Request With Text Message

#code "{version}/_code/whatsapp/send_message/text_type.json"

## Sending Template Message
#include "_include/endpoint.md"

```
{endpoint}whatsapp/message/send
```

#### PARAMETERS

| Name          | Description                                                                                                                                                                                         | Limits                                                                | Required                                               |
| ------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------- | ------------------------------------------------------ |
| name          | Template `Alias` Name                                                                                                                                                                               | N/A                                                                   | yes                                                    |
| language      | Language to send the template in. Default `en`                                                                                                                                                      | N/A                                                                   | No                                                     |
| header_params | Only one header replace variable value.                                                                                                                                                             | Up to 1024 characters for all parameters and predefined template text | Yes incase only templates contain header variable      |
| body_params   | Up to 1024 characters for all parameters that are predefined template text, if `authentication` template has only one replace variable value.                                                       | Up to 1024 characters for all parameters and predefined template text | Yes incase only template contains body with no headers |
| components    | This block contains header, body, footer sections payload as per predefined template.                                                                                                               | Up to 1024 characters for all parameters and predefined template text | Yes incase Template contains headers and footers       |
| ttl           | Time to live of the template message. If the receiver has not opened the template message before the time to live expires, the message will be deleted. Default 30 Days. Need to specify in Seconds | Can be more than 1 day i.e 86400 sec                                  | No                                                     |

#### Example Request With Templates

#code "{version}/_code/whatsapp/send_message/template_type.json"

#### Example Request With Authentication Template

```
curl -X POST \
  '{endpoint}whatsapp/message/send' \
  -H 'authorization: Bearer d9e1cac3812186b353c5022xxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "channels": [
        {
            "name": "whatsapp",
            "from": "91901912xxxx"
        }
    ],
    "recipient": {
        "to": [
            "91XXXXXXx"
        ]
    },
    "message": {
        "type": "template",
        "payload": {
            "name": "template_alias_name",
            "language": "en",
            "body_params" : [23455]
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

## Send Image Message
#include "_include/endpoint.md"

```
{endpoint}whatsapp/message/send
```

#### PARAMETERS

| Name     | Description                                                                                                                                                                      | Limits | Required |
| -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------ | -------- |
| url      | Public url of the image file. Either HTTP/HTTPS link.                                                                                                                            | 5 MB   | Yes      |
| type     | `image/jpg`, `image/jpeg` and `image/png`                                                                                                                                        | YES    | YES      |
| caption  | some text for image caption                                                                                                                                                      | N/A    | No       |
| filename | Media file name                                                                                                                                                                  | N/A    | No       |
| pixels   | vertically crops images with the 1:91:1 aspect ratio: 800×418 pixels. To communicate effectively, design the image such that the crux information is at the center of the image. | YES    | YES      |

#### Example Request With Image Message

#code "{version}/_code/whatsapp/send_message/image_type.json"

## Send Document Message
#include "_include/endpoint.md"

We can send Document which is having valid MIME-type as attachment using below API. So anything not image, audio or video will be transmitted as document message.

```
{endpoint}whatsapp/message/send
```

#### PARAMETERS

| Name     | Description                                                 | Limits              | Required |
| -------- | ----------------------------------------------------------- | ------------------- | -------- |
| url      | Public url of the document file. Either HTTP or HTTPS link. | Max File size 100MB | Yes      |
| type     | Any valid MIME-type                                         | N/A                 | No       |
| caption  | some text for document caption                              | N/A                 | No       |
| filename | Media file name                                             | N/A                 | No       |

#### Example Request With Document Message

#code "{version}/_code/whatsapp/send_message/document_type.json"

## Send Audio Message
#include "_include/endpoint.md"

We can send Audio clips as attachment using below API.

```
{endpoint}whatsapp/message/send
```

#### PARAMETERS

| Name     | Description                                                                                             | Limits    | Required |
| -------- | ------------------------------------------------------------------------------------------------------- | --------- | -------- |
| url      | Public url of the audio file. Either HTTP or HTTPS link.                                                | Upto 16MB | Yes      |
| type     | `audio/aac, audio/mp4, audio/amr, audio/mpeg; codecs=opus.` (The base audio/ogg type is not supported.) | YES       | YES      |
| caption  | some text for audio caption                                                                             | N/A       | No       |
| filename | Media file name                                                                                         | N/A       | No       |

#### Example Request With Audio Message

#code "{version}/_code/whatsapp/send_message/audio_type.json"

## Send Video Message
#include "_include/endpoint.md"

We can send Video clips as attachment using below API.

```
{endpoint}whatsapp/message/send
```

#### PARAMETERS

| Name     | Description                                                                            | Limits    | Required |
| -------- | -------------------------------------------------------------------------------------- | --------- | -------- |
| url      | Public url of the video file. Either HTTP or HTTPS link.                               | Upto 16MB | Yes      |
| type     | `video/mp4, video/3gpp` (Only `H.264` video codec and `AAC` audio codec is supported.) | YES       | Yes      |
| caption  | some text for audio caption                                                            | N/A       | No       |
| filename | Media file name                                                                        | N/A       | No       |

#### Example Request With Video Message

#code "{version}/_code/whatsapp/send_message/video_type.json"

## Send Notification With Interactive Suggestions
#include "_include/endpoint.md"

```
{endpoint}whatsapp/message/send
```

#### PARAMETERS

| Name         | Description                                                                                                                                     | Limits | Required |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- | ------ | -------- |
| choices      | this block contains options list of the message                                                                                                 | N/A    | Yes      |
| payload.type | if reply message type value should be `reply`, or list message type value should be `list`                                                      | N/A    | Yes      |
| choices.type | if reply message type value should be `reply`, or list message type value first object should be `button` and second object should be `section` | N/A    | Yes      |

#### Example Request With Interactive Reply Message

#code "{version}/_code/whatsapp/send_message/interactive_type.json"

#### Example Request With Interactive List Messages

#code "{version}/_code/whatsapp/send_message/interactive_list.json"

## Send Vcard / Contacts Message
#include "_include/endpoint.md"

```
{endpoint}whatsapp/message/send
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

#### Example Request With Vcard Message

#code "{version}/_code/whatsapp/send_message/contact_message.json"

## Send Location Message
#include "_include/endpoint.md"

```
{endpoint}whatsapp/message/send
```

#### PARAMETERS

| Name      | Description                           | Limits | Required |
| --------- | ------------------------------------- | ------ | -------- |
| longitude | Longitude of the location coordinates | N/A    | Yes      |
| latitude  | Latitude of the location coordinates  | N/A    | Yes      |
| name      | Address name                          | N/A    | No       |
| address   | Textual representation of location    | N/A    | No       |

#### Example Request With Location Message

#code "{version}/_code/whatsapp/send_message/location_message.json"

