# Edit Smart Link

Convert long url into short and smart url.
#include "_include/endpoint.md"

#### PUT

```
{endpoint}link/urls/{id}
```

#### PARAMETERS

| Name        | Optional | Descriptions                     |
| ----------- | -------- | -------------------------------- |
| long_url    | no       | Long Url                         |
| title       | yes      | Link title.                      |
| webhook_id  | yes      | Webhook ID created in our portal |
| is_advanced | yes      | Want to track mobile number      |

#### Example Request

```
curl -X POST \
  '{endpoint}link/urls/{id}' \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 5b02112fb7xxxxxxxxx'
    -H 'Content-Type: application/json' \
    -d '{
      "long_url": "https://www.example.com",
      "title": "testing",
      "webhook_id": "5558",
      "is_advanced": "1"
}'
```

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Link Updated Successfully",
  "data": {
    "id": 5,
    "title": "testing",
    "short_url": "https://tx3.in/",
    "long_url": "https://o5o4o6.com/?a=1457&c=298748&s1=TN(air(40_50)",
    "webhook_id": "5558",
    "token": null,
    "visits": [],
    "last_visited": null,
    "is_advanced": "1",
    "status": 1,
    "created_at": "2022-10-28T12:37:43.000000Z",
    "updated_at": "2022-10-28T12:37:43.000000Z"
  }
}
```
