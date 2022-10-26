## Delete Template

Delete template using post method under your account

#### API Endpoint

```
{domain}/api/{version}/
```

#### GET

```
{endpoint}sms/templates/{id}
```

Replace the {id} with the actual id of the template that you would like to delete.

#### Example Request

```
curl -X GET \
  {endpoint}sms/templates/b10a9c3c-33bd-42f4-9e68-31c2216e5bcf \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 5b02112fb7xxxxxxxxx'
```

#### Example Response

```json
{
  "status": "OK",
  "message": "Template deleted successfully"
}
```
