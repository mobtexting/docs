# View Coverage list of all enabled countries

View Coverage list of all enabled countries under your account

#### GET

```
{domain}/api/v2/sms/locations/coveragelist
```

#### PARAMETERS

| Name    | optional | Descriptions                                                                            |
| ------- | -------- | --------------------------------------------------------------------------------------- |
| country | Yes      | Enter the country name (multile countries are seperated by comma) Example:India,Albania |
| mcc     | Yes      | Enter the mcc                                                                           |
| mnc     | Yes      | Enter the mnc                                                                           |

#### Example Request

```
curl -X GET \
  {domain}/api/v2/sms/locations/coveragelist \
    -H 'Authorization: Bearer 7160f04c05870ee8881xxxxxxxxxxxxx' \
    -H 'Accept: application/json' \
    -F country=India,Albania \
    -F mcc=404 \
    -F mnc=108
```

#### Example Response

```json
{
  "status": "OK",
  "data": {
    "current_page": 1,
    "data": [
      {
        "location": "India",
        "network": "Airtel",
        "mcc": "404",
        "mnc": "111",
        "charges": "0.0043",
        "effective_date": "2021-02-04 19:38:40",
        "serial": 1
      },
      {
        "location": "India",
        "network": "Vodafone",
        "mcc": "404",
        "mnc": "108",
        "charges": "0.0043",
        "effective_date": "2021-02-04 19:38:40",
        "serial": 2
      }
    ],
    "first_page_url": "{domain}/api/v2/sms/locations/coveragelist?page=1",
    "from": 1,
    "last_page": 1,
    "last_page_url": "{domain}/api/v2/sms/locations/coveragelist?page=1",
    "next_page_url": null,
    "path": "{domain}/api/v2/sms/locations/coveragelist",
    "per_page": 25,
    "prev_page_url": null,
    "to": 2,
    "total": 2
  }
}
```
