## Create Templates

Create templates using post method under your account

#### API Endpoint

```
{domain}/api/{version}/
```

#### POST

```
{endpoint}sms/templates
```

#### PARAMETERS

| Name        | Optional | Descriptions                                                     |
| ----------- | -------- | ---------------------------------------------------------------- |
| sender      | No       | Enter the approved sender-id under your account                  |
| name        | No       | Input the name of the template that you would like to refer with |
| body        | No       | Input the body of the sms(template)                              |
| template_id | Mixed    | DLT Template id (required for india)                             |
| type        | Mixed    | Type of the template like (P, T, SI, SE)(required for india)     |

#### Template types

| Template type | Description      |
| ------------- | ---------------- |
| T             | Transactional    |
| P             | Promotional      |
| SI            | Service Explicit |
| SE            | Service Implicit |

#### Example Request

```
curl -X POST \
  {endpoint}sms/templates \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 5b02112fb7xxxxxxxxx'
    -H 'Content-Type: application/x-www-form-urlencoded' \
    -d sender=TXTsms \
    -d name=test1 \
    -d 'body=testing sms 1'
```

#### Example Response

```json
{
    "status": "OK",
    "code": 200,
    "message": "Template saved successfully",
    "data": {
        "body": "Your Verification codes",
        "sender_id": "13e35ad0-2455-4a42-87bd-8709638XXXXX",
        "sender": "satis1",
        "status": 1,
        "body_length": 23,
        "template_type": "T",
        "is_english": 1,
        "name": "satis1",
        "created_at": "2022-10-06T18:37:22.000000Z",
        "template_id": "123456787",
        "id": "efe3ad4a-6c54-4e98-95c6-960bd22XXXXX",
        "user_id": XXXXX,
        "updated_at": "2022-10-06T18:37:22.000000Z"
    }
}
```
