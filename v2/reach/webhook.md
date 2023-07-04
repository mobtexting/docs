# WEBHOOK (OR) CALLBACK URL

The WEBHOOK Push API sends the report of the Click2Call to the client’s URL in `POST` method.

To request such reports, you need to create webhook URL first in Webhooks section. Then pass that particular `webhook_id` you created earlier while making a call through API.

We will send a `POST` with json format to your webhook URL with below parameters

## Example Parameter

| Name          | Description                                   |
| ------------- | --------------------------------------------- |
| webhook_id    | ID of the webhook created in Webhooks section |
| bridge        | DID number for call initiation                |
| from          | From number for call initiation               |
| to            | Phone number to which call has connected      |
| start_at      | Call Start time in `YYYY-MM-DD h:i:s` format  |
| end_at        | Call end time in `YYYY-MM-DD h:i:s` format    |
| duration      | Duration of the call in seconds (first call)  |
| mid           | message id of the campaign                    |
| flow_id       | Flowid for the campaign used                  |
| status        | Call Status                                   |
| source        | OBD                                           |
| recording_url | Recording Url if call got recorded            |

## Example Webhook Url

```
  https://www.domain.com/ack/receive
```

WebookID value can be provided while doing the campaign from panel.

If you are doing OBD using api, we need to send `webhook_id` paramater to send id of webhook.

- The response codes other than 200 or 202 are not taken into consideration and requests for such response codes are considered as failed.

- The method used for sending the callback report onto the client’s URL is `POST`.

## Example Request to Client's URL

```
curl -X POST \
  https://www.domain.com/ack/receive \
  -H 'content-type: application/json' \
  -d '{
      "bridge": 91806828XXXX,
      "from": 91891952XXXX,
      "to": 91886713XXXX,
      "source": "OBD",
      "mid": "1234-1333-XXXXX",
      "flow_id": 123,
      "start_at": "2021-04-09 16:27:39",
      "end_at": "2021-04-09 16:27:55",
      "duration": "23",
      "status": "ANSWER",
      "recording_url": "https://youraudiofilelocation/",
}'
```
