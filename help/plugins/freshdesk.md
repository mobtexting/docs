# Freshdesk Plugin

MOBtexting integration for Freshdesk allows customers to get notified through SMS on ticket updates:

Key Features:

- SMS notification on ticket creation.
- SMS notification on ticket status change.
- SMS notification on new reply/public note on a ticket.
- Easy configuration through API.

Follow the guide to learn how to use:

### 1. Obtain access token

Please follow this guide for getting your access token:
[Generating Access Token](/docs/{version}/access_token)

### 2. Install

Goto your Freshdesk settings and search for Apps

In Apps search for MOBtexting and click on install.

You'll be asked few details.
Please enter the details accordingly.

![alt text](https://mobtexting-assets.s3-ap-southeast-1.amazonaws.com/images/plugins/Screenshot+from+2020-02-07+15-11-41.png)

![alt text](https://mobtexting-assets.s3-ap-southeast-1.amazonaws.com/images/plugins/Screenshot+from+2020-02-07+15-13-18.png)

Finally click on install.

### 2. Replaceble variables

You can use replacable variables for messages.

For example: Dear customer, your ticket id is {id}

{id} will be replaced by the corresponding ticket id

Available variables are:

id

subject

description_text

status

priority
