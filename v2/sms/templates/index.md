## View Templates

View all templates created under your account

#### API Endpoint

```
{domain}/api/{version}/
```

#### GET

```
{endpoint}sms/templates
```

#### Filters

| name         | Optional | value                 |
| ------------ | -------- | --------------------- |
| filter[name] | Yes      | Name of the template. |

#### Example Request

```
curl -X GET \
  '{endpoint}sms/templates?filter[name]=test' \
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
        "id": "fab3ad9c-3cbb-47e7-af8e-9a9f0a5e362d",
        "sender_id": "66e834c8-d932-4cc7-a336-7b8ea8f78ba9",
        "template_id": "1107161521283358301",
        "template_type": "Transactional",
        "sender": "SENDER",
        "name": "hind-number",
        "body": "Your Verification code is:@{{1}} is code @{{2}}",
        "content": "Your Verification code is:@{{1}} and @{{2}}",
        "body_length": 53,
        "match_count": 0,
        "percentage": 0,
        "is_english": 1,
        "status": 1,
        "created_at": "2021-04-06 13:57:33",
        "updated_at": "2021-04-14 17:32:53",
        "serial": 1
      }
    ],
    "first_page_url": "{endpoint}sms/templates?page=1",
    "from": 1,
    "last_page": 1,
    "last_page_url": "{endpoint}sms/templates?page=1",
    "next_page_url": null,
    "path": "{endpoint}sms/templates",
    "per_page": 25,
    "prev_page_url": null,
    "to": 1,
    "total": 1
  }
}
```
