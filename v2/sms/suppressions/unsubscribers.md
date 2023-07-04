# View Unsubscribers

View all created unsubscribers
#include "_include/endpoint.md"

#### GET

```
{endpoint}sms/suppressions/unsubscribers
```

#### Example Request

```
curl -X GET \
  '{endpoint}sms/suppressions/unsubscribers' \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 7160f04c0587xxxxxxxxxxxxxxxx'
```

Kindly replace the token with your respective access_token and other params.

#### Example Response

```json
{
    "status": "OK",
    "code": 200,
    "message": "Unsubscribers list",
    "data": [
        {
            "id": "0e3fdaad-2b46-4dcf-8b14-xxxxxxxxxxxx",
            "iso": "IN",
            "receiver": "9198xxxxxxxx",
            "type": "xxxxxxx",
            "value": "xxxxx",
            "created_at": "2023-04-11T12:53:29.000000Z"
        },
        ....
    ],
    "links": {
        "first": "{endpoint}sms/suppressions/unsubscribers?page=1",
        "last": "{endpoint}sms/suppressions/unsubscribers?page=1",
        "prev": null,
        "next": null
    },
    "meta": {
        "current_page": 1,
        "from": 1,
        "last_page": 1,
        "links": [
            {
                "url": null,
                "label": "&laquo; Previous",
                "active": false
            },
            {
                "url": "{endpoint}sms/suppressions/unsubscribers?page=1",
                "label": "1",
                "active": true
            },
            {
                "url": null,
                "label": "Next &raquo;",
                "active": false
            }
        ],
        "path": "{endpoint}sms/suppressions/unsubscribers",
        "per_page": 15,
        "to": 6,
        "total": 6
    }
}
```

## Create Unsubscriber

Create receiver using POST method.
#include "_include/endpoint.md"

#### POST

```
{endpoint}sms/suppressions/unsubscribers
```

#### PARAMETERS

| Name     | optional | Descriptions                                          |
| -------- | -------- | ----------------------------------------------------- |
| receiver | No       | Enter the receiver that you want to create            |
| type     | Mixed    | Type of the receiver like (tag, product, sender, all) |
| value    | Mixed    | Input the value of the type                           |

#### Example Request

```
curl -X POST\
  '{endpoint}sms/suppressions/unsubscribers' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer 7160f04c0587xxxxxxxxxxxxxxxx' \
  -H 'Content-Type: application/json' \
  -d '{
    "receiver": "98xxxxxxxx",
    "type": "xxxxxxx",
    "value": "xxxxx"
}'
```

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Receiver added successfully",
  "data": {
    "id": "848c22a0-6969-455a-b5dc-4b119016b55b",
    "iso": "IN",
    "receiver": "919876543210",
    "type": "tag",
    "value": "promo",
    "created_at": "2023-04-11T12:50:17.000000Z"
  }
}
```

## Edit Unsubscriber

Edit receiver using put method.
#include "_include/endpoint.md"

#### PUT

```
{endpoint}sms/suppressions/unsubscribers/{id}
```

Replace the {id} with the actual id of the receiver that you would like to Edit.

#### PARAMETERS

| Name     | optional | Descriptions                                          |
| -------- | -------- | ----------------------------------------------------- |
| receiver | No       | Enter the receiver that you want to edit              |
| type     | Mixed    | Type of the receiver like (tag, product, sender, all) |
| value    | Mixed    | Input the value of the type                           |

#### Example Request

```
curl -X PUT \
  '{endpoint}sms/suppressions/unsubscribers/848c22a0-6969-455a-b5dc-4b119016b55b' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer 7160f04c0587xxxxxxxxxxxxxxxx' \
  -H 'Content-Type: application/json' \
  -d '{
    "receiver": "98xxxxxxxx",
    "type": "xxxxxxx",
    "value": "xxxxx"
}'

```

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Receiver update successfully",
  "data": {
    "id": "848c22a0-6969-455a-b5dc-4b119016b55b",
    "iso": "IN",
    "receiver": "919876543210",
    "type": "tag",
    "value": "promo1",
    "created_at": "2023-04-11T12:50:17.000000Z"
  }
}
```

## View Single Unsubscriber

View one created receiver
#include "_include/endpoint.md"

#### GET

```
{endpoint}sms/suppressions/unsubscribers/{id}
```

#### Example Request

```
curl -X GET \
  '{endpoint}sms/suppressions/unsubscribers/0e3fdaad-2b46-4dcf-8b14-aafffbxxxxxx' \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 7160f04c0587xxxxxxxxxxxxxxxx'
```

Kindly replace the token with your respective access_token .

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Unsubscribers data",
  "data": {
    "id": "0e3fdaad-2b46-4dcf-8b14-xxxxxxxxxxxx",
    "iso": "IN",
    "receiver": "9198xxxxxxxx",
    "type": "xxxxxxx",
    "value": "xxxxxx",
    "created_at": "2023-04-11T12:53:29.000000Z"
  }
}
```

## Import Unsubscriber

Import receiver by uploading a file
#include "_include/endpoint.md"

#### POST

```
{endpoint}/sms/suppressions/unsubscribers/import
```

#### Example Request

```
curl -X POST\
  '{endpoint}sms/suppressions/unsubscribers/import' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer 7160f04c0587xxxxxxxxxxxxxxxx' \
  -H 'Content-Type: application/form-data' \
  -F 'file=@"yourfilepath/receiver.xlsx"'
```

#### PARAMETERS

```
| Name     | Description                                                  | Limits | Required |
| -------- | ------------------------------------------------------------ | ------ | -------- |
| file     | Receiver number file. (Supported filetype: txt,csv,xls,xlsx) | 100 MB | Yes      |
```

#### EXAMPLE RESPONSE

```json
{
  "status": "OK",
  "message": "Receivers accepted for import"
}
```

## Delete Unsubscriber

Delete receiver using delete method
#include "_include/endpoint.md"

#### DELETE

```
{endpoint}sms/suppressions/unsubscribers/{id}
```

Replace the {id} with the actual id of the receiver that you would like to delete.

#### Example Request

```
curl -X DELETE \
  '{endpoint}sms/suppressions/unsubscribers/0e3fdaad-2b46-4dcf-8b14-aafffbxxxxxx' \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 7160f04c0587xxxxxxxxxxxxxxxx'
```

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Deleted Successfully",
  "data": []
}
```

## Cleanup Unsubscriber

Delete all receiver at once
#include "_include/endpoint.md"

#### POST

```
{endpoint}sms/suppressions/unsubscribers
```

#### Example Request

```
curl -X DELETE \
  '{endpoint}sms/suppressions/unsubscribers' \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 7160f04c0587xxxxxxxxxxxxxxxx'
```

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Deleted Successfully",
  "data": []
}
```
