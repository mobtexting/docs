# CREATE OUTBOUND CALL USING TEXT

Using Text2Speech API we can trigger a call using text as input and that text will be played as voice message once recipient answers the call.

#### API Endpoint

```
{domain}/api/{version}/
```

#### POST

```
{endpoint}outgoing/tts
```

#### MANDATORY PARAMETERS

| Name   | Descriptions                                                                       |
| ------ | ---------------------------------------------------------------------------------- |
| bridge | Bridge number for call initiation                                                  |
| to     | Phone number with country code to which call has to connect                        |
| text   | Message text you want to send which will be played as speech once call is answered |

#### OPTIONAL PARAMETERS

| Name            | Descriptions                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| options         | Extra options for TTS API                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| break           | definition of the break that you can add in the text to Play                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| >identifier     | Identifier for the break characters in message text to play                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| time            | Break duration                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| voice           | definition of voice options                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| language        | language in which the text will be played. Possible values are English, French, German, Dutch, Spanish, Italian, Portuguese, Russian                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| gender          | gender of the voice in which the text will be played. Possible values are Female and Male                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| iteration_tries | number of iterations the text will be played. By default, iterationsNumber is set to 1                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| iteration_delay | break time between 2 iterations of the text. delay is mentioned in sec.Default 0.5 sec                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| voiceid         | id of the voice in which the text will be played, these Ids can be chosen from this list: Nicole, Kevin, Enrique, Tatyana, Russell, Olivia, Lotte, Geraint, Carmen, Mads, Penelope, Mia, Joanna, Matthew, Brian, Seoyeon, Ruben, Ricardo, Maxim, Lea, Giorgio, Carla, Naja, Maja, Astrid, Ivy, Kimberly, Chantal, Amy, Vicki, Marlene, Ewa, Conchita, Camila, Karl, Zeina, Miguel, Mathieu, Justin, Lucia, Jacek, Bianca, Takumi, Ines, Gwyneth, Cristiano, Mizuki, Celine, Zhiyu, Jan, Liv, Joey, Raveena, Filiz, Dora, Salli, Aditi, Vitoria, Emma, Lupe, Hans, Kendra |

## Voice Examples

| Name      | Language                | Gender |
| --------- | ----------------------- | ------ |
| Aditi     | Hindi                   | Female |
| Raveena   | English                 | Female |
| Zeina     | Arabic                  | Female |
| Hala      | Arabic (Gulf)           | Female |
| Arlet     | Catalan                 | Female |
| Hiujin    | Chinese (Cantonese)     | Female |
| Zhiyu     | Chinese (Mandarin)      | Female |
| Naja      | Danish                  | Female |
| Laura     | Dutch                   | Female |
| Nicole    | English (Australian)    | Female |
| Amy       | English (British)       | Female |
| Aria      | English (New Zealand)   | Female |
| Ayanda    | English (South African) | Female |
| Kendra    | English (US)            | Female |
| Geraint   | English (Welsh)         | Male   |
| Suvi      | Finnish                 | Female |
| Léa       | French                  | Female |
| Chantal   | French (Canadian)       | Female |
| Marlene   | German                  | Female |
| Hans      | German                  | Male   |
| Dóra/Dora | Icelandic               | Female |
| Carla     | Italian                 | Female |
| Mizuki    | Japanese                | Female |
| Seoyeon   | Korean                  | Female |
| Liv       | Norwegian               | Female |
| Ewa       | Polish                  | Female |
| Camila    | Portuguese (Brazilian)  | Female |
| Inês/Ines | Portuguese (European)   | Female |
| Carmen    | Romanian                | Female |
| Tatyana   | Russian                 | Female |
| Conchita  | Spanish (European)      | Female |
| Mia       | Spanish (Mexican)       | Female |
| Lupe      | Spanish (US)            | Female |
| Astrid    | Swedish                 | Female |
| Filiz     | Turkish                 | Female |
| Gwyneth   | Welsh                   | Female |

## Example Request Using Break Characters

```
curl -X POST '{endpoint}outgoing/tts' \
    -H 'authorization: Bearer 46fd72850fXXXXXX' \
  -H 'cache-control: no-cache' \
  -H 'content-type: application/json' \
  -d '{
    "bridge": "9172007XXX",
    "to": 918867XXXXXX,
    "text": "Hi## This is the text to speech using ##outgoing api",
    "options": {
        "language": "en-US",
        "break": {
            "identifier": "##",
            "time": 1
        }
    }
}'
```

#### Example Response

```json
{
  "status": "OK",
  "message": "Calls queued successfully",
  "data": [
    {
      "id": "52ecf5da-259b-4e0f-a2eb-XXXXXX",
      "channel": "outgoing",
      "caller_id": "917200XXXXXX",
      "mobile": "918867XXXXXX",
      "flow_id": "5784",
      "credits": "0.0005",
      "created_at": "2023-01-23T12:13:25.666366Z",
      "foreign_id": null,
      "status": "queued"
    }
  ]
}
```

## Example Request Using Voice options

```
curl -X POST '{endpoint}outgoing/tts' \
    -H 'authorization: Bearer 46fd72850fXXXXXX' \
  -H 'cache-control: no-cache' \
  -H 'content-type: application/json' \
  -d '{
    "bridge": "9172007XXX",
    "to": 918867XXXXXX,
    "text": "Hi## This is the text to speech using ##outgoing api",
    "options": {
        "language": "en-US",
        "break": {
            "identifier": "##",
            "time": 1
        },
        "voice": {
            "language": "german",
            "gender":"male"
        }
    }
}'
```

#### Example Response

```json
{
  "status": "OK",
  "message": "Calls queued successfully",
  "data": [
    {
      "id": "52ecf5da-259b-4e0f-a2eb-XXXXXX",
      "channel": "outgoing",
      "caller_id": "917200XXXXXX",
      "mobile": "918867XXXXXX",
      "flow_id": "5784",
      "credits": "0.0005",
      "created_at": "2023-01-23T12:13:25.666366Z",
      "foreign_id": null,
      "status": "queued"
    }
  ]
}
```

## Example Request Using Iteration of text

```
curl -X POST '{endpoint}outgoing/tts' \
    -H 'authorization: Bearer 46fd72850fXXXXXX' \
  -H 'cache-control: no-cache' \
  -H 'content-type: application/json' \
  -d '{
    "bridge": "9172007XXX",
    "to": 918867XXXXXX,
    "text": "Hi## This is the text to speech using ##outgoing api",
    "options": {
        "language": "en-US",
        "break": {
            "identifier": "##",
            "time": 1
        },
        "iteration_tries": 2
    }
}'
```

#### Example Response

```json
{
  "status": "OK",
  "message": "Calls queued successfully",
  "data": [
    {
      "id": "52ecf5da-259b-4e0f-a2eb-XXXXXX",
      "channel": "outgoing",
      "caller_id": "917200XXXXXX",
      "mobile": "918867XXXXXX",
      "flow_id": "5784",
      "credits": "0.0005",
      "created_at": "2023-01-23T12:13:25.666366Z",
      "foreign_id": null,
      "status": "queued"
    }
  ]
}
```
