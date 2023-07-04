# Delete Smart Link

#include "_include/endpoint.md"

#### DELETE

```
{endpoint}link/urls/{id}
```

Replace the {id} with the actual id of the link that you would like to delete.

#### Example Request

```
curl -X POST \
  '{endpoint}link/urls/{id}' \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 5b02112fb7xxxxxxxxx'
    -H 'Content-Type: application/x-www-form-urlencoded' \
  -d 'title=smart%20link&long_url=https%3A%2F%2Fwww.google.com&advanced=1'
```

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Link Deleted Successfully",
  "data": []
}
```
