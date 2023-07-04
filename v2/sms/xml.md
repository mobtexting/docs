# Send SMS Using XML object
#include "_include/endpoint.md"

#### POST

```
{endpoint}sms/send/xml
```

You can send sms using `POST` method content in body.

`root` entry holds the default values for each node. You can overwite the `root` values inside `nodes` value except `webhook_id`, `service` and `time`.

#### BODY

```xml
<?xml version="1.0" encoding="UTF-8"?>
<data>

   <root>
      <webhook_id>1234a-1knnn-13XXXX</webhook_id>
      <message><![CDATA[global message]]></message>
      <sender>SANKAR</sender>
      <service>T</service>
      <time>2018-07-05 10:30AM</time>
      <type>N</type>
      <entity_id>1233555XXXXXXXXX</entity_id>
      <template_id>9002929XXXXXXX</template_id>
   </root>

   <nodes>
      <node>
         <custom>9190199556xx</custom>
         <message><![CDATA[this message will be used insted of root]]></message>
         <sender>SANKAR</sender>
         <to>919019955622</to>
      </node>
      <node>
         <custom>34</custom>
         <to>9188671356xx</to>
         <sender>SANKAR</sender>
      </node>
   </nodes>

</data>
```

#### MANDATORY PARAMETERS

| Name    | Descriptions                                                                            |
| ------- | --------------------------------------------------------------------------------------- |
| to      | Phone number to send with country prefix. (multiple numbers can be separated by comma.) |
| message | The content of the SMS                                                                  |
| sender  | The registered and approved Sender-id                                                   |
| service | Determines whether the SMS to be sent is Transactional, Promotional or other.           |

#### OPTIONAL PARAMETERS

| Name        | Descriptions                                                                                                                                                            |
| ----------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| webhook_id  | The `id` of the webhook created in Webhook Section for which the SMS response to be sent after delivery report from operator. [read more](/docs/{version}/sms-push-dlr) |
| time        | Schedule time (in format i.e,yyyy-mm-dd hh:mm:ss) at which the SMS has to be sent.                                                                                      |
| type        | The SMS to be sent is Unicode, Normal or Auto detect. (value "U", "N" or "A")                                                                                           |
| flash       | This parameter can be used to send flash sms via API ( Values 1 or 0.)                                                                                                  |
| custom      | Any customised parameters can be passed using this parameter                                                                                                            |
| port        | Port number to which SMS has to be sent                                                                                                                                 |
| entity_id   | Entityid registered in DLT portal                                                                                                                                       |
| template_id | TemplateId registered in DLT portal                                                                                                                                     |

#### Example Request

```curl
curl -X POST \
  "{endpoint}sms/send/xml" \
  -H 'Authorization: Bearer 425b8dec5d6b618fa9c08xxxx' \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/xml' \
  -d '<?xml version="1.0" encoding="UTF-8"?>
<data>

   <root>
      <webhook_id>1234-afwrr-1sXXXx</webhook_id>
      <message><![CDATA[global message]]></message>
      <sender>SANKAR</sender>
      <service>T</service>
      <time>2018-07-05 10:30AM</time>
      <type>N</type>
      <flash>0</flash>
      <entity_id>1233555XXXXXXXXX</entity_id>
      <template_id>9002929XXXXXXX</template_id>
   </root>

   <nodes>
      <node>
         <message><![CDATA[this message will be used insted of root]]></message>
         <sender>SANKAR</sender>
         <to>9190199556xx</to>
         <custom>9190199556xx</custom>
      </node>
      <node>
         <custom>34</custom>
         <to>9188671356xx</to>
         <sender>SANKAR</sender>
      </node>
   </nodes>

</data>'
```

#### Example Response

```json
{
  "status": 200,
  "message": "2 numbers accepted for delivery.",
  "data": [
    {
      "id": "b34e35ad-fe34-4a8b-977c-b21cd76cd7d6:1",
      "mobile": "919019xxxx2",
      "status": "AWAITING-DLR",
      "units": 1,
      "length": 7,
      "charges": 1,
      "customid": "346576-446565-45657-XFTR",
      "iso_code": null,
      "submitted_at": "2018-07-09 16:27:35"
    },
    {
      "id": "b34e35ad-fe34-4a8b-977c-b21cd76cd7d6:1",
      "mobile": "9188xxxxxxxxxx",
      "status": "AWAITING-DLR",
      "units": 1,
      "length": 7,
      "charges": 1,
      "customid": "34",
      "iso_code": null,
      "submitted_at": "2018-07-09 16:27:35"
    }
  ]
}
```
