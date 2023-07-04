#### Curl
```
curl --location --request PUT '{endpoint}/api/v2/sms/templates/c61293e2-14f1-405b-b299-2b71f16xxxxx' \
--header 'Authorization: Bearer 7160f04c05870ee88812a435f65xxxxx' \
--header 'Content-Type: application/json' \
--data-raw '{
    "sender": "vasavi",
    "name": "temp12",
    "body": "Welcome to mobtexting family",
    "template_id": ""
}'
```

#### C#
```
var client = new RestClient("{endpoint}/api/v2/sms/templates/c61293e2-14f1-405b-b299-2b71f16xxxxx");
client.Timeout = -1;
var request = new RestRequest(Method.PUT);
request.AddHeader("Authorization", "Bearer 7160f04c05870ee88812a435f65xxxxx");
request.AddHeader("Content-Type", "application/json");
var body = @"{" + "\n" +
@"    ""sender"": ""xxxxx""," + "\n" +
@"    ""name"": ""temp12""," + "\n" +
@"    ""body"": ""Welcome to mobtexting family""," + "\n" +
@"    ""template_id"": """"" + "\n" +
@"}";
request.AddParameter("application/json", body,  ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
```

#### Java Script
```
var settings = {
  "url": "{endpoint}/api/v2/sms/templates/c61293e2-14f1-405b-b299-2b71f16xxxxx",
  "method": "PUT",
  "timeout": 0,
  "headers": {
    "Authorization": "Bearer 7160f04c05870ee88812a435f65xxxxx",
    "Content-Type": "application/json"
  },
  "data": JSON.stringify({
    "sender": "xxxxx",
    "name": "temp12",
    "body": "Welcome to mobtexting family",
    "template_id": ""
  }),
};

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

#### Node Js
```
var axios = require('axios');
var data = JSON.stringify({
  "sender": "xxxxx",
  "name": "temp12",
  "body": "Welcome to mobtexting family",
  "template_id": ""
});

var config = {
  method: 'put',
  url: '{endpoint}/api/v2/sms/templates/c61293e2-14f1-405b-b299-2b71f16xxxxx',
  headers: { 
    'Authorization': 'Bearer 7160f04c05870ee88812a435f65xxxx', 
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