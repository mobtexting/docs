# SMPP Gateway

SMPP (Short Message Peer-to-Peer) is a protocol used by the telecommunications industry for
exchanging SMS messages between Short Message Service Centers (SMSC) and External Short
Messaging Entities (ESME). The SMPP protocol is sent through TCP/IP, which allows faster
delivery of SMS messages.

## INTRODUCTION

The Messaging Platform uses the SMPP v3.4 Protocol Specification Issue 1.5, However it has been designed to be backward compatible with SMPP v3.3.
This document should be read in conjunction with SMPP v3.4 Specification v1.5 and
assumes with SMPP a level of familiarity functionality.

## SERVER LIST

{app} has multiple SMPP servers for you to connect to. Each SMPP server offers the ability to connect to it via the regular (plaintext) method or via a TLS1.0 or better connection.

Here is an overview of the available servers:

| Hostname            | Port |
| ------------------- | ---- |
| smpp1.{smpp_domain} | 3634 |
| smpp2.{smpp_domain} | 3634 |

## Additional TLV (For Indian Routes)

| Mandatory TLV          | Tag value Decimal | Tag value Hex |
| ---------------------- | ----------------- | ------------- |
| PE_ID                  | 5120              | 1400          |
| Template_ID            | 5121              | 1401          |
| Telemarketer_ID(TM_ID) | 51212             | 1402          |

## CONNECTIVITY

Clients may connect to the Messaging Platform Server multiple numbers of times. This may be of importance if the client wishes to deploy multiple applications simultaneously. To connect to the platform, one needs to specify the following parameters:

**IP Address and Port:**
This is the TCP/IP endpoint on which the ESME should connect to the platform.

**Username:**
This is the username (`system_id`) of your account configured on the Platform

**Password:**
Password for the above account. Required for security reasons to prevent unauthorized access to your account.

**System_type:**
Set the system_type field to `smpp`.

**Interface_version:**
The client application should connect with the interface_version field set to 0x34 (52 decimal), if it is using SMPP v3.4, otherwise the Platformassumes that the application uses SMPP v3.3.

**enquire_link:** The application should issue an enquire_link every minute. This will
ensure the link stays active even when it is not in use. The Messaging Platform will automatically disconnect any link which is inactive for more than 5mins.

## BINDINGS AND THROUGHPUT

Whenever an SMPP account has been setup for you, you’ll receive the maximum amount of binds you’re allowed to set up as well as a maximum throughput. In most cases, these values will be something like 3 binds and 50 message per seconds.

It might be interesting to note that these values are enforced on a per-server basis. That means that given the above example, you can set up 9 binds in total with a throughput of 150 messages per second when you connect to all servers.

Be aware that for maintenance purposes we only guarantee either that one server is up at any given time. So we advise to connect to all of them.

## BINDINGS AND RELAYING

{app}’s message relaying system is connection and server agnostic. That means that when you send an MT via a `submit_sm` PDU on connection A, you might receive the matching DLR in the form of a `deliver_sm` on connection B if both connections are bound with the same username. This is even true for connections made to different servers, so the above scenario would still be true if connection A is made to the smpp01 server and connection B to the smpp02 server.

## SUBMITTING MESSAGES

#### Submission Types:

Messages may be submitted with either `submit_sm` or `data_sm`, using either the
short_message or message_payload fields. The message length may not exceed the
byte limit for the network that the message is being sent to (for example 140 bytes
on GSM networks).

The Platform does not support submit_multi. If the same message has to be sent to multiple destinations, each message must be sent separately.

Concatenated messages are supported by using the User Data Header (UDH), which is included in the message size byte limit.

#### Submit Responses

A positive response to a `submit` will contain an error code of zero and a non-null message reference.

A negative response will contain a vendor specific error code. The complete set of SMPP Error Codes and their associated values are defined in the following table.

| Error Number | Error Name              | Error Description                                  |
| ------------ | ----------------------- | -------------------------------------------------- |
| 0x00000000   | ESME_ROK                | No Error                                           |
| 0x00000001   | ESME_RINVMSGLEN         | Message too long                                   |
| 0x00000002   | ESME_RINVCMDLEN         | Command length is invalid                          |
| 0x00000003   | ESME_RINVCMDID          | Command ID is invalid or not supported             |
| 0x00000004   | ESME_RINVBNDSTS         | Incorrect bind status for given command            |
| 0x00000005   | ESME_RALYBND            | Already bound                                      |
| 0x00000006   | ESME_RINVPRTFLG         | Invalid Priority Flag                              |
| 0x00000007   | ESME_RINVREGDLVFLG      | Invalid registered delivery flag                   |
| 0x00000008   | ESME_RSYSERR            | System error                                       |
| 0x0000000A   | ESME_RINVSRCADR         | Invalid source address                             |
| 0x0000000B   | ESME_RINVDSTADR         | Invalid destination address                        |
| 0x0000000C   | ESME_RINVMSGID          | Message ID is invalid                              |
| 0x0000000D   | ESME_RBINDFAIL          | Bind failed                                        |
| 0x0000000E   | ESME_RINVPASWD          | Invalid password                                   |
| 0x0000000F   | ESME_RINVSYSID          | Invalid System ID                                  |
| 0x00000011   | ESME_RCANCELFAIL        | Cancelling message failed                          |
| 0x00000013   | ESME_RREPLACEFAIL       | Message recplacement failed                        |
| 0x00000014   | ESME_RMSSQFUL           | Message queue full                                 |
| 0x00000015   | ESME_RINVSERTYP         | Invalid service type                               |
| 0x00000033   | ESME_RINVNUMDESTS       | Invalid number of destinations                     |
| 0x00000034   | ESME_RINVDLNAME         | Invalid distribution list name                     |
| 0x00000040   | ESME_RINVDESTFLAG       | Invalid destination flag                           |
| 0x00000042   | ESME_RINVSUBREP         | Invalid submit with replace request                |
| 0x00000043   | ESME_RINVESMCLASS       | Invalid esm class set                              |
| 0x00000044   | ESME_RCNTSUBDL          | Invalid submit to ditribution list                 |
| 0x00000045   | ESME_RSUBMITFAIL        | Submitting message has failed                      |
| 0x00000048   | ESME_RINVSRCTON         | Invalid source address type of number ( TON )      |
| 0x00000049   | ESME_RINVSRCNPI         | Invalid source address numbering plan ( NPI )      |
| 0x00000050   | ESME_RINVDSTTON         | Invalid destination address type of number ( TON ) |
| 0x00000051   | ESME_RINVDSTNPI         | Invalid destination address numbering plan ( NPI ) |
| 0x00000053   | ESME_RINVSYSTYP         | Invalid system type                                |
| 0x00000054   | ESME_RINVREPFLAG        | Invalid replace_if_present flag                    |
| 0x00000055   | ESME_RINVNUMMSGS        | Invalid number of messages                         |
| 0x00000058   | ESME_RTHROTTLED         | Throttling error                                   |
| 0x00000061   | ESME_RINVSCHED          | Invalid scheduled delivery time                    |
| 0x00000062   | ESME_RINVEXPIRY         | Invalid Validty Period value                       |
| 0x00000063   | ESME_RINVDFTMSGID       | Predefined message not found                       |
| 0x00000064   | ESME_RX_T_APPN          | ESME Receiver temporary error                      |
| 0x00000065   | ESME_RX_P_APPN          | ESME Receiver permanent error                      |
| 0x00000066   | ESME_RX_R_APPN          | ESME Receiver reject message error                 |
| 0x00000067   | ESME_RQUERYFAIL         | Message query request failed                       |
| 0x000000C0   | ESME_RINVTLVSTREAM      | Error in the optional part of the PDU body         |
| 0x000000C1   | ESME_RTLVNOTALLWD       | TLV not allowed                                    |
| 0x000000C2   | ESME_RINVTLVLEN         | Invalid parameter length                           |
| 0x000000C3   | ESME_RMISSINGTLV        | Expected TLV missing                               |
| 0x000000C4   | ESME_RINVTLVVAL         | Invalid TLV value                                  |
| 0x000000FE   | ESME_RDELIVERYFAILURE   | Transaction delivery failure                       |
| 0x000000FF   | ESME_RUNKNOWNERR        | Unknown error                                      |
| 0x00000100   | ESME_RSERTYPUNAUTH      | ESME not authorised to use specified servicetype   |
| 0x00000101   | ESME_RPROHIBITED        | ESME prohibited from using specified operation     |
| 0x00000102   | ESME_RSERTYPUNAVAIL     | Specified servicetype is unavailable               |
| 0x00000103   | ESME_RSERTYPDENIED      | Specified servicetype is denied                    |
| 0x00000104   | ESME_RINVDCS            | Invalid data coding scheme                         |
| 0x00000105   | ESME_RINVSRCADDRSUBUNIT | Invalid source address subunit                     |
| 0x00000106   | ESME_RINVSTDADDRSUBUNIR | Invalid destination address subunit                |
| 0x0000040B   | ESME_RINVBALANCE        | Insufficient credits to send message               |

### Character Sets, Class and Data Coding

The Messaging Platform supports the following two types of data coding schemes: - GSM 03.38 Encoding (default) - Latin 1 (ISO-8859-1) encoding

The default character set is GSM 338. Although for data_coding=1 the character set GSM 03.38 is supported it is NOT RECOMMENDED, as it is known to cause problems with character encoding. Please set data_coding = 3 for ISO-8859-1(if and only if told so explicitly) encoded messages and data_coding=0 for GSM 03.38 encoded messages.

For Unicode messages you have to set data_coding = 8 and the message is expected in UTF-16 Big Endean format.

### Delivery Reports

The Messaging Platform will return a delivery report (Intermediate and/or final depending on the route) for a specific message to the client application when the registered_delivery field, while submitting the message, is set to 1. In order
to retrieve the delivery report from our server the client will have to connect to the Messaging Platform in the receiver or transceiver mode

Status and error code which can be returned by Messaging Platform.

| Code | Status                | Status Description                                  |
| ---- | --------------------- | --------------------------------------------------- |
| 000  | DELIVRD               | Delivered to SIM.                                   |
| 001  | INVALID-SUB           | Unidentified subscriber.                            |
| 002  | INVALID-SUB           | Illegal subscriber                                  |
| 003  | ABSENT-SUB            | Unidentified subscriber.                            |
| 004  | HANDSET-ERR           | Illegal equipment                                   |
| 005  | BARRED                | SMS is prohibited                                   |
| 006  | HANDSET-ERR           | MS does not support SMS                             |
| 007  | HANDSET-ERR           | MS receiving error                                  |
| 008  | NET-ERR               | Facility not supported.                             |
| 009  | MEMEXEC               | Handset memory full                                 |
| 010  | ABSENT-SUB            | Absent subscriber                                   |
| 011  | FAILED                | SMSC system failure                                 |
| 012  | NET-ERR               | Gateway mobile switching error                      |
| 013  | MOB-OFF               | Mobile handset switched off                         |
| 014  | FAILED                | SMS undelivered due to roaming limitation           |
| 015  | INVALID-SUB           | Unidentified subscriber                             |
| 016  | HANDSET-BUSY          | Subscriber is busy.                                 |
| 017  | NET-ERR               | Resource cannot be used at GMSC level               |
| 018  | SERIES-BLK            | Series blocked                                      |
| 019  | NET-ERR               | Submission error or invalid input data              |
| 020  | BARRED                | CUG reject                                          |
| 021  | EXPIRED               | SMS timeout                                         |
| 034  | UNDELIV               | Unknown Error                                       |
| 045  | FAILED                | Unknown Error                                       |
| 099  | UNDELIV               | Unknown Error                                       |
| 400  | SERIES-BLOCK          | Series has been temporary / permanently blocked.    |
| 401  | NO-CREDITS            | Credit exhausted.                                   |
| 402  | NO-ACCOUNT            | Invalid account.                                    |
| 404  | INV-NUMBER            | Invalid destination number                          |
| 405  | SERVER-ERR            | ESME client error                                   |
| 406  | SERVER-ERR            | ESME client error                                   |
| 407  | SPAM                  | Sent illigal content                                |
| 408  | DNDNUMB               | Number registered in dnd database.                  |
| 450  | BLACKLST              | Number blocklisted to receive messages              |
| 451  | SNDR-NOT-ALLOTED      | Sender Id been blocked                              |
| 452  | TEMPLATE-NOT-FOUND    | No matching templates                               |
| 453  | INV-TEMPLATE          | Message rejected as template not allotted for ESME  |
| 454  | INV-SENDER            | Message rejected as sender id not allotted for ESME |
| 455  | NOT-OPTIN             | Message rejected as number not in optin list        |
| 456  | OPTOUT-REJ            | Rejected as number optout to receive messages       |
| 457  | PROMO-TMOUT           | Promotional time exceeded                           |
| 458  | REJECTED              | Unknown Error                                       |
| 459  | NOTALLOWED            | Country not allowed to send sms                     |
| 460  | DUPLICATE             | Same content sent                                   |
| 461  | UNDELIV               | Unknown Error                                       |
| 778  | REJ-MULTIPART         | All message parts are not delivrd to handset        |
| 777  | DLT-REJECTED          | Invalid Sender-Id or Invalid Template               |
| 780  | DLT-INV-TMID          | Invalid DLT telemarketer Id                         |
| 781  | DLT-INV-ENTITY        | Invalid Entity DLT Id                               |
| 782  | DLT-INV-TM-ID         | Invalid DLT Template Id                             |
| 783  | DLT-TM-VAR-EXECEED    | Template variable exceeded 30 chars                 |
| 784  | DLT-ENTITY-NOT-FOUND  | Entity Id not found                                 |
| 785  | DLT-TM-BLACKLST       | Template Id blacklisted                             |
| 786  | DLT-ENTITY-BLACKLST   | Entity Id blacklisted                               |
| 787  | DLT-HEADER-INACTIVE   | Sender Inactive                                     |
| 788  | DLT-TM-INACTIVE       | Template is Inactive                                |
| 789  | DLT-SENDER-NOT-REG-TM | Sender not registered for template                  |
