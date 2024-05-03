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
| name        | Yes      | Input the name of the template that you would like to refer with |
| body        | Yes      | Input the body of the sms template (It can include variables like @{{var1}} which should be `alphabetic` or `alphanumeric`)                              |
| template_id | Mixed   | DLT Template id (required for india)                             |
| type        | Mixed   | Type of the template like (P, T, SI, SE)(required for india)     |
| is_english  | Yes     | Input the is_english (0, 1)

#### Example Request

#code "{version}/_code/sms/templates/edit.json"

#### Example Response

```json
{
    "status": "OK",
    "code": 200,
    "message": "Template Updated Successfully",
    "data": {
        "id": "a09c5d2c-d9bf-4f22-99c5-4592d0fxxxxx",
        "sender_id": "845f6e29-0320-4aad-9f62-90baf44xxxxx",
        "template_id": "342442343xxxx",
        "template_type": @if(config('service.unified')) "Global" @else "Transactional" @endif,
        "sender": "SENDER",
        "name": "temp12",
        "alias": "temp",
        "body": "Welcome to mobtexting family",
        "content": null,
        "body_length": 28,
        "match_count": 0,
        "percentage": 0,
        "is_complete": 0,
        "is_english": 1,
        "status": 1,
        "created_at": "2024-05-02T11:14:54.000000Z",
        "updated_at": "2024-05-02T12:24:28.000000Z"
    }
}
```
