# Click2Call/Number Masking

#include "_include/endpoint.md"

#### POST

```
{endpoint}voice/c2c
```

#### MANDATORY PARAMETERS

| Name   | Descriptions                                                           |
| ------ | ---------------------------------------------------------------------- |
| bridge | DID number for call initiation                                         |
| from   | Number To whom call will connect first with CountryCode                |
| to     | Phone number with Country Code / IVR flow to which call has to connect |

#### OPTIONAL PARAMETERS

| Name       | Descriptions                                             |
| ---------- | -------------------------------------------------------- |
| mid        | Message id for reference                                 |
| webhook_id | Webhook ID for pushing the call data once call completed, Instead of passing webhook_id everytime in the payload, refer to [create subscription](/docs/{version}/subscriptions#content-create-subscription) |
| variables  | `Array` of the variables which can be used in flow       |
| record     | Record this conversation (default `0`). allowed: 0 or 1  |
| duration   | Limit the call duration in minutes. default (none)       |
| attempts   | No of redial attempts on unanswered calls. default 2. Max 2 |

#### Example C2C Using to as Mobile Number

#code "{version}/_code/voice/c2c_as_mobile.json"

#### Example C2C Using to as Flow ID

#code "{version}/_code/voice/c2c_as_flowid.json"

#### Example Response

```json
{
  "status": 200,
  "message": "Call initiated successfully"
}
```

@if (!config('service.unified'))

#### Example C2C with to as Flow ID & Variables

```
curl -X POST '{endpoint}voice/c2c' \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 38e896f55670311982434e929559bxxxx' \
    -H 'Content-Type: application/json' \
    -d '{
    "bridge":"91806828XXXX",
    "from":"918867135XXXX",
    "to":"flow:220",
    "variables[Name]":"YourName",
    "variables[otp]":"12344",
    "record":"1"
}'
```

- Here `flow_id` `220` is the Ivr Journey ID created in Engage > Studio Section

  The journey created should have a play widget with text to speech containing variables as follows:

  `Hello {Name}, your otp for login is {otp}`

  The above message contains two variables, this varaible values will replace from the API parameters when customer answers the click2call

#### Example Response

```json
{
  "status": 200,
  "message": "Call initiated successfully"
}
```

@endif

## Callback URL with Webhook ID

The WEBHOOK Push API sends the report of the Click2Call to the client’s URL in `POST` method.

To request such reports, you need to create webhook URL first in Webhooks section. Then pass that particular `webhook_id` you created earlier while making a call through API.

We will send a `POST` with json format to your webhook URL with below parameters

#### CALLBACK VARIABLES

Callback is a functionality to get notified through an API call when a call is completed. One needs to follow below steps to achieve valid callback

| Name          | Descriptions                                         |
| ------------- | ---------------------------------------------------- |
| webhook_id    | ID of the webhook created in Webhooks section        |
| bridge        | DID number for call initiation                       |
| from          | To whom call will connect first                      |
| to            | Phone number / IVR flow to which call has to connect |
| source        | C2C (click2Call)                                     |
| start_at      | Call Start time in `YYYY-MM-DD h:i:s` format         |
| end_at        | Call end time in `YYYY-MM-DD h:i:s` format           |
| date          | Current time in `YYYY-MM-DD h:i:s` format            |
| unixtime      | Current time in `unixtime` format                    |
| duration      | Duration of the call in seconds (first call)         |
| billing       | Duration of the call in seconds (second call)        |
| status        | Call Status                                          |
| status1       | Call Status of first call                            |
| status2       | Call Status of second call                           |
| recording_url | Recording Url if call got recorded                   |
| hangup_by     | Call Hangup By either agent or caller                |

- The response codes other than 200 or 202 are not taken into consideration and requests for such response codes are considered as failed.
- The method used for sending the callback report onto the client’s URL is `POST`.

#### Example Request to Client's URL

```shell -X POST \
  https://www.domain.com/ack/receive \
  -H 'content-type: application/json' \
  -d '{
      "bridge": 91806828XXXX,
      "from": 91891952XXXX,
      "to": 91886713XXXX,
      "source": "C2C",
      "start_at": "2021-04-09 16:27:39",
      "end_at": "2021-04-09 16:27:55",
      "date": "2021-04-09 16:27:55",
      "unixtime": "1653455555",
      "duration": "23",
      "billing": "23",
      "status": "COMPLETED",
      "status1": "RECEIVED",
      "status2": "ANSWER",
      "recording_url": "https://youraudiofilelocation/",
      "hangup_by": "caller"
}'
```
