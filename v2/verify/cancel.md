# Cancel Verify

Deletes an existing Verify request. You only need to supply the unique id that was returned upon creation.
#include "_include/endpoint.md"

#### GET

```
{endpoint}verify/cancel/{id}
```

#### MANDATORY PARAMETERS

| Name | Type   | Description                                                                                       |
| ---- | ------ | ------------------------------------------------------------------------------------------------- |
| id   | string | The Verify request to check. This is the `id` you received in the response to the Verify request. |

#### Example Request

```curl
curl -X GET \
  '{endpoint}verify/cancel/41379328-d3a7-4fcd-be90-d5237f911d76' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer 38e896f55670311982434e929559xxxx'
```

#### Example Response

```json
{
  "id": "41379328-d3a7-4fcd-be90-d5237f911d76",
  "status": "success"
}
```
