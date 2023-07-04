#### Curl
```
curl -X PUT \
  '{endpoint}sms/senders/ff467e28-7170-4a72-952e-c999cxxxxxx' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer 5b02112fb7xxxxxxxxx' \
  -H 'Content-Type: application/json' \
  -d '{
    "entity_name":"xxxxx",
    "entity_id":"xxxxx",
    "service":"MKT",
    "country_code":"IN"
}'  
```

#### C#
```
var client = new RestClient("{endpoint}/api/v2/sms/senders/9c4500a8-608c-41bb-857a-0e4aae980cdb");
client.Timeout = -1;
var request = new RestRequest(Method.PUT);
request.AddHeader("Authorization", "Bearer 7160f04c05870ee88812a435f65xxxxx");
request.AddHeader("Content-Type", "application/json");
var body = @"{" + "\n" +
@"    ""entity_name"":""sample1""," + "\n" +
@"    ""entity_id"":""12349087""," + "\n" +
@"    ""service"":""G""," + "\n" +
@"    ""country_code"":""IN""" + "\n" +
@"}";
request.AddParameter("application/json", body,  ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
```

#### Java Script

```
var settings = {
  "url": "{endpoint}/api/v2/sms/senders/9c4500a8-608c-41bb-857a-0e4aae98xxxx",
  "method": "PUT",
  "timeout": 0,
  "headers": {
    "Authorization": "Bearer 7160f04c05870ee88812a435f65xxxxx",
    "Content-Type": "application/json"
  },
  "data": JSON.stringify({
    "entity_name": "sample1",
    "entity_id": "12349087",
    "service": "G",
    "country_code": "IN"
  }),
};

$.ajax(settings).done(function (response) {
  console.log(response);
});
```
#### Node

```
var axios = require('axios');
var data = JSON.stringify({
  "entity_name": "sample1",
  "entity_id": "12349087",
  "service": "G",
  "country_code": "IN"
});

var config = {
  method: 'put',
  url: '{endpoint}/api/v2/sms/senders/9c4500a8-608c-41bb-857a-0e4aae9xxxxx',
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