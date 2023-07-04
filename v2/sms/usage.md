# View Account Usage Report

It will display account usage report
#include "_include/endpoint.md"

#### GET

```
{endpoint}sms/activity
```

#### PARAMETERS

#### Example Request

```
curl -X GET \
  '{endpoint}sms/activity' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer 209eccd40ee3a2e14af7fe45b21xxx'
  -H 'Content-Type: application/json'
```

Kindly replace the token with your respective access_token and other params.

#### Example Response

```json
{
    "rows": {
        "current_page": 1,
        "data": [
           {
                "service": "S",
                "opening": "0.0000",
                "available": "0.0000",
                "sent_units": "5",
                "sent_credits": "5.0000",
                "deliv_units": "0",
                "on_date": "2019-05-07",
                "serial": 1
            },
            {
                "service": "S",
                "opening": "0.0000",
                "available": "0.0000",
                "sent_units": "16",
                "sent_credits": "16.0000",
                "deliv_units": "0",
                "on_date": "2018-05-08",
                "serial": 2
            },
        ---
        ],
        "first_page_url": "{endpoint}sms/activty?page=1",
        "from": 1,
        "last_page": 1,
        "last_page_url": "{endpoint}sms/activity?page=1",
        "next_page_url": null,
        "path": "{endpoint}sms/activity",
        "per_page": 25,
        "prev_page_url": null,
        "to": 16,
        "total": 16
    }
}
```
