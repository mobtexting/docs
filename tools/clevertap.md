# Clevertap SMS Integration

## Integration Steps for send sms
To integrate with Clevertap as an SMS provider, perform the following steps:
1. In the CleverTap dashboard, navigate to Settings > Engage > Channels > SMS.
2. Click + Add Provider.
![alt text](/images/docs/plugins/clevertap/addprovider.png)
3. Under Provider, select Other (Generic).
4. Select POST method and give following api as a provider end point  
```
{domain}/api/v2/sms/clevertap/send
```
5. Under Authentication, choose No Authentication.

6. Select Headers to pass along any HTTP headers which will be added to the HTTP request sent to the API endpoint.

![alt text](/images/docs/plugins/clevertap/headers.png)

Enter key and value pairs.
| Key | value              |
| ---------------| -------------------------------------|
| Accept         | application/json|
| Authorization  | Bearer 7160f04c05870ee************** |
| Content-Type   | application/x-www-form-urlencoded    |

7. Select Parameters and choose x-www-form-urlencoded to pass key and value pairs.
![alt text](/images/docs/plugins/clevertap/parameters.png)

| Key | value                      |Descriptions|
------------|-----------------------|-------------|
| sender    | TXTSMS               |The registered and approved Sender-id | 
| to        | 8074******           |Phone number to send with country prefix. (multiple numbers can be separated by comma.)|
| message   | welcome to CPaaS|The content of the SMS|
| service   | T                    |Determines whether the SMS to be sent is Transactional, Promotional or other.|

## System Dynamic Replacements
for dynamic variables check [here](https://docs.clevertap.com/docs/generic-sms#system-dynamic-replacements)

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

## Send sms using json 
Select POST method and give following api as a provider end point.  

```
{domain}/api/v2/sms/clevertap/json
```

![alt text](/images/docs/plugins/clevertap/headers.png)

Select Headers to pass along any HTTP headers which will be added to the HTTP request sent to the API endpoint.

Enter key and value pairs.
| Key | value              |
| ---------------| -------------------------------------|
| Authorization  | Bearer 7160f04c05870ee************** |
| Content-Type   | application/json                     |

Select Parameters and choose json to pass a json object as following below.

```
{
    "root": {
        "type": "A",
        "flash": 0,
        "sender": "TXTSMS",
        "message": "welcome to CPaas Alerts,
        "service": "T"
    },
    "nodes": [
        {
            "to": "919492******",
            "sender": "MOBSMS",
            "message": "Message from & json api node 1"
        },
        {
            "to": "918074******"
        }
    ]
}

```



 