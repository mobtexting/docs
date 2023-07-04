# Adding Credits to Customers
#include "_include/endpoint.md"

#### POST

```
{endpoint}finance/balance
```

You can add the credits to your customers using this api.

`access_token` of main reseller(admin) account should use for adding credits to your customers

#### MANDATORY PARAMETERS

| Name     | Descriptions                                |
| -------- | ------------------------------------------- |
| username | Username of account you want to add credits |
| credits  | Number of credits                           |
| service  | Service in which need to add credits.       |

#### OPTIONAL PARAMETERS

| Name     | Descriptions             |
| -------- | ------------------------ |
| notes    | Reference notes          |
| order_id | Reference orderid if any |

#### Example Request

```curl
  curl -X POST \
  '{endpoint}finance/balance' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer 38e896f55670311982434e929559bxxxx' \
  -H 'content-type: application/x-www-form-urlencoded' \
  -d 'service=MKT&username=laxmanxxx&credits=100&notes=test%20from%20api'
```

#### Example Response

```json
{
  "status": "OK",
  "message": "Funds updated successfully.."
}
```
