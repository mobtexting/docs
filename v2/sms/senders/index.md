# View Senders List

View all Sender-ids created under your account
#include "_include/endpoint.md"

#### GET

```
{endpoint}sms/senders
```

#### PARAMETERS

| name         | optional | value                  |
| ------------ | -------- | ---------------------- |
| filter[name] | Yes      | name of the sender-id. |

#### Example Request

```
curl -X GET \
  '{endpoint}sms/senders' \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 5b02112fb7xxxxxxxxx'
```

Kindly replace the token with your respective access_token and other params.

#### Example Response

```json
{
    "status": "OK",
    "code": 200,
    "message": "Senders List",
    "data": [
        {
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
        },
      ....
    ],
        "links": {
        "first": "{endpoint}sms/senders?page=1",
        "last": "{endpoint}sms/senders?page=7",
        "prev": null,
        "next": "{endpoint}sms/senders?page=2"
    },
    "meta": {
        "current_page": 1,
        "from": 1,
        "last_page": 7,
        "links": [
            {
                "url": null,
                "label": "&laquo; Previous",
                "active": false
            },
            {
                "url": "{endpoint}sms/senders?page=1",
                "label": "1",
                "active": true
            },
      ....
        ],
        "path": "{endpoint}sms/senders",
        "per_page": 15,
        "to": 15,
        "total": 92
  }
}
```

#### Status Description 

| status value | description |
| ------------ | ------------|
| 0            | Pending     |
| 1            | Approved    |
| 2            | Rejected    |
