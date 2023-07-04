# Verify search

To check the status of past or current verification requests:

- Send a Verify Search request containing the `id` of the verification requests you are interested in.
- Check the `status` of the response to determine if the code the user supplied matches the one sent by {app}.
#include "_include/endpoint.md"

#### GET

```
{endpoint}verify/search/{id}
```

#### MANDATORY PARAMETERS

| Name | Type   | Description                                                                                       |
| ---- | ------ | ------------------------------------------------------------------------------------------------- |
| id   | string | The Verify request to check. This is the `id` you received in the response to the Verify request. |

#### Example Request

```curl
curl -X GET \
  '{endpoint}verify/search/fb5e1214-7c9f-4f54-b18f-78dc7a901dec \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer 38e896f55670311982434e929559bxxx' \
```

#### Example Response

```json
{
  "id": "fb5e1214-7c9f-4f54-b18f-78dc7a901dec",
  "to": "919019955xxx",
  "reference": null,
  "status": "sent",
  "created_at": "2019-01-31 14:41:48",
  "expire_at": "2019-01-31 14:43:48",
  "channels": [
    {
      "id": "38d70cec-1745-469d-80b3-19592a074ce2",
      "to": "919019955622",
      "from": "VERIFY",
      "channel": "sms",
      "event_id": "00a18bf7-dc06-4279-9ce6-068e3482eb51:1",
      "created_at": "2019-01-31 14:41:49",
      "status": null
    }
  ]
}
```
