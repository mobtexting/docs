# View Template

View one template created under your account
#include "_include/endpoint.md"

#### GET

```
{endpoint}sms/templates/{id}
```

#### Example Request

```
curl -X GET \
  '{endpoint}sms/templates/b23769e6-019f-48f4-aae9-ec00a5xxxxxx' \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 5b02112fb7xxxxxxxxx'
```

Kindly replace the token with your respective access_token .

#### Example Response

```json
{
    "status": "OK",
    "code": 200,
    "message": "Template Data",
    "data": {
         "id": "b23769e6-019f-48f4-aae9-ec00a5xxxxxx",
         "sender_id": "015c2f82-1352-4d19-9f8f-b8449xxxxxx",
         "template_id": "1107161521283358301",
         "template_type": "Transactional",
         "sender": "SENDER",
         "name": "hind-number",
         "alias": "hind-number",
         "body": "Your Verification code is:@{{1}} is code @{{2}}",
         "content": null,
         "body_length": 53,
         "match_count": 0,
         "percentage": 0,
         "is_complete": 0,
         "is_english": 1,
         "status": 1,
         "created_at": "2022-11-16T04:41:32.000000Z",
         "updated_at": "2022-11-16T04:56:11.000000Z"
    }
}
```
