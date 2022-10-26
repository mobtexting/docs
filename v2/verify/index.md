# Verify Api

Verify API enables you to verify a mobile phone number with two-factor authentication.

This is useful for:

- Protecting against spam, by preventing spammers from creating multiple accounts
- Monitoring suspicious activity, by forcing an account user to verify ownership of a number
- Ensuring that you can reach your users at any time because you have their correct phone number

Create a new Verify object through the API to start the verification process of a recipient. We will take care of creating a token and making sure that the message gets delivered to the user's handset.

## Verify Request

#### API Endpoint

```
{domain}/api/{version}/
```

#### POST

```
{endpoint}verify/send
```

#### Payload

```json
{
  "channels": [
    {
      "name": "whatsapp",
      "from": "91901912xxx",
      "recipient": {
        "to": "9189195xxxx"
      },
      "order": 0,
      "wait": 60 // seconds
    },
    {
      "name": "sms",
      "from": "91901912xxx",
      "recipient": {
        "to": "9189195xxxx"
      },
      "order": 1,
      "wait": 60
    }
  ],
  "payload": {
    "ip_address": "192.168.*.*",
    "length": 6,
    "timeout": 6
  }
}
```

#### PARAMETERS

| Name       | Type   | Description                                                                             |
| ---------- | ------ | --------------------------------------------------------------------------------------- |
| foreign_id | string | A client reference                                                                      |
| timeout    | int    | The verification code expiry time in seconds. Default: 120                              |
| length     | string | The number of characters in the verification code. Must be between 4 and 10. Default: 6 |
| ip_address | string | The IP address used by your user when they entered the verification code.               |

#### OPTIONAL PARAMETERS

| Name     | Description                                                                                                               |
| -------- | ------------------------------------------------------------------------------------------------------------------------- | --- |
| template | Custom Message for sending otp if message object not specifed in verify config. use {token} in content for replacing otp. |     |

#### Example Response

```json
{
  "id": "fb5e1214-7c9f-4f54-b18f-78dc7a901dec",
  "status": "sent",
  "to": "919019955xxx",
  "reference": null,
  "created_at": "2019-01-31 14:41:48",
  "expire_at": "2019-01-31 14:43:48"
}
```
