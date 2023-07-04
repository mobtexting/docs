# View Smart Link Visits

Access the particular Link Visits
#include "_include/endpoint.md"

#### GET

```
{endpoint}link/urls/{id}/visits
```

#### PARAMETERS

| Name | Optinal | Descriptions   |
| ---- | ------- | -------------- |
| id   |         | Smart Link id. |

#### Example Request

```
curl -X GET \
  '{endpoint}link/urls/{id}/visits' \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 5b02112fb7xxxxxxxxx'
```

Kindly replace the token with your respective access_token and other params.

#### Example Response

```json
{
    "status": "OK",
    "code": 200,
    "message": "Visits",
    "data": [
            {
                "id": "835b7433-0aaf-457c-88e7-7433b00d****",
                "user_id": "26",
                "link_id": "20",
                "client_ip": "127.0.0.1",
                "scheme": null,
                "host": null,
                "query_string": "",
                "user_agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_13_6) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/67.0.3396.99 Safari/537.36",
                "browser": "Chrome",
                "browser_version": "67.0.3396.99",
                "browser_lang": "en",
                "browser_engine": "Blink",
                "resolution": null,
                "platform": "Mac",
                "platform_version": "10.13.6",
                "platform_name": "MAC",
                "device_type": "desktop",
                "device_brand": "Apple",
                "device_model": "",
                "touch_enabled": "0",
                "latitude": "",
                "longitude": "",
                "country": "localhost",
                "country_code": "",
                "region": "",
                "city": "localhost",
                "zipcode": "",
                "timezone": "",
                "options": null,
                "created_at": "2022-10-31 10:07:27",
                "visit_id": "58a26f02-73e2-40ef-ab35-de427e9a6c6b",
                "token": "JFlCjw",
                "message_id": "JFlCjw",
                "mobile": "9019955***"
            },
        ],
       "links": {
        "first": "{endpoint}link/urls/21/visits?page=1",
        "last": "{endpoint}link/urls/21/visits?page=1",
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
                "url": "{endpoint}link/urls/21/visits?page=1",
                "label": "1",
                "active": true
            },
            {
                "url": null,
                "label": "Next &raquo;",
                "active": false
            }
        ],
        "path": "{endpoint}link/urls/21/visits",
        "per_page": 15,
        "to": 1,
        "total": 1
    }
}
```
