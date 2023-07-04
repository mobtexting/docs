# Create Sound File

This Voice API supports the following:
#include "_include/endpoint.md"

#### POST

```
{endpoint}voice/sounds
```

#### MANDATORY PARAMETERS

| Name  | Descriptions                       |
| ----- | ---------------------------------- |
| audio | sound file that you want to upload |

#### OPTIONAL PARAMETERS

| Name | Descriptions                             |
| ---- | ---------------------------------------- |
| name | name of the sound file for your response |

#### Example Request

```
curl -X POST '{endpoint}voice/sounds?access_token=7160f04c05870ee88812a435xxxxxxxx' \
--header 'Accept: application/json' \
--form 'name=myaudiofile' \
--form 'audio=@/home/mdigital/Desktop/testsms/welcome.mp3'
```

#### Example Response

```json
{
  "status": "OK",
  "message": "Sound uploaded successfully",
  "data": {
    "id": "5d2c9c40-8f00-48f3-902e-d4c1f2a7b0a4"
  }
}
```

- The `id` parameter in response can be used for outgoing campaign purpose as a audio source.
