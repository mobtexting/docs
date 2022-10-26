## View Senders List

View all Sender-ids created under your account

#### API Endpoint

```
{domain}/api/{version}/
```

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
  '{endpoint}sms/senders \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 5b02112fb7xxxxxxxxx'
```

Kindly replace the token with your respective access_token and other params.

#### Example Response

```json
{
  "rows": {
    "current_page": 1,
    "data": [
      {
        "id": "f66b983b-713a-4818-a691-2c684eb4eccd",
        "user_id": 26,
        "name": "SENDER",
        "entity_name": "SAMPLE COMPANY",
        "entity_id": "123233434355345555",
        "header_id": null,
        "country_code": "IN",
        "message": null,
        "document": null,
        "status": 1,
        "is_open": 0,
        "purpose": null,
        "created_at": "2021-05-04 17:46:58",
        "updated_at": "2021-05-04 17:46:58",
        "serial": 1
      }
      ....
    ],
    "first_page_url": "{endpoint}sms/senders?page=1",
    "from": 1,
    "last_page": 1,
    "last_page_url": "{endpoint}sms/senders?page=1",
    "next_page_url": null,
    "path": "{endpoint}sms/senders",
    "per_page": 25,
    "prev_page_url": null,
    "to": 1,
    "total": 1
  }
}
```

#### Status Description 

| status value | description |
| ------------ | ------------|
| 0            | Pending     |
| 1            | Approved    |
| 2            | Rejected    |