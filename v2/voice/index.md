# Voice Flow

### CALL STATUS

#### Description of Status:

| Name        | Descriptions                                                                                               |
| ----------- | ---------------------------------------------------------------------------------------------------------- |
| ANSWER      | Call is answered. A successful dial. The caller reached the callee.                                        |
| BUSY        | Busy signal. The dial command reached its number but the number is busy.                                   |
| NOANSWER    | The dial command reached its number, the number rang for too long, then the dial timed out.                |
| CANCEL      | Call is cancelled. The dial command reached its number but the caller hung up before the callee picked up. |
| CONGESTION  | This status is usually a sign that the dialled number is not recognised.                                   |
| CHANUNAVAIL | Channel unavailable. On SIP, peer may not be registered.                                                   |
| RECEIVED    | Call received in ivr system but not call forward happen.                                                   |
| MISSED      | Call received in ivr system but not agent responsed to the call.                                           |
| COMPLETED   | Second leg is answered.                                                                                    |

#### Call Strategies

| Name       | Descriptions                                |
| ---------- | ------------------------------------------- |
| parallel   | call all available agents until one answers |
| sequential | Take turns calling each available agents    |
| random     | Call random agents who ever available       |
| fewest     | Call the one with fewest completed calls    |

### REPLACEABLE VARIABLES

We generate some of the variables in flow process, those can used to pass the information your system.

Varibles consist of alphanumeric characters and underscores, should always start with a letter, and do not have any kind of leading sigil (that is, they look like var_name, not \$var_name).

All variables should be enclosed between a set of double curly braces `@{{}}` braces. ex: `@{{to}}`
You can access the Array of the variables with `.` dot notation. Example if you want to access the caller name information from caller object `@{{caller.name}}`

#### FLOW VARIABLES

| Name               | Scope  | Description                                               |
| ------------------ | ------ | --------------------------------------------------------- |
| id                 | global | Call unique id                                            |
| from               | global | Call from number with country code                        |
| to                 | global | Call to number with country code                          |
| bridge             | global | DID number with country code                              |
| start_at           | global | Call Start time in `YYYY-MM-DD h:i:s` format              |
| end_at             | global | Call end time in `YYYY-MM-DD h:i:s` format                |
| date               | global | Current time in `YYYY-MM-DD h:i:s` format                 |
| unixtime           | global | Current time in `unixtime` format                         |
| caller.country     | global | Caller two letters country code. ex: `IN` (India)         |
| caller.provider    | global | Caller two letters operator code. ex: `RJ` (Reliance JIO) |
| caller.region      | global | Caller two letters region code. ex: `KA` (karnataka)      |
| caller.name        | global | Caller name if avaliable in contacts                      |
| caller.email       | global | Caller email if avaliable in contacts                     |
| outgoing.id        | step   | Outgoing call unique id                                   |
| outgoing.parent_id | step   | Outgoing call parent id                                   |
| outgoing.from      | step   | Call from number with country code                        |
| outgoing.to        | step   | Call to number with country code                          |
| outgoing.caller_id | step   | Caller id set to this call                                |
| outgoing.start_at  | step   | Call Start time in `YYYY-MM-DD h:i:s` format              |
| outgoing.end_at    | step   | Call end time in `YYYY-MM-DD h:i:s` format                |
| outgoing.country   | step   | Calling country prefix                                    |
| outgoing.duration  | step   | Call duration incliding ringtime                          |
| outgoing.billing   | step   | Call billable duration                                    |
| outgoing.status    | step   | Call status                                               |
| outgoing.hangup_by | step   | Who disconnect the call first (agent                      | caller) |

#### Advanced output: Filters

Output markup can take filters, which modify the result of the output statement. You can invoke filters by following the output statement's main expression with:

- A pipe character (|)
- The name of the filter
- Optionally, a colon (:) and a comma-separated list of additional parameters to the filter. Each additional parameter must be a valid expression, and each filter pre-defines the parameters it accepts and the order in which they must be passed.

Filters can also be chained together by adding additional filter statements (starting with another pipe character). The output of the previous filter will be the input for the next one.

```
@{{mobile|slice:-10 }}
@{{caller.name|upper}}
@{{date|date_format:'d/m/y'}}
```

| Name        | Description                                                                                                                                                                            |
| ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| append      | append a string e.g. `@{{ 'foo' \| append:'bar' }} #=> 'foobar'`                                                                                                                       |
| ceil        | rounds a number up to the nearest integer, e.g. `@{{ 4.6 \| ceil }} #=> 5`                                                                                                             |
| date_format | reformat a date `@{{start_at \| date_format:'d/m/Y'}}`                                                                                                                                 |
| default     | returns the given variable unless it is null or the empty string, when it will return the given value, e.g `@{{ undefined_variable \| default: "Default value" }} #=> "Default value"` |
| divided_by  | integer division e.g. `@{{ 10 \| divided_by:3 }} #=> 3`                                                                                                                                |
| downcase    | convert an input string to lowercase                                                                                                                                                   |
| escape      | html escape a string                                                                                                                                                                   |
| first       | get the first element of the passed in array                                                                                                                                           |
| floor       | rounds a number down to the nearest integer, e.g. `@{{ 4.6 \| floor }} #=> 4`                                                                                                          |
| lstrip      | strips all whitespace from the beginning of a string                                                                                                                                   |
| minus       | subtraction e.g. `@{{ 4 \| minus:2 }} #=> 2`                                                                                                                                           |
| modulo      | remainder, e.g. `@{{ 3 \| modulo:2 }} #=> 1`                                                                                                                                           |
| plus        | addition e.g. `@{{ '1' \| plus:'1' }} #=> 2, @{{ 1 \| plus:1 }} #=> 2`                                                                                                                 |
| prepend     | prepend a string e.g. `@{{ 'bar' \| prepend:'foo' }} #=> 'foobar'`                                                                                                                     |
| round       | rounds input to the nearest integer or specified number of decimals e.g. `@{{ 4.5612 \| round: 2 }} #=> 4.56`                                                                          |
| rstrip      | strips all whitespace from the end of a string                                                                                                                                         |
| size        | return the size of an array or string                                                                                                                                                  |
| slice       | slice a string. Takes an offset and length, e.g. @{{ "hello" \| slice: -3, 3 }} #=> llo                                                                                                |
| split       | split a string on a matching pattern e.g. `@{{ "a~b" \| split:"~" }} #=> ['a','b']`                                                                                                    |
| strip       | strips all whitespace from both ends of the string                                                                                                                                     |
| times       | multiplication e.g `@{{ 5 \| times:4 }} #=> 20`                                                                                                                                        |
| upcase      | convert an input string to uppercase                                                                                                                                                   |
| url_encode  | url encode a string                                                                                                                                                                    |

**Strings.** Literal strings must be surrounded by double quotes or single quotes ("my string" or 'my string'). There is no difference; neither style allows variable interpolation.

**Integers.** Integers must not be quoted.

**Booleans and nil.** The literal values true, false, and nil.

#### Other variable within variable

Sometimes you want to use the other variable value with in variable to get the right value

`[]` can used to pass the variable with in other variable. ex: `@{{questions.[jump].name}}`

Here we are using `jump` variable to get the original value of question.

it will be `question.0.name`, `question.1.name`, `question.2.name`

#### Variables in play

We can define how to treat the variables while playing.

`digits` we want to say as digits, we can use `@{{otp@digits}}`

`number` we want to say as number, we can use `@{{otp@number}}`

`play` we want to download the mp3 file and play, we can use `@{{clip@play}}`

`sound` to play in build sound files, we can use `@{{clip@sound}}`

#### 3-way calling

We can convert a 2-way call into 3-way.

Press `#` while you are in call. Then enter the receiver number.

After you are connected to the third person, press `**` to convert the call into conference.
