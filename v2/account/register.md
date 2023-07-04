# User Registration Api

Registration api will support only `POST` method.
#include "_include/endpoint.md"

#### POST

```
{domain}/api/{version}/register
```

#### MANDATORY PARAMETERS

| Name     | Descriptions                                                                                    |
| -------- | ----------------------------------------------------------------------------------------------- |
| name     | Name of the user                                                                                |
| email    | EmailId of the user                                                                             |
| password | Password must contain uppercase, lowercase characters and numbers. Lenght between 6 to 20 chars |

#### OPTIONAL PARAMETERS

| Name   | Descriptions                   |
| ------ | ------------------------------ |
| mobile | Mobile number with coutry code |

#### Example Request

```
curl -X POST \
  {domain}/api/{version}/register \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -F name=Lakshman \
  -F email=youremailid@mail.com \
  -F mobile=91886713xxxx \
  -F password=Qwe@12334
```

Kindly replace the name, email, mobile, password accroding to your details.

#### Example Response

```json
{
  "status": "OK",
  "message": "User registered successfully"
}
```
