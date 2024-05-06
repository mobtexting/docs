# Create Templates

Create templates using post method under your account
#include "_include/endpoint.md"

#### POST

```
{endpoint}sms/templates
```

#### PARAMETERS

| Name        | Optional | Descriptions                                                     |
| ----------- | -------- | ---------------------------------------------------------------- |
| sender      | No       | Enter the approved sender-id under your account                  |
| name        | No       | Input the name of the template that you would like to refer with |
| body        | No       | Input the body of the sms template (It can include variables like @{{var1}} which should be `alphabetic` or `alphanumeric`)                          |
| template_id | Mixed    | DLT Template id (required for india)                             |
| type        | Mixed    | Type of the template like (P, T, SI, SE)(required for india)     |

#### Template types

| Template type | Description      |
| ------------- | ---------------- |
| T             | Transactional    |
| P             | Promotional      |
| SI            | Service Implicit |
| SE            | Service Explicit |

#### Example Request

#code "{version}/_code/sms/templates/create.json"

#### Example Response

```json
{
   "status":"OK",
   "code":200,
   "message":"Template Saved Successfully",
   "data":{
      "id":"329d5b16-ab52-4da3-9ba4-a9d99a3xxxxx",
      "sender_id":"b6a266e1-0290-4921-b54a-f4ed158xxxxx",
      "template_id":"1234567",
      "template_type": "Transactional",
      "sender":"Sen123",
      "name":"temp",
      "alias":"temp",
      "body":"This is verification @{{var1}} and @{{var2}}",
      "content":null,
      "body_length":42,
      "match_count":0,
      "percentage":0,
      "is_complete":0,
      "is_english":1,
      "status":1,
      "created_at":"2022-05-02T10:49:13.000000Z",
      "updated_at":"2022-05-02T10:49:13.000000Z"
   }
}
```
