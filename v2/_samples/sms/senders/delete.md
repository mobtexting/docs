#### Curl
```
curl -X DELETE \
  '{endpoint}sms/senders/ff467e28-7170-4a72-952e-c999cxxxxxx' \
  -H 'Authorization: Bearer 5b02112fb7xxxxxxxxxxxxxxx' \
```

#### C#
```
var client = new RestClient("{endpoint}/api/v2/sms/senders/5cd1f09b-fb97-465a-8ce7-e2e9136xxxxx");
client.Timeout = -1;
var request = new RestRequest(Method.DELETE);
request.AddHeader("Authorization", "Bearer 7160f04c05870ee88812a435f65xxxxx");
var body = @"";
request.AddParameter("text/plain", body,  ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
```

#### Java Script
```
var client = new RestClient("{endpoint}/api/v2/sms/senders/5cd1f09b-fb97-465a-8ce7-e2e9136xxxxx");
client.Timeout = -1;
var request = new RestRequest(Method.DELETE);
request.AddHeader("Authorization", "Bearer 7160f04c05870ee88812a435f65xxxxx");
var body = @"";
request.AddParameter("text/plain", body,  ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
```
#### Node Js
```
var axios = require('axios');
var data = '';

var config = {
  method: 'delete',
  url: '{endpoint}/api/v2/sms/senders/5cd1f09b-fb97-465a-8ce7-e2e9136xxxxx',
  headers: { 
    'Authorization': 'Bearer 7160f04c05870ee88812a435f65xxxxxx'
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