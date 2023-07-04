# Moengage SMS Integration

## Steps to configure a Custom Connector
To integrate Mobtexting as an SMS provider, perform the following steps:
1. On the MoEngage Dashboard, navigate to Settings > Channel > SMS & Connector and click SMS Connector Config tab.
2. In Custom Connecters, click CREATE.

| Field | Description              |
| ---------------| -------------------------------------|
| Connecter Name | Type the name to identify the custom connector.|
| Sender Name    | Type the senderid. |
3. Select POST method and give following api as a provider end point.

```
{domain}/api/v2/sms/moengage/send
```
4. Give headers as following below.

![alt text](/images/docs/plugins/moengage/headers.png)

Enter key and value pairs.
| Key | value              |
| ---------------| -------------------------------------|
| Accept         | application/json|
| Authorization  | Bearer 7160f04c05870ee************** |
| Content-Type   | application/x-www-form-urlencoded    |

5. Choose body type as form to pass send data as a key and value pairs.

![alt text](/images/docs/plugins/moengage/form.png)

| Key | value                      |
------------|-----------------------|
| sender    | TXTSMS               | 
| to        | Moesms_destination   |
| message   | Moesms_message|
| service   | T                    |

![alt text](/images/docs/plugins/moengage/headerparams.png)

## OPTIONAL PARAMETERS

| Name        | Descriptions |
| ----------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| entity_id   | Principal Entityid registered in DLT portal (applicable for indian routes only)                                                                                         |
| template_id | TemplateId registered in DLT portal (applicable for indian routes only)                                                                                                 |
| webhook_id  | The `id` of the webhook created in Webhook Section for which the SMS response to be sent after delivery report from operator. [read more](/docs/{version}/sms-push-dlr) |
| time        | Schedule time (in format i.e,yyyy-mm-dd hh:mm:ss) at which the SMS has to be sent.                                                                                      |
| type        | The SMS to be sent is Unicode, Normal or Auto detect. (value "U", "N" or "A")                                                                                           |
| flash       | This parameter can be used to send flash sms via API ( Values 1 or 0.)                                                                                                  |
| custom      | Your own unique_id parameters|
| port | Port number to which SMS has to be delivered |


 