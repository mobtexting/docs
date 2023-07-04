# Opencart Plugin

Integrate your account with this plug-in to send order status and shipment details to your customers. Keep your admin informed on checkouts, new registrations and orders via SMS.

## Purpose

When an order is placed, shipped or status changed in opencart you can confirm with your customer and/or store admin via a text message sent directly to their mobile phone.

## Features

- Send SMS to customers and admin on new orders
- Send SMS to customers and admin on status updates
- Send SMS using your brand or domain as the Sender ID (Messages appear from ‘YourCompany’).
- Update store admin when a customer registers or checkouts.

## Configuration Process:

- Download the opencart_plugin, and place all the sub folders from opencart folder in the root-> upload folder
- Log in as an administrator and navigate to the Extension->module page.

![alt text](/images/docs/opencart1.png)

- Select Install against our SMS module
- Once install select Edit against our SMS module.
- Under API information tab, enter the sender ID and token details.

![alt text](/images/docs/opencart2.png)

- Under New orders tab, draft a message that needs to be sent to the customer when a new order is placed. You can customize your SMS using variable parameters within @{{1}}
- Under Orders Status tab, draft a messages that needs to be sent to the customer on each status change. You can customize your SMS using variable parameters within @{{2}}
- Under Additional Options tab, select if or not message has to be sent to the store admin, store admin number and the conditions when it has to be sent
- Click Save.

## Flow:

- Whenever a new order is placed from the store, customer and admin (if configured) receives an SMS with the current status.
- Also on every status change customer and admin if configured receives an SMS.
- On configuration Admin will also receive an SMS when a new customer is registered or customer checkout.
- To view the status of the SMS sent, login to our SMS panel and check the sent items tab for the last 3 days update and download reports for the date beyond.

#### Links for further reference

[Click here](http://docs.opencart.com/en-gb/extension/installer)

For any further help on integration with respect to our application kindly contact our support team.
