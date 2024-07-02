# PULL DLR STATUS
#include "_include/endpoint.md"

#### GET

```
{endpoint}sms/status?id=469ea920-ccd1-4a39-b728-c0b6f15f6aa6:1
```

You can send sms using `GET` method. GET method requires data should be url_encoded.

#### ACCEPTED PARAMETERS

| Name     | Descriptions                         |
| -------- | ------------------------------------ |
| id       | Message Id we have given in response |
| mobile   | Mobile number with country code      |
| cid      | Your custom id                       |
| date     | For which date you want the report   |
| group_id | Message group Id                     |

you can pass any of the above params to get the dlr response.

#### Example Request

#code "{version}/_code/sms/pull-dlr.json"

#### Example Response

```json
{
  "status": 200,
  "message": "OK",
  "data": [
    {
      "id": "469ea920-ccd1-4a39-b728-c0b6f15f6aa6:1",
      "mobile": "9189212693xx",
      "status": "DELIVRD",
      "units": 1,
      "length": 7,
      "charges": 1,
      "custom": "",
      "location": "",
      "provider": "",
      "submitted_at": "2018-07-06 09:57:42",
      "delivered_at": "2018-07-06 21:57:42"
    }
  ]
}
```

#### Example Response with pagination

You will receive the pagination links if request contains `group_id` or `date`
You will be limited the records 100 per page.

```json
{
    "status": "OK",
    "code": 200,
    "message": "OK",
    "data": [
        {
            "id": "6bb5da1a-b53e-4fbd-b0ae-6926cad4540b:1",
            "mobile": "918074318216",
            "status": "AWAITING-DLR",
            "units": 1,
            "service": "T",
            "length": 10,
            "charges": 1,
            "custom": "",
            "custom1": "",
            "location": "",
            "provider": "",
            "submitted_at": "2024-06-24 09:51:03",
            "delivered_at": "",
            "sender": "MOBTRN"
        },
        {
            "id": "6bb5da1a-b53e-4fbd-b0ae-6926cad4540b:2",
            "mobile": "919492839930",
            "status": "AWAITING-DLR",
            "units": 1,
            "service": "T",
            "length": 10,
            "charges": 1,
            "custom": "",
            "custom1": "",
            "location": "",
            "provider": "",
            "submitted_at": "2024-06-24 09:51:03",
            "delivered_at": "",
            "sender": "MOBTRN"
        }
    ],
    "links": {
        "first": "{endpoint}/api/v2/sms/status?page=1",
        "last": "{endpoint}/api/v2/sms/status?page=1",
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
                "url": "{endpoint}/api/v2/sms/status?page=1",
                "label": "1",
                "active": true
            },
            {
                "url": null,
                "label": "Next &raquo;",
                "active": false
            }
        ],
        "path": "{endpoint}/api/v2/sms/status",
        "per_page": 100,
        "to": 2,
        "total": 2
    }
}
```