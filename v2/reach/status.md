# OUTBOUND CALL Status

This Voice API supports the following:

#### HTTP Methods

It will support `GET` request.

```
{domain}/api/{version}/outgoing/callstatus
```

#### MANDATORY PARAMETERS

| Name   | Descriptions                                    |
| ------ | ----------------------------------------------- |
| id     | ID of the call which initiated through api (or) |
| cid    | Your custom id (or)                             |
| date   | valid date (or)                                 |
| mobile | valid mobile number with coutry code            |

#### Example Request

#code "{version}/_code/reach/callstatus.json"

#### Example Response

```json

{
    "status": 200,
    "message": "OK",
    "data": [
        {
            "id": "8456bf26-1b6e-4ac1-adb9-2768258f71d0",
            "channel": "outgoing",
            "from": "3589100xxxx",
            "to": "91761936xxxx",
            "created_at": "2024-07-10 08:27:14",
            "foreign_id": "",
            "status": "ANSWER",
            "start_at": "2024-07-10 08:27:26",
            "end_at": "2024-07-10 08:27:29",
            "dtmf": ""
        }
    ]
}
```
