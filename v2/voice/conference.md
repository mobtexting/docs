# List Conferences
#include "_include/endpoint.md"

#### HTTP Methods

`GET` method used to list all conferences.

#### GET

```
{domain}/api/{version}/voice/conferences?access_token=234dexopwxxxxxx
```

#### Example Response

```json
{
  "status": "OK",
  "data": {
    "current_page": 1,
    "data": [
      {
        "name": "Conference Request",
        "number": "9108012788",
        "moderator_pin": "157118",
        "participant_pin": "611159",
        "max_people": "3",
        "start_date": "2019-07-01 13:14:39",
        "end_date": "2019-07-01 13:14:39"
      },
      {
        "name": "Lakshman",
        "number": "9108012788",
        "moderator_pin": "185691",
        "participant_pin": "313616",
        "max_people": "5",
        "start_date": "2019-08-20 18:09:30",
        "end_date": "2019-08-30 18:09:30"
      }
    ],
    "first_page_url": "{endpoint}voice/conferences?page=1",
    "from": 1,
    "last_page": 1,
    "last_page_url": "{endpoint}voice/conferences?page=1",
    "next_page_url": null,
    "path": "{endpoint}voice/conferences",
    "per_page": 15,
    "prev_page_url": null,
    "to": 3,
    "total": 3
  }
}
```

# Create Conference

This Voice API supports the following:

#### HTTP Methods

It will support only POST requests.

#### POST

```
{domain}/api/{version}voice/conference/create?access_token=234dexopwxxxxxx
```

#### MANDATORY PARAMETERS

| Name         | Descriptions              |
| ------------ | ------------------------- |
| access_token | Access token your account |

#### OPTIONAL PARAMETERS

| Name       | Descriptions                                                             |
| ---------- | ------------------------------------------------------------------------ |
| max_people | Number of participants in conference , should be min 2 and max 10 people |
| validity   | Validity of conference (in days), should be min 7 and max 365            |
| name       | Name of the conference                                                   |

#### Example Request

```
curl -X POST \
  '{domain}/api/{version}/voice/conference/create?access_token=b7a3d012c96172dfaxxxxxxx' \
  -H 'cache-control: no-cache' \
  -F name=Lakshman \
  -F max_people=5 \
  -F validity=10
```

#### Example Response

```json
{
  "status": "OK",
  "message": "Success",
  "data": {
    "moderator_pin": "185691",
    "participant_pin": "313616",
    "max_people": "5",
    "start_date": "2019-08-20 18:09:30",
    "end_date": "2019-08-30 18:09:30"
  }
}
```
