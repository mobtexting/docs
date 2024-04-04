# Generate Optin/Optout Link

Any number can be opted in/out based on the selected Service, Sender and/or Tags by dynamic link creation that provides granularity on the optout/optin feature.

## Optout Link

#### POST

```
{endpoint}sms/suppressions/optout/link
```

#### PARAMETERS

| Name    | optional | Descriptions                                                                            |
| ------- | -------- | --------------------------------------------------------------------------------------- |
| sender  | Yes      | Enter a valid sender                                                                    |
| tags    | Yes      | Provide max. of 2 tags(array)                                                           |
| service | Yes      | The short code of the service name. ex: (MKT) [full list](/docs/{version}/sms/products) |

### Example Request

```
curl -X POST \
  '{endpoint}api/v2/sms/suppressions/optout/link' \
  -H 'authorization: Bearer 5b02112fb7xxxxxxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "sender": "654321",
    "tag" : ["tag1","tag2"],
    "service": "T"
}'
```

### Example Response

```
{
    "status": "OK",
    "message": "Optout link generated Successfully.",
    "data": "https://tx3.in/mo/[#optout#]?sender=654321&tag=tag1,tag2&service=T"
}
```

## Optin Link

#### POST

```
{endpoint}sms/suppressions/optin/link
```

#### PARAMETERS

| Name    | optional | Descriptions                                                                            |
| ------- | -------- | --------------------------------------------------------------------------------------- |
| sender  | Yes      | Enter a valid sender                                                                    |
| tags    | Yes      | Provide max. of 2 tags(array)                                                           |
| service | Yes      | The short code of the service name. ex: (MKT) [full list](/docs/{version}/sms/products) |

### Example Request

```
curl -X POST \
  '{endpoint}api/v2/sms/suppressions/optin/link' \
  -H 'authorization: Bearer 5b02112fb7xxxxxxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "sender": "654321",
    "tag" : ["tag1","tag2"],
    "service": "T"
}'
```

### Example Response

```
{
    "status": "OK",
    "message": "Optin link generated Successfully.",
    "data": "https://tx3.in/mi/[#optin#]?sender=654321&tag=tag1,tag2&service=T"
}
```
