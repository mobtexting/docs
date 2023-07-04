# OPTOUT

RCS campaigns are targeted to those customers who are registered subscribers to your RCS
services. You can block the customer's number using our optout feature. Once the customer's number is blocked, meanwhile if you try to trigger RCS to the customer's number then our system will automatically reject the RCS triggered and the customer will not recieve the RCS.
#include "_include/endpoint.md"

#### POST

```
{endpoint}rcs/optout
```

#### MANDATORY PARAMETERS

| Name   | Descriptions                             |
| ------ | ---------------------------------------- |
| number | Receiver numbers that you want to block. |

#### Example Request

```
curl -X POST \
  '{endpoint}rcs/optout'
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
{endpoint}rcs/optout/{number}
```

Replace the {number} with the actual number of the RCS that you would like to delete.

#### Example Request

```
curl -X DELETE \
  {endpoint}rcs/optout/91873650xxxx \
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
