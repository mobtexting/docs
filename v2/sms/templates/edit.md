# Edit Templates

Edit template using put method under your account
#include "_include/endpoint.md"

#### PUT

```
{endpoint}sms/templates/{id}
```

Replace the {id} with the actual id of the template that you would like to Edit.

#### PARAMETERS

| Name        | Optinal | Descriptions                                                     |
| ----------- | ------- | ---------------------------------------------------------------- |
| name        | No      | Input the name of the template that you would like to refer with |
| body        | No      | Input the body of the sms(template)                              |
| template_id | Mixed   | DLT Template id (required for india)                             |
| type        | Mixed   | Type of the template like (P, T, SI, SE)(required for india)     |
| is_english  | No      | Input the is_english (0, 1)

#### Example Request
#include "{version}/_samples/sms/templates/edit.md"

#### Example Response

```json
{
    "status": "OK",
    "code": 200,
    "message": "Template Update Successfully",
    "data": {
        "id": "b23769e6-019f-48f4-aae9-ec00a5xxxxxx",
        "sender_id": "015c2f82-1352-4d19-9f8f-b8449xxxxxx",
        "template_id": "110716152128335xxxx",
        "template_type": "Transactional",
        "sender": "SENDER",
        "name": "hind-number",
        "alias": "hind-number",
        "body": "Your Verification code is:@{{1}} is code @{{2}}",
        "content": null,
        "body_length": 53,
        "match_count": 0,
        "percentage": 0,
        "is_complete": 0,
        "is_english": 1,
        "status": 1,
        "created_at": "2022-11-16T04:41:32.000000Z",
        "updated_at": "2022-11-16T04:56:11.000000Z"
    }
}
```
