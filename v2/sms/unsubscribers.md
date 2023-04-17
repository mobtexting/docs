## View Unsubscribers

View all created unsubscribers

#### API Endpoint

```
{domain}/api/{version}/
```

#### GET

```
{endpoint}sms/unsubscribers
```

#### Example Request

```
curl -X GET \
  '{endpoint}sms/unsubscribers' \
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
        "first": "{endpoint}sms/unsubscribers?page=1",
        "last": "{endpoint}sms/unsubscribers?page=1",
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
                "url": "{endpoint}sms/unsubscribers?page=1",
                "label": "1",
                "active": true
            },
            {
                "url": null,
                "label": "Next &raquo;",
                "active": false
            }
        ],
        "path": "{endpoint}sms/unsubscribers",
        "per_page": 15,
        "to": 6,
        "total": 6
    }
}
```

## Create Unsubscriber

Create receiver using POST method.

#### API Endpoint

```
{domain}/api/{version}/
```

#### POST

```
{endpoint}sms/unsubscribers
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
  '{endpoint}sms/unsubscribers' \
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

#### API Endpoint

```
{domain}/api/{version}/
```

#### PUT

```
{endpoint}sms/unsubscribers/{id}
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
  '{endpoint}sms/unsubscribers/848c22a0-6969-455a-b5dc-4b119016b55b' \
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

#### API Endpoint

```
{domain}/api/{version}/
```

#### GET

```
{endpoint}sms/unsubscribers/{id}
```

#### Example Request

```
curl -X GET \
  '{endpoint}sms/unsubscribers/0e3fdaad-2b46-4dcf-8b14-aafffbxxxxxx' \
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

#### API Endpoint

```
{domain}/api/{version}/
```

#### POST

```
{endpoint}/sms/unsubscribers/import
```

#### Example Request

```
curl -X POST\
  '{endpoint}sms/unsubscribers/import' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer 7160f04c0587xxxxxxxxxxxxxxxx' \
  -H 'Content-Type: application/form-data' \
  -F 'file=@"yourfilepath/receiver.xlsx"'
```

#### PARAMETERS

```
| Name     | Description                                              | Limits | Required |
| -------- | -------------------------------------------------------- | ------ | -------- |
| url      | Public url of the receiver file. Either HTTP/HTTPS link. | 100 MB | Yes      |
| caption  | some text for reciver caption                            | N/A    | No       |
| filename | Receiver file name                                       | N/A    | No       |
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

#### API Endpoint

```
{domain}/api/{version}/
```

#### DELETE

```
{endpoint}sms/unsubscribers/{id}
```

Replace the {id} with the actual id of the receiver that you would like to delete.

#### Example Request

```
curl -X DELETE \
  '{endpoint}sms/unsubscribers/0e3fdaad-2b46-4dcf-8b14-aafffbxxxxxx' \
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

#### API Endpoint

```
{domain}/api/{version}/
```

#### POST

```
{endpoint}sms/unsubscribers
```

#### Example Request

```
curl -X DELETE \
  '{endpoint}sms/unsubscribers' \
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
