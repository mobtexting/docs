# SMS Api Using File

The SMS API supports the following:

#### HTTP Methods

`POST` - When you send a POST request with file containing mobile numbers of customers, We send SMS message you specify to all the numbers exist in file.

> Country code is mandatory to be included in the `to` paramenter for global messaging.

## Send SMS

#### API Endpoint

```
{domain}/api/{version}/
```

#### POST

```
{endpoint}sms/bulk
```

You can send sms using `POST` method only as uploading file will supporting in `POST`.

#### MANDATORY PARAMETERS

| Name    | Descriptions                                                                                                |
| ------- | ----------------------------------------------------------------------------------------------------------- |
| message | The content of the SMS                                                                                      |
| sender  | The registered and approved Sender-id                                                                       |
| service | The short code of the service name. ex: (MKT) [full list](/docs/{version}/#content-products)                |
| file    | Request body form-data you need to select file parameter and need to upload file containing mobile numbers. |

#### OPTIONAL PARAMETERS

| Name        | Descriptions                                                                                                                                                           |
| ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| webhook_id  | The `id` of the webhook created in Webhook Section for which the SMS response to be sent after delivery report from operator. read more](/docs/{version}/sms-push-dlr) |
| time        | Schedule time (in format i.e,yyyy-mm-dd hh:mm:ss) at which the SMS has to be sent.                                                                                     |
| type        | The SMS to be sent is Unicode, Normal or Auto detect. (value "U", "N" or "A")                                                                                          |
| flash       | This parameter can be used to send flash sms via API ( Values 1 or 0.)                                                                                                 |
| custom      | Any customised parameters can be passed using this parameter                                                                                                           |
| port        | Port number to which SMS has to be sent                                                                                                                                |
| column      | Mobile number column name same as in customize sms                                                                                                                     |
| entity_id   | Principal Entityid registered in DLT portal (applicable for indian routes only)                                                                                        |
| template_id | TemplateId registered in DLT portal (applicable for indian routes only)                                                                                                |

#### Example Request

```
curl -X POST \
  '{endpoint}sms/bulk' \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 38e896f55670311982434e929559bxxxx' \
    -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
    -d 'sender=TXTSMS' \
    -d 'to=917026267xxx' \
    -d 'service=MKT' \
    -d 'message=Your OTP is 123456'
    -F file=@filename.txt
```

#### Example Response

```json
{
  "status": 200,
  "message": "XXX numbers accepted for delivery.",
  "data": []
}
```
