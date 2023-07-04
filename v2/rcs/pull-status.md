# PULL DELIVERY STATUS
#include "_include/endpoint.md"

#### GET

```
{endpoint}rcs/message/status?id=cdf829fd-5148-44bb-8433-xxxxx
```

#### ACCEPTED PARAMETERS

| Name     | Descriptions                         |
| -------- | ------------------------------------ |
| id       | Message Id we have given in response |
| mobile   | Mobile number with country code      |

you can pass any of the above params to get the dlr response.

#### Example Request

```curl
curl -X GET \
  '{endpoint}rcs/message/status?access_token=209eccd40e45b21xxxx&id=cdf829fd-5148-44bb-8433-xxxxx'
```

#### Example Response

```json
{
    "status": "200",
    "message": "OK",
    "data": [
        {
            "id": "cdf829fd-5148-44bb-8433-xxxxx",
            "channel": "rcs",
            "from": "700969ca-0cb2-11ec-XXXXX",
            "to": "918867135684",
            "credits": "1.0000",
            "created_at": "2021-09-07T00:07:50.000000Z",
            "foreign_id": "MsT356dI2hRzm9fTdBJeodbw",
            "status": "delivered",
            "delivered_at": "2021-09-07 11:07:55",
            "read_at": "2021-09-07T05:37:58.000000Z"
        }
    ]
}
```
