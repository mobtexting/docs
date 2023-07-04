#### Curl
```
curl -X GET \
  '{endpoint}sms/templates?filter[name]=test' \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 5b02112fb7xxxxxxxxx'
```
Kindly replace the token with your respective access_token and other params.

#### C#
```
var client = new RestClient("{endpoint}/api/v2/sms/templates");
client.Timeout = -1;
var request = new RestRequest(Method.GET);
request.AddHeader("Authorization", "Bearer 7160f04c05870ee88812a435f65xxxxx");
var body = @"";
request.AddParameter("text/plain", body,  ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
```

#### Java Script
```
var settings = {
  "url": "{endpoint}/api/v2/sms/templates",
  "method": "GET",
  "timeout": 0,
  "headers": {
    "Authorization": "Bearer 7160f04c05870ee88812a435f65xxxxx"
  },
};

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

#### Node 
```
var axios = require('axios');
var data = '';

var config = {
  method: 'get',
  url: '{endpoint}/api/v2/sms/templates',
  headers: { 
    'Authorization': 'Bearer 7160f04c05870ee88812a435f65xxxxx'
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

