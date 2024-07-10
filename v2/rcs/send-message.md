# RCS Messaging Service

## Channel Info

```
{
	"channels": [{
		"name": "rcs",
		"from": "700969ca-0cb2-11ec-a2cxxxx", //Agent ID
        "meta" : {
            "foreign_id":"your-custom-id",
            "tags": ["tag1", "tag2"]
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
      "channel": "rcs",
      "from": "700969ca-0cb2-11ec-a2cxxxx",
      "recipient": "9190199xxxxx",
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
| channels  | This block contains information related messaging channel   | N/A                 | Yes                            |
| name      | Name of Messaging Channel. `whatsapp                        | rcs                 | ip_message`                    | `string` | Yes |
| from      | RCS Agent Reference ID                                      | `string`            | Yes                            |
| recipient | This block contains contacts information related to channel | N/A                 | Yes                            |
| group_id  | Segment id which contain list of phone numbers              | `string` or `array` | Yes if `to` param not present  |
| to        | Receiver mobile numbers : `text`                            | `array`             | Yes, if `group_id` not present |
| meta      | This block contains all the optional parameters             | `object`            | No                             |
| tags      | opt-out the message based on the tags.                      | `string`            | No                             |

`Note` : The `recipient` block inside channel is related to particular communication channel and it is optional. The outside `recipient` channel contain common recipients for every channel.

#### HTTP Methods

It will support only `POST` requests.
#include "_include/endpoint.md"

## Sending Text Message

```
{endpoint}rcs/message/send
```

#### Example Request With Text Messgae

#code "{version}/_code/rcs/text_message.json"

#### PARAMETERS

| Name    | Description                                 | Limits              | Required |
| ------- | ------------------------------------------- | ------------------- | -------- |
| payload | Messaage Payload section                    | N/A                 | Yes      |
| to      | Destination mobile number with country code | NA                  | Yes      |
| text    | Message Content you want to send            | Max 4096 Characters | Yes      |

## Sending Media Message

Using Media Message you can send image, audio, video and document files to your customers.

```
{endpoint}rcs/message/send
```

#### Example Request With Image Messgae

#code "{version}/_code/rcs/image_message.json"

#### PARAMETERS

| Name    | Description                                                                                                                              | Limits     | Required |
| ------- | ---------------------------------------------------------------------------------------------------------------------------------------- | ---------- | -------- |
| payload | Messaage Payload section                                                                                                                 | N/A        | Yes      |
| to      | Destination mobile number with country code                                                                                              | NA         | Yes      |
| type    | Media types supported image/jpeg, image/jpg, image/gif, image/png, video/h263, video/m4v, video/mp4, video/mpeg, video/mpeg4, video/webm | NA         | Yes      |
| url     | Publicly available Image/ Media URL                                                                                                      | Max 100 MB | Yes      |

## Send Interactive Message

#include "_include/endpoint.md"

We can send interactive messages like suggested replies and suggested actions using this api.

Suggested replies[text] have a maximum of 25 characters.

```
{endpoint}rcs/message/send
```

#### Example Request With Interactive Choice Messgae

The following code sends text with two suggested replies

#code "{version}/_code/rcs/interactive_message.json"

#### PARAMETERS

| Name    | Description                                                                   | Limits        | Required |
| ------- | ----------------------------------------------------------------------------- | ------------- | -------- |
| header  | Optional                                                                      | N/A           | No       |
| body    | this block contains acutal content for the message                            | N/A           | Yes      |
| footer  | Optional                                                                      | N/A           | No       |
| choices | this block contains actions for suggestions of the message                    | N/A           | Yes      |
| text    | this parameter holds suggested reply text                                     | Max 25 Chars. | Yes      |
| content | this parameter holds suggested reply text's identification for your reference | N/A           | Yes      |

#### Example Request with suggested actions:

The following code sends text with two suggested actions

```
curl -X POST \
  '{endpoint}rcs/message/send' \
  -H 'authorization: Bearer d9e1cac3812186b353c5022xxxxx' \
  -H 'content-type: application/json' \
  -d '{
	"channels": [{
		"name": "rcs",
		"from": "700969ca-0cb2-11ec-a2cxxxx"
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
			"choices": [
				{
					"type": "location",
					"payload": {
						"longitude": 12.912985,
            "latitude": 77.599505,
            "name": "Company Pvt Ltd",
            "address": "JP Nagar, Mini forest"
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
				}
			]
		}
	}
}'
```

#### PARAMETERS

| Name      | Description                                                | Limits                                | Required |
| --------- | ---------------------------------------------------------- | ------------------------------------- | -------- |
| header    | Optional                                                   | N/A                                   | No       |
| body      | this block contains acutal content for the message         | N/A                                   | Yes      |
| footer    | Optional                                                   | N/A                                   | No       |
| choices   | this block contains actions for suggestions of the message | N/A                                   | Yes      |
| latitude  | The latitude in degrees.                                   | must be in the range [-90.0, +90.0]   | Yes      |
| longitude | The longitude in degrees.                                  | must be in the range [-180.0, +180.0] | Yes      |
| calender  | creates user's calender event upon click                   | N/A                                   | Yes      |

## Send Card Message

#include "_include/endpoint.md"

We can send RichRCard Message using below API.

```
{endpoint}rcs/message/send
```

#### Example Request With Card Messgae

#code "{version}/_code/rcs/card_message.json"

#### PARAMETERS

| Name                | Description                                                      | Limits           | Required |
| ------------------- | ---------------------------------------------------------------- | ---------------- | -------- |
| type                | Type of the message Ex: "card"                                   | NA               | Yes      |
| payload             | Actual message data                                              | NA               | Yes      |
| title               | Title of the card                                                | NA               | Yes      |
| description         | Description of the card                                          | NA               | Yes      |
| body                | This section contains media file information                     | NA               | Yes      |
| body.payload.height | Height of the card SHORT [112 DP], MEDIUM [168 DP], TALL[264 DP] | Yes              |
| choices             | This section contains choices for selection                      | Max of 4 choices | No       |

## Send Carousel Message

Carousels may contain a minimum of two and a maximum of ten rich cards.
#include "_include/endpoint.md"

We can send Carousel using below API.

```
{endpoint}rcs/message/send
```

#### Example Request With Carousel Messgae

#code "{version}/_code/rcs/carousel_message.json"

#### PARAMETERS

| Name                | Description                                                      | Limits           | Required |
| ------------------- | ---------------------------------------------------------------- | ---------------- | -------- |
| type                | Type of the message Ex: "carousel"                               | NA               | Yes      |
| payload             | Actual message data                                              | NA               | Yes      |
| title               | Title of the card                                                | Max of 200 chars | Yes      |
| description         | Description of the card                                          | Max of 200 chars | Yes      |
| body                | This section contains media file information                     | NA               | Yes      |
| choices             | This section contains choices for selection                      | Max of 4 choices | No       |
| body.payload.height | Height of the card SHORT [112 DP], MEDIUM [168 DP], TALL[264 DP] | Yes              |

Note: TALL cannot be used for rich card carousels when the card width is set to SMALL
