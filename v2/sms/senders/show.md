# View Sender

View one Sender-ids created under your account
#include "_include/endpoint.md"

#### GET

```
{endpoint}sms/senders/{id}
```

#### Example Request

```
curl -X GET \
  '{endpoint}sms/senders/ff467e28-7170-4a72-952e-c999cxxxxxx' \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 5b02112fb7xxxxxxxxx'
```

Kindly replace the token with your respective access_token.

#### Example Response

```json
{
    "status": "OK",
    "code": 200,
    "message": "Sender Data",
    "data": {
        "id": "ff467e28-7170-4a72-952e-c999cxxxxxx",
        "name": "SENDER",
        "service": {
            "id": 55,
            "display_name": "Global SMS",
            "name": "G"
        },
        "entity_name": "SAMPLE COMPANY",
        "entity_id": "123233434355345555",
        "header_id": null,
        "iso": "IN",
        "message": null,
        "document": null,
        "is_open": 0,
        "purpose": 1,
        "status": 1,
        "created_at": "2022-11-16T06:53:26.000000Z",
        "updated_at": "2022-11-16T06:55:55.000000Z"
    }
}
```

#### Status Description 

| status value | description |
| ------------ | ------------|
| 0            | Pending     |
| 1            | Approved    |
| 2            | Rejected    |
