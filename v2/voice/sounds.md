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

#code "{version}/_code/voice/sounds.json"

#### Example Response

```json
{
    "status": "OK",
    "code": 200,
    "message": "Sound uploaded successfully",
    "data": {
        "id": "29ab2b24-3f93-441c-ae9c-6404361e5d14"
    }
}
```

- The `id` parameter in response can be used for outgoing campaign purpose as a audio source.
