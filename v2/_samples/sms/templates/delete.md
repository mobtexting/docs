#### Curl
```
curl --location --request DELETE '{endpoint}/api/v2/sms/templates/8ac3c113-b697-4340-aa3a-05151dxxxxxx' \
--header 'Authorization: Bearer 7160f04c05870ee88812a435f65xxxxx' \
--data-raw ''
```

#### C#
```
var client = new RestClient("{endpoint}/api/v2/sms/templates/8ac3c113-b697-4340-aa3a-05151dxxxxxx");
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
var settings = {
  "url": "{endpoint}/api/v2/sms/templates/8ac3c113-b697-4340-aa3a-05151dxxxxxx",
  "method": "DELETE",
  "timeout": 0,
  "headers": {
    "Authorization": "Bearer 7160f04c05870ee88812a435f65xxxxx"
  },
};

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

#### Node Js
```
var axios = require('axios');
var data = '';

var config = {
  method: 'delete',
  url: '{endpoint}/api/v2/sms/templates/8ac3c113-b697-4340-aa3a-05151dxxxxxx',
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