# Messaging

The SMS API supports the following:

#### HTTP Methods

`POST` - When you send a POST request with the end user's phone number to the messaging subresource, We sends the SMS message you specify.

Country code is mandatory to be included in the `to` paramenter for global messaging.

Before you start sending SMS through this API, please test whether your content is matching a template which has been pre approved. Otherwise, the SMS will end up being rejected.

## Send SMS

#### API Endpoint

```
{domain}/api/{version}/
```

#### POST

```
{endpoint}sms/send
```

#### MANDATORY PARAMETERS

| Name    | Descriptions                                                                                 |
| ------- | -------------------------------------------------------------------------------------------- |
| to      | Phone number to send with country prefix.                                                    |
| message | The content of the SMS                                                                       |
| sender  | The registered and approved Sender-id                                                        |
| service | The short code of the service name. ex: (MKT) [full list](/docs/{version}/#content-products) |

#### OPTIONAL PARAMETERS

| Name        | Descriptions                                                                                                                                                           |
| ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| webhook_id  | The `id` of the webhook created in Webhook Section for which the SMS response to be sent after delivery report from operator. [read more](/docs/{version}/sms/webhook) |
| time        | Schedule time (in format i.e,yyyy-mm-dd hh:mm:ss) at which the SMS has to be sent.                                                                                     |
| type        | The SMS to be sent is Unicode, Normal or Auto detect. (value "U", "N" or "A")                                                                                          |
| flash       | This parameter can be used to send flash sms via API ( Values 1 or 0.)                                                                                                 |
| custom      | Your own unique_id                                                                                                                                                     |
| port        | Port number to which SMS has to be delivered                                                                                                                           |
| entity_id   | Principal Entityid registered in DLT portal (applicable for indian routes only)                                                                                        |
| template_id | TemplateId registered in DLT portal (applicable for indian routes only)                                                                                                |

#### Example Request

```
curl -X POST '{endpoint}sms/send' \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 38e896f55670311982434e929559bxxxx' \
    -H 'Content-Type: application/x-www-form-urlencoded' \
    -d 'sender=TXTSMS' \
    -d 'to=917026267xxx' \
    -d 'service=MKT' \
    -d 'message=Your OTP is 123456'
```

#### Example Response

```json
{
  "status": 200,
  "message": "1 numbers accepted for delivery.",
  "data": [
    {
      "id": "b34e35ad-fe34-4a8b-977c-b21cd76cd7d6:1",
      "mobile": "918921269xxx",
      "status": "AWAITING-DLR",
      "units": 1,
      "length": 7,
      "charges": 1,
      "customid": "",
      "iso_code": null,
      "submitted_at": "2018-07-09 16:27:35"
    }
  ]
}
```
