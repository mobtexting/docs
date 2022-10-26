## OPTOUT

Whatsapp campaigns are targeted to those customers who are registered subscribers to your Whatsapp
services. You can block the customer's number using our optout feature. Once the customer's number is blocked, meanwhile if you try to trigger Whatsapp to the customer's number then our system will automatically reject the Whatsapp triggered and the customer will not recieve the Whatsapp.

#### API Endpoint

```
{domain}/api/{version}/
```

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
  '{endpoint}rcs/optout'
   -H 'Content-Type: application/x-www-form-urlencoded' \
   -H 'Accept: application/json' \
   -H 'Authorization: Bearer 38e896f55670311982434e929559xxxx'
   -F number=9174114xxxxx
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
