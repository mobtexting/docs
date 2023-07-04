# View VMN Logs

Lists all message of VMN numbers of your account.
#include "_include/endpoint.md"

#### GET

```
{endpoint}vmn/logs
```

#### PARAMETERS

| name             | optional | value                                    |
| ---------------- | -------- | ---------------------------------------- |
| filter[mobile]   | Yes      | mobile number of the customer.           |
| filter[number]   | Yes      | vmn number.                              |
| date[created_at] | Yes      | date filter required format : 2022-02-12 |

#### Example Request

```
curl -X GET \
  '{endpoint}vmn/logs \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 5b02112fb7xxxxxxxxx'
```

Kindly replace the token with your respective access_token and other params.

#### Note:

This api have a throttling, so we will accept only 30 requests per minute for this api.

#### Example Response

```json
{
  "rows": {
    "current_page": 1,
    "data": [
      {
        "id": "0495240d-2e3c-4e1c-bd51-4b78291142bf",
        "user_id": 2,
        "mobile": "5ae61073-c9f7-4",
        "number": "919019120xxx",
        "first_keyword": "",
        "second_keyword": "",
        "body": "",
        "flow_id": 117,
        "location": null,
        "location_code": null,
        "region": null,
        "provider": null,
        "created_at": "2021-12-20T06:29:00.000000Z",
        "serial": 1
      },
      {
        "id": "0901c0e7-286c-4435-ad1c-312d296dfbb8",
        "user_id": 2,
        "mobile": "5ae61073-c9f7-4",
        "number": "919019120xxx",
        "first_keyword": "",
        "second_keyword": "",
        "body": "",
        "flow_id": 117,
        "location": null,
        "location_code": null,
        "region": null,
        "provider": null,
        "created_at": "2021-12-20T06:27:41.000000Z",
        "serial": 2
      },
      {
        "id": "2203989c-59da-4ccd-87c1-5d91127b8b5f",
        "user_id": 2,
        "mobile": "5ae61073-c9f7-4",
        "number": "919019120xxx",
        "first_keyword": "",
        "second_keyword": "",
        "body": "",
        "flow_id": 117,
        "location": null,
        "location_code": null,
        "region": null,
        "provider": null,
        "created_at": "2021-12-20T06:27:40.000000Z",
        "serial": 3
      }
    ],
    "first_page_url": "{endpoint}vmn/logs?page=1",
    "from": 1,
    "last_page": 1,
    "last_page_url": "{endpoint}vmn/logs?page=1",
    "links": [
      {
        "url": null,
        "label": "&laquo; Previous",
        "active": false
      },
      {
        "url": "{endpoint}vmn/logs?page=1",
        "label": "1",
        "active": true
      },
      {
        "url": null,
        "label": "Next &raquo;",
        "active": false
      }
    ],
    "next_page_url": null,
    "path": "{endpoint}vmn/logs",
    "per_page": 25,
    "prev_page_url": null,
    "to": 14,
    "total": 14
  }
}
```
