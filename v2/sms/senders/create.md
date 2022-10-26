## Create Sender-ids

Create sender-ids using post method under your account

#### API Endpoint

```
{domain}/api/{version}/
```

#### POST

```
{endpoint}sms/senders
```

#### PARAMETERS

| Name         | optional | Descriptions                                                                                 |
| ------------ | -------- | -------------------------------------------------------------------------------------------- |
| name         | No       | Enter the sender-id that you want to create                                                  |
| country_code | No       | For which country this sender belongs to. 2 letters                                          |
| service      | No       | The short code of the service name. ex: (MKT) [full list](/docs/{version}/#content-products) |
| entity_id    | Mixed    | Input the entity id (required for india)                                                     |
| entity_name  | Mixed    | Company name whom this sender belongs to (required for india)                                |

#### Example Request

```
curl -X POST \
  {endpoint}sms/senders \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer 5b02112fb7xxxxxxxxxxxxxxxx' \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -d name=xxxxxx \
  -d service=xxxxxx \
  -d entity_name=xxxxx \
  -d entity_id=xxxxx \
  -d country_code=IN \
```

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Sender saved successfully",
  "id": "f66b983b-713a-4818-a691-2c684eb4eccd"
}
```
