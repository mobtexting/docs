# View Smart Links

View all smart links created under your account
#include "_include/endpoint.md"

#### GET

```
{endpoint}link/urls
```

#### PARAMETERS

#### Example Request

```
curl -X GET \
  '{endpoint}link/urls' \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 5b02112fb7xxxxxxxxx'
```

Kindly replace the token with your respective access_token and other params.

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "OK",
  "data": [
    {
      "id": 4,
      "title": "testing",
      "short_url": "https://tx3.in/",
      "long_url": "https://o5o4o6.com/?a=1457&c=298748&s1=TN(air(40_50)",
      "webhook_id": null,
      "token": null,
      "visits": 1,
      "last_visited": "2022-10-27 00:00:00",
      "is_advanced": 1,
      "status": 1,
      "created_at": "2022-10-11T09:58:42.000000Z",
      "updated_at": "2022-10-28T07:25:36.000000Z"
    }
  ],
  "links": {
    "first": "{endpoint}link/urls?page=1",
    "last": "{endpoint}link/urls?page=1",
    "prev": null,
    "next": null
  },
  "meta": {
    "current_page": 1,
    "from": 1,
    "last_page": 1,
    "links": [
      {
        "url": null,
        "label": "&laquo; Previous",
        "active": false
      },
      {
        "url": "{endpoint}link/urls?page=1",
        "label": "1",
        "active": true
      },
      {
        "url": null,
        "label": "Next &raquo;",
        "active": false
      }
    ],
    "path": "{endpoint}link/urls",
    "per_page": 15,
    "to": 1,
    "total": 1
  }
}
```
