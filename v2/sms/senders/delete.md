## Delete Sender-id

Delete sender-id using post method under your account

#### API Endpoint

```
{domain}/api/{version}/
```

#### DELETE

```
{endpoint}sms/senders/{id}
```

Replace the {id} with the actual id of the sender that you would like to delete.

#### Example Request

```
curl -X DELETE \
  {endpoint}sms/senders/b7e42a8e-b6df-4a5e-ac42-xxxxxxxxxxxx \
  -H 'Authorization: Bearer 5b02112fb7xxxxxxxxxxxxxxx' \
```

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Sender deleted successfully"
}
```
