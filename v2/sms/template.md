# Template SMS API

Now you can send message using template id of the predefined template created in your account.

Example template as follows:

Dear @{{1}}, Thanks for registering with us. Your details as follows @{{2}}, @{{3}}.

While sending sms we need to pass the variables in the api url then content will be replaced automatically in the template as below.

Ex: variables=["laxman","laxman46XXXXXX@gmail.com","91891952XXXX"]

Note: Variables in array must be in order created in template. Even blank values also will replace if we specify in variables array.

Dear laxman, Thanks for regisitering with us. Your details as follows laxman46XXXX@gmail.com, 91891952XXXX.

## Send SMS

#### API Endpoint

```
{domain}/api/{version}/
```

#### POST

```
{endpoint}sms/template
```

You can send sms using `POST` method content in body.

All params in send sms will support in JSON also.

#### BODY

```json
{
  "service": "MKT",
  "template_id": "008ed156-61b1-4582-aa8e-0f4068776c2e",
  "variables": ["Laxman", "", "New"],
  "to": ["91891952xxxxx", "918919xxxxxx"]
}
```

#### MANDATORY PARAMETERS

| Name        | Descriptions                                                                                           |
| ----------- | ------------------------------------------------------------------------------------------------------ |
| to          | Phone number to send with country prefix. (multiple numbers need to be sent as array.)                 |
| template_id | Id of the template                                                                                     |
| service     | The short code of the service name. ex: (MKT) [full list](/docs/{version}/#content-products)           |
| variables   | Varible values for replacing in template content (need to send as array) Ex:["name","891919XXX","new"] |

#### OPTIONAL PARAMETERS

| Name       | Descriptions                                                                                                                                                            |
| ---------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| name       | Name of the campaign                                                                                                                                                    |
| webhook_id | The `id` of the webhook created in Webhook Section for which the SMS response to be sent after delivery report from operator. [read more](/docs/{version}/sms-push-dlr) |
| time       | Schedule time (in format i.e,yyyy-mm-dd hh:mm:ss) at which the SMS has to be sent.                                                                                      |
| type       | The SMS to be sent is Unicode, Normal or Auto detect. (value "U", "N" or "A")                                                                                           |
| flash      | This parameter can be used to send flash sms via API ( Values 1 or 0.)                                                                                                  |
| custom     | Any customised parameters can be passed using this parameter                                                                                                            |
| port       | Port number to which SMS has to be sent                                                                                                                                 |

#### Example Request

```
  curl -X POST \
    '{endpoint}sms/template \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 38e896f55670311982434e929559bxxxx' \
    -H 'content-type: application/x-www-form-urlencoded' \
    -d '{
      "service": "MKT",
      "template_id": "008ed156-61b1-4582-aa8e-0f4068776c2e",
      "variables" : ["Laxman", "myname@gmail.com",  "New"],
      "to": ["918919525224","8919555555"]
    }'
```

#### Example Response

```json
{
  "status": 200,
  "message": "2 numbers accepted for delivery.",
  "data": [
    {
      "id": "06a1880f-2396-42e7-a141-06fa3a9b23bf:1",
      "mobile": "9189195xxxx",
      "status": "AWAITING-DLR",
      "units": 1,
      "length": 152,
      "charges": "1.0000",
      "customid": "",
      "iso_code": null,
      "submitted_at": "2020-09-24 15:42:56"
    },
    {
      "id": "06a1880f-2396-42e7-a141-06fa3a9b23bf:2",
      "mobile": "9189195xxxx",
      "status": "AWAITING-DLR",
      "units": 1,
      "length": 152,
      "charges": "1.0000",
      "customid": null,
      "iso_code": null,
      "submitted_at": "2020-09-24 15:42:56"
    }
  ]
}
```
