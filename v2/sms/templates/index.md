# View Templates

View all templates created under your account
#include "_include/endpoint.md"

#### GET

```
{endpoint}sms/templates
```

#### Filters

| name         | Optional | value                 |
| ------------ | -------- | --------------------- |
| filter[name] | Yes      | Name of the template. |

#### Example Request
#include "{version}/_samples/sms/templates/index.md"

#### Example Response

```json
{
    "status": "OK",
    "code": 200,
    "message": "Templates List",
    "data": [
        {
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
        },
      ....
    ],
   "links": {
        "first": "{endpoint}sms/templates?page=1",
        "last": "{endpoint}sms/templates?page=3",
        "prev": null,
        "next": "{endpoint}sms/templates?page=2"
    },
    "meta": {
        "current_page": 1,
        "from": 1,
        "last_page": 3,
        "links": [
            {
                "url": null,
                "label": "&laquo; Previous",
                "active": false
            },
            {
                "url": "{endpoint}sms/templates?page=1",
                "label": "1",
                "active": true
            },
          ....
        ],
        "path": "{endpoint}sms/templates",
        "per_page": 15,
        "to": 15,
        "total": 43
    }
}
```
