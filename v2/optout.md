## OPTOUT 

Traditionally, SMS campaigns are targeted to those customers who are registered subscribers to your SMS
services. You can block the customer's number using our optout feature. Once the customer's number is blocked, meanwhile if you try to trigger Sms to the  customer's number then our system will automatically reject the Sms triggered and the customer will not recieve the sms.

#### POST/GET

```
{endpoint}optout?token=a19eb34810exxxxxxxxx&number=74114xxxxx,707856xxxx
```

####  MANDATORY PARAMETERS

| Name     | Descriptions |
|----------|--------------|
| token | Token that is generated under your account.|
| number | Mobile numbers that you want to block.|


#### Example Request

```
curl -X GET
  {domain}/api/v2/optout?access_token=a19eb34810exxxxxxxxx&number=74114xxxxx,707856xxxx
```

Kindly replace the token with your respective token and you can specify multiple mobile numbers by seperating it with ','(comma).
  
On triggering the above API the specified numbers will be added to your optout list.


#### Example Response

```json
{
  'status'  => 200, 
  'message' => 'Number added to optout list'
}
```