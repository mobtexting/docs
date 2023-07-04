# OPTOUT

Whatsapp campaigns are targeted to those customers who are registered subscribers to your Whatsapp
services. You can block the customer's number using our optout feature. Once the customer's number is blocked, meanwhile if you try to trigger Whatsapp to the customer's number then our system will automatically reject the Whatsapp triggered and the customer will not recieve the Whatsapp.
#include "_include/endpoint.md"

#### POST

```
{endpoint}whatsapp/optout
```

#### MANDATORY PARAMETERS

| Name   | Descriptions                             |
| ------ | ---------------------------------------- |
| number | Receiver numbers that you want to block. |

#### Example Request

```
curl -X POST \
  '{endpoint}whatsapp/optout'
   -H 'Content-Type: application/json' \
   -H 'Accept: application/json' \
   -H 'Authorization: Bearer 38e896f55670311982434e929559xxxx'
   -d '{
    "number":"9174114xxxxx"
}'
```

On triggering the above API the specified numbers will be added to your optout list.

#### Example Response

```json
{
  'status' => OK,
  'code' => 200,
  'message' => 'Number added to optout list',
  'data': {
        'receiver': '918736******',
        'iso': 'IN',
        'created_at': '2022-10-26T06:33:40.000000Z',
        'id': 71
    },
}
```
## Delete Number from optout list

Delete number using delete method under your optout list
#include "_include/endpoint.md"

#### DELETE

```
{endpoint}whatsapp/optout/{number}
```

Replace the {number} with the actual number of the whatsapp that you would like to delete.

#### Example Request

```
curl -X DELETE \
  {endpoint}whatsapp/optout/91873650xxxx \
  -H 'Authorization: Bearer 5b02112fb7xxxxxxxxxxxxxxx' \
```

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Deleted successfully",
  "data": []
}
```
