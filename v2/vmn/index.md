# Interact Flow

### REPLACEABLE VARIABLES

We generate some of the variables in flow process, those can used to pass the information your system.

Varibles consist of alphanumeric characters and underscores, should always start with a letter, and do not have any kind of leading sigil (that is, they look like var_name, not \$var_name).

All variables should be enclosed between a set of double curly braces `@{{}}` braces. ex: `@{{to}}`
You can access the Array of the variables with `.` dot notation. Example if you want to access the caller name information from caller object `@{{caller.name}}`

### Freshdesk FLOW VARIABLES

| Name                                   | Scope | Description                                                   |
| -------------------------------------- | ----- | ------------------------------------------------------------- |
| freshdesk_ticket.status                | step  | Freshdesk Ticket Status                                       |
| freshdesk_ticket.subject               | step  | Freshdesk Ticket Subject                                      |
| freshdesk_ticket.description           | step  | Freshdesk Ticket Description                                  |
| freshdesk_ticket.priority              | step  | Freshdesk Ticket Priority                                     |
| freshdesk_ticket.type                  | step  | Freshdesk Ticket Type                                         |
| freshdesk_ticket.created_at            | step  | Freshdesk Ticket creation Date                                |
| freshdesk_ticket.fr_due_by             | step  | When the first response is due                                |
| freshdesk_ticket.due_by                | step  | When the ticket is due to be resolved                         |
| freshdesk_ticket.requester.name        | step  | Freshdesk Ticket Requester Name                               |
| freshdesk_ticket.requester.email       | step  | Freshdesk Ticket Requester Email                              |
| freshdesk_ticket.requester.phone       | step  | Freshdesk Ticket Requester Phone Number                       |
| freshdesk_ticket.requester.mobile      | step  | Freshdesk Ticket Requester Mobile Number                      |
| freshdesk_ticket.requester.status      | step  | Freshdesk Ticket Requester Status                             |
| freshdesk_ticket.assignee.occasional   | step  | Freshdesk Ticket Assignee Occasional Agent or Full time Agent |
| freshdesk_ticket.assignee.status       | step  | Freshdesk Ticket Assignee Status                              |
| freshdesk_ticket.assignee.email        | step  | Freshdesk Ticket Assignee Email                               |
| freshdesk_ticket.assignee.name         | step  | Freshdesk Ticket Assignee Name                                |
| freshdesk_ticket.assignee.phone        | step  | Freshdesk Ticket Assignee phone number                        |
| freshdesk_ticket.assignee.mobile       | step  | Freshdesk Ticket Assignee Mobile number                       |
| freshdesk_ticket.assignee.job_title    | step  | Freshdesk Ticket Assignee Job Title                           |
| freshdesk_ticket.assignee.ticket_scope | step  | Ticket permission of the Agent                                |

### Freshservice FLOW VARIABLES

| Name                                      | Scope | Description                                                      |
| ----------------------------------------- | ----- | ---------------------------------------------------------------- |
| freshservice_ticket.status                | step  | Freshservice Ticket Status                                       |
| freshservice_ticket.subject               | step  | Freshservice Ticket Subject                                      |
| freshservice_ticket.description           | step  | Freshservice Ticket Description                                  |
| freshservice_ticket.priority              | step  | Freshservice Ticket Priority                                     |
| freshservice_ticket.type                  | step  | Freshservice Ticket Type                                         |
| freshservice_ticket.created_at            | step  | Freshservice Ticket creation Date                                |
| freshservice_ticket.fr_due_by             | step  | When the first response is due                                   |
| freshservice_ticket.due_by                | step  | When the ticket is due to be resolved                            |
| freshservice_ticket.requester.first_name  | step  | Freshservice Ticket Requester First Name                         |
| freshservice_ticket.requester.last_name   | step  | Freshservice Ticket Requester Last Name                          |
| freshservice_ticket.requester.email       | step  | Freshservice Ticket Requester Email                              |
| freshservice_ticket.requester.phone       | step  | Freshservice Ticket Requester Phone Number                       |
| freshservice_ticket.requester.mobile      | step  | Freshservice Ticket Requester Mobile Number                      |
| freshservice_ticket.requester.status      | step  | Freshservice Ticket Requester Status                             |
| freshservice_ticket.assignee.occasional   | step  | Freshservice Ticket Assignee Occasional Agent or Full time Agent |
| freshservice_ticket.assignee.status       | step  | Freshservice Ticket Assignee Status                              |
| freshservice_ticket.assignee.email        | step  | Freshservice Ticket Assignee Email                               |
| freshservice_ticket.assignee.job_title    | step  | Freshservice Ticket Assignee Job Title                           |
| freshservice_ticket.assignee.ticket_scope | step  | Ticket permission of the agent                                   |
| freshservice_ticket.assignee.first_name   | step  | Freshservice Ticket Assignee First Name                          |
| freshservice_ticket.assignee.last_name    | step  | Freshservice Ticket Assignee Last Name                           |
| freshservice_ticket.assignee.phone        | step  | Freshservice Ticket Assignee phone number                        |
| freshservice_ticket.assignee.mobile       | step  | Freshservice Ticket Assignee Mobile number                       |

### Zendesk FLOW VARIABLES

| Name                                | Scope | Description                           |
| ----------------------------------- | ----- | ------------------------------------- |
| zendesk_ticket.status               | step  | Zendesk Ticket Status                 |
| zendesk_ticket.subject              | step  | Zendesk Ticket Subject                |
| zendesk_ticket.description          | step  | Zendesk Ticket Description            |
| zendesk_ticket.priority             | step  | Zendesk Ticket Priority               |
| zendesk_ticket.type                 | step  | Zendesk Ticket Type                   |
| zendesk_ticket.channel              | step  | Zendesk Ticket Channel                |
| zendesk_ticket.created_at           | step  | Zendesk Ticket creation Date          |
| zendesk_ticket.fr_due_by            | step  | When the first response is due        |
| zendesk_ticket.due_by               | step  | When the ticket is due to be resolved |
| zendesk_ticket.requester.name       | step  | Zendesk Ticket Requester Name         |
| zendesk_ticket.requester.email      | step  | Zendesk Ticket Requester Email        |
| zendesk_ticket.requester.phone      | step  | Zendesk Ticket Requester Phone Number |
| zendesk_ticket.requester.role       | step  | Zendesk Ticket Requester Role         |
| zendesk_ticket.requester.created_at | step  | Requester Created Date                |
| zendesk_ticket.requester.status     | step  | Zendesk Ticket Requester Status       |
| Zendesk_ticket.assignee.status      | step  | Zendesk Ticket Assignee Status        |
| Zendesk_ticket.assignee.email       | step  | Zendesk Ticket Assignee Email         |
| Zendesk_ticket.assignee.name        | step  | Zendesk Ticket Assignee Name          |
| Zendesk_ticket.assignee.phone       | step  | Zendesk Ticket Assignee phone number  |
| zendesk_ticket.assignee.role        | step  | Zendesk Ticket Assignee Role          |
| Zendesk_ticket.assignee.created_at  | step  | Assignee Created Date                 |

### Hubspot FLOW VARIABLES

| Name                       | Scope | Description                |
| -------------------------- | ----- | -------------------------- |
| hubspot_ticket.status      | step  | Hubspot Ticket Status      |
| hubspot_ticket.subject     | step  | Hubspot Ticket Subject     |
| hubspot_ticket.priority    | step  | Hubspot Ticket Priority    |
| hubspot_ticket.type        | step  | Hubspot Ticket Type        |
| hubspot_ticket.description | step  | Hubspot Ticket Description |

### Zohodesk FLOW VARIABLES

| Name                                  | Scope | Description                            |
| ------------------------------------- | ----- | -------------------------------------- |
| zohodesk_ticket.status                | step  | Zohodesk Ticket Status                 |
| zohodesk_ticket.statustype            | step  | Zohodesk Ticket Status Type            |
| zohodesk_ticket.subject               | step  | Zohodesk Ticket Subject                |
| zohodesk_ticket.ticketnumber          | step  | Zohodesk Ticketnumber                  |
| zohodesk_ticket.priority              | step  | Zohodesk Ticket Priority               |
| zohodesk_ticket.channel               | step  | Zohodesk Ticket Channel                |
| zohodesk_ticket.description           | step  | Zohodesk Ticket Description            |
| zohodesk_ticket.created_at            | step  | Zohodesk Ticket creation Date          |
| zohodesk_ticket.fr_due_by             | step  | When the first response is due         |
| zohodesk_ticket.due_date              | step  | When the ticket is due to be resolved  |
| zohodesk_ticket.classification        | step  | Zohodesk Ticket Classification         |
| zohodesk_ticket.requester.first_name  | step  | Zohodesk Ticket Requester First Name   |
| zohodesk_ticket.requester.last_name   | step  | Zohodesk Ticket Requester Last Name    |
| zohodesk_ticket.requester.email       | step  | Zohodesk Ticket Requester Email        |
| zohodesk_ticket.requester.phone       | step  | Zohodesk Ticket Requester Phone        |
| zohodesk_ticket.requester.country     | step  | Zohodesk Ticket Requester Country      |
| zohodesk_ticket.requester.state       | step  | Zohodesk Ticket Requester State        |
| zohodesk_ticket.requester.city        | step  | Zohodesk Ticket Requester city         |
| zohodesk_ticket.requester.zip         | step  | Zohodesk Ticket Requester Zip          |
| zohodesk_ticket.requester.description | step  | Zohodesk Ticket Requester Description  |
| zohodesk_ticket.requester.created_at  | step  | Requester Creation time                |
| zohodesk_ticket.requester.type        | step  | Zohodesk Requester Type                |
| zohodesk_ticket.requester.title       | step  | Zohodesk Requester Title               |
| Zohodesk_ticket.assignee.name         | step  | Zohodesk Ticket Assignee Name          |
| Zohodesk_ticket.assignee.first_name   | step  | Zohodesk Ticket Assignee First Name    |
| Zohodesk_ticket.assignee.last_name    | step  | Zohodesk Ticket Assignee Last Name     |
| Zohodesk_ticket.assignee.email        | step  | Zohodesk Ticket Assignee Email         |
| Zohodesk_ticket.assignee.phone        | step  | Zohodesk Ticket Assignee phone number  |
| zohodesk_ticket.assignee.mobile       | step  | Zohodesk Ticket Assignee Mobile number |
