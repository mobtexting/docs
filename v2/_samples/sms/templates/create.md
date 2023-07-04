#### Curl
```
curl --location --request POST '{endpoint}/api/v2/sms/templates' \
--header 'Authorization: Bearer 7160f04c05870ee88812a435f65xxxxx' \
--header 'Content-Type: application/json' \
--data-raw '{
    "sender": "xxxxx",
    "name": "temp",
    "body": "This is verification{{1}} and {{2}}",
    "template_id": "1234567",
    "type": "ENT"
}'
```

#### C#
```
var client = new RestClient("{endpoint}/api/v2/sms/templates");
client.Timeout = -1;
var request = new RestRequest(Method.POST);
request.AddHeader("Authorization", "Bearer 7160f04c05870ee88812a435f65xxxxx");
request.AddHeader("Content-Type", "application/json");
var body = @"{" + "\n" +
@"    ""sender"": ""xxxxx""," + "\n" +
@"    ""name"": ""temp""," + "\n" +
@"    ""body"": ""This is verification{{1}} and {{2}}""," + "\n" +
@"    ""template_id"": ""1234567""," + "\n" +
@"    ""type"": ""ENT""" + "\n" +
@"}";
request.AddParameter("application/json", body,  ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
```

#### JavaScript
```
var settings = {
  "url": "{endpoint}/api/v2/sms/templates",
  "method": "POST",
  "timeout": 0,
  "headers": {
    "Authorization": "Bearer 7160f04c05870ee88812a435f65xxxxx",
    "Content-Type": "application/json"
  },
  "data": JSON.stringify({
    "sender": "xxxxx",
    "name": "temp",
    "body": "This is verification{{1}} and {{2}}",
    "template_id": "1234567",
    "type": "ENT"
  }),
};

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

#### NodeJs
```
var axios = require('axios');
var data = JSON.stringify({
  "sender": "vasavi",
  "name": "temp",
  "body": "This is verification{{1}} and {{2}}",
  "template_id": "1234567",
  "type": "ENT"
});

var config = {
  method: 'post',
  url: '{endpoint}/api/v2/sms/templates',
  headers: { 
    'Authorization': 'Bearer 7160f04c05870ee88812a435f65xxxxx', 
    'Content-Type': 'application/json'
  },
  data : data
};

axios(config)
.then(function (response) {
  console.log(JSON.stringify(response.data));
})
.catch(function (error) {
  console.log(error);
});
```
