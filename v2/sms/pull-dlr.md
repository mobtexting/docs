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

```curl
curl -X GET \
  '{endpoint}sms/status?id=469ea920-ccd1-xxxx&access_token=209eccd40e45b21xxxx'
```

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
    "status": 200,
    "message": "OK",
    "data": {
        "current_page": 1,
        "data": [
            {
                "id": "0703cf54-eef3-401c-8e7b-c1ea5b27b799:1",
                "mobile": "919538372357",
                "status": "AWAITING-DLR",
                "units": "1",
                "length": "14",
                "charges": 1,
                "custom": "",
                "location": "",
                "provider": "",
                "submitted_at": "2018-10-26 12:35:00",
                "delivered_at": ""
            },
            ---
        ],
        "from": 1,
        "last_page": 100,
        "first_page_url": "",
        "last_page_url": "",
        "next_page_url": "",
        "path": "",
        "per_page": 100,
        "prev_page_url": null,
        "to": 100,
        "total": 10000
    }
}
```
