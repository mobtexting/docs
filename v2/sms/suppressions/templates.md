# View Template Blocklists

View all Blocklists
#include "_include/endpoint.md"

#### GET

```
{endpoint}sms/suppressions/templates
```

#### Example Request

```
curl -X GET \
  '{endpoint}sms/suppressions/templates' \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 7160f04c0587xxxxxxxxxxxxxxxx'
```

Kindly replace the token with your respective access_token and other params.

#### Example Response

```json
{
    "status": "OK",
    "code": 200,
    "message": "Block templates list",
    "data": [
        {
            "id": "2",
            "template_id": "12xxxxx",
            "status": 1,
        },
        ....
    ],
    "links": {
        "first": "{endpoint}sms/suppressions/templates?page=1",
        "last": "{endpoint}sms/suppressions/templates?page=1",
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
                "url": "{endpoint}sms/suppressions/templates?page=1",
                "label": "1",
                "active": true
            },
            {
                "url": null,
                "label": "Next &raquo;",
                "active": false
            }
        ],
        "path": "{endpoint}sms/suppressions/templates",
        "per_page": 15,
        "to": 3,
        "total": 3
    }
}
```

## Create Block Template

Create block template using POST method.
#include "_include/endpoint.md"

#### POST

```
{endpoint}sms/suppressions/templates
```

#### PARAMETERS

| Name        | optional | Descriptions                                  |
| ----------- | -------- | --------------------------------------------- |
| template_id | No       | Enter the template_id that you want to create |
| status      | Mixed    | 1 or 0                                        |

#### Example Request

```
curl -X POST\
  '{endpoint}sms/suppressions/templates' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer 7160f04c0587xxxxxxxxxxxxxxxx' \
  -H 'Content-Type: application/json' \
  -d '{
    "template_id": "12xxxxx",
    "status": "1"
}'
```

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Block template added successfully",
  "data": {
    "id": "2",
    "template_id": "12xxxxx",
    "status": 1
  }
}
```

## Edit Block Template

Edit block template using put method.
#include "_include/endpoint.md"

#### PUT

```
{endpoint}sms/suppressions/templates/{id}
```

Replace the {id} with the actual id of the receiver that you would like to Edit.

#### PARAMETERS

| Name        | optional | Descriptions                             |
| ----------- | -------- | ---------------------------------------- |
| template_id | No       | Enter the receiver that you want to edit |
| status      | Mixed    | 1 or 0                                   |

#### Example Request

```
curl -X PUT \
  '{endpoint}sms/suppressions/templates/2' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer 7160f04c0587xxxxxxxxxxxxxxxx' \
  -H 'Content-Type: application/json' \
  -d '{
    "template_id": "12xxxxx",
    "status": "1"
}'

```

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Block template updated successfully",
  "data": {
    "id": "2",
    "template_id": "12xxxxx",
    "status": 1
  }
}
```

## View Block Templates

View one created block template
#include "_include/endpoint.md"

#### GET

```
{endpoint}sms/suppressions/templates/{id}
```

#### Example Request

```
curl -X GET \
  '{endpoint}sms/suppressions/templates/2' \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 7160f04c0587xxxxxxxxxxxxxxxx'
```

Kindly replace the token with your respective access_token .

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Block template data",
  "data": {
    "id": 2,
    "template_id": "12xxxxx",
    "status": 1
  }
}
```

## Import Block Templates

Import block templates by uploading a file
#include "_include/endpoint.md"

#### POST

```
{endpoint}/sms/suppressions/templates/import
```

#### Example Request

```
curl -X POST\
  '{endpoint}sms/suppressions/templates/import' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer 7160f04c0587xxxxxxxxxxxxxxxx' \
  -H 'Content-Type: application/form-data' \
  -F 'file=@"yourfilepath/templates.xlsx"'
```

#### PARAMETERS

| Name     | Description                                              | Limits | Required |
| -------- | -------------------------------------------------------- | ------ | -------- |
| url      | Public url of the receiver file. Either HTTP/HTTPS link. | 100 MB | Yes      |
| caption  | some text for reciver caption                            | N/A    | No       |
| filename | Receiver file name                                       | N/A    | No       |

#### EXAMPLE RESPONSE

```json
{
  "status": "OK",
  "message": "Blocked templates accepted for import"
}
```

## Delete Block Template

Delete block template using delete method
#include "_include/endpoint.md"

#### DELETE

```
{endpoint}sms/suppressions/templates/{id}
```

Replace the {id} with the actual id of the block template's id that you would like to delete.

#### Example Request

```
curl -X DELETE \
  '{endpoint}sms/suppressions/templates/2' \
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

## Cleanup Templates

Delete all templates at once
#include "_include/endpoint.md"

#### POST

```
{endpoint}sms/suppressions/templates
```

#### Example Request

```
curl -X DELETE \
  '{endpoint}sms/suppressions/templates' \
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
