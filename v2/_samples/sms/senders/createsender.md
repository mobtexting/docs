### C#
```
var client = new RestClient("{endpoint}/api/v2/sms/senders");
client.Timeout = -1;
var request = new RestRequest(Method.GET);
request.AddHeader("Authorization", "Bearer 7160f04c05870ee88812a435f65xxxxx");
var body = @"";
request.AddParameter("text/plain", body,  ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
```

### Java Script
```
var myHeaders = new Headers();
myHeaders.append("Authorization", "Bearer 7160f04c05870ee88812a435f65xxxxx");

var raw = "";

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("{endpoint}/api/v2/sms/senders", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

### Curl
```
curl -X POST \
  '{endpoint}sms/senders' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer 5b02112fb7xxxxxxxxxxxxxxxx' \
  -H 'Content-Type: application/json' \
  -d '{
    "name":"xxxxxx",
    "service":"xxxxxx",
    "entity_name":"xxxxx",
    "entity_id":"xxxxx" ,
    "country_code":"IN" 
}'
```