# Verify HLR of mobile numbers

Verify HLR of mubile numbers using post method under your account
#include "_include/endpoint.md"

#### POST

```
{endpoint}lookup/verify
```

#### PARAMETERS

| Name | optional | Descriptions                              |
| ---- | -------- | ----------------------------------------- |
| to   | No       | Enter the mobile number with country code |

#### Example Request

```

curl -X POST \
  {endpoint}lookup/verify \
  -H 'Authorization: Bearer 5b02112fb7xxxxxxxxxxxxxxxx' \
  -F to=9194928xxxxx \
```

#### Example Response

```json
{
  "status": 200,
  "message": "Verified Successfully",
  "data": [
    {
      "phone": "919492xxxxx",
      "mcc_mnc": "40xxx",
      "imsi": "404738104xxxxxx",
      "serving_msc": "919xxx",
      "status": "SUCCESS",
      "original_network": {
        "network_prefix": "94928",
        "country_prefix": "91",
        "network_name": "BSNL",
        "country_name": "India",
        "state_name": "Andhra Pradesh"
      },
      "ported": false,
      "ported_network": {
        "ported_network_prefix": null,
        "ported_country_prefix": null,
        "ported_network_name": null,
        "ported_country_name": null,
        "ported_state_name": null
      },
      "roaming": false,
      "roaming_network": {
        "roaming_network_prefix": null,
        "roaming_country_prefix": null,
        "roaming_network_name": null,
        "roaming_country_name": null,
        "roaming_state_name": null
      }
    }
  ]
}
```
