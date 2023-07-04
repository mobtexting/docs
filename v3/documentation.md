@if(isset($branding) && isset($branding->options) && isset($branding->options['docs.postman']))
[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/{collection})
@endif

- [Introduction](#)

  - [Authentication](/docs/{version})
  - [Rate Limits](/docs/{version}#content-rate-limits)
  - [Status Code](/docs/{version}#content-http-status-codes)

<!--
- Account

  - [Check Account Balance](/docs/{version}/account/balance)
  - [Adding Credits](/docs/{version}/account/add-credits)
-->

- [Messaging](#)

  - [Introduction](/docs/v2/sms)
  - [SMS Length Summary](/docs/v2/sms/length-summary)
  - [Send Notification](/docs/v2/sms/send)
  - [Send Template Notification](/docs/v2/sms/template)
  - [Webhook](/docs/v2/sms/webhook)
  - [Pull DLR](/docs/v2/sms/pull-dlr)
  - [Optout](/docs/v2/sms/optout)
  - [View Senders](/docs/v2/sms/senders)
  - [Show Sender](/docs/v2/sms/senders/show)
  - [Create Sender](/docs/v2/sms/senders/create)
  - [Edit Sender](/docs/v2/sms/senders/edit)
  - [Delete Sender](/docs/v2/sms/senders/delete)
  - [View Templates](/docs/v2/sms/templates)
  - [Show Template](/docs/v2/sms/templates/show)
  - [Create Template](/docs/v2/sms/templates/create)
  - [Edit Template](/docs/v2/sms/templates/edit)
  - [Delete Template](/docs/v2/sms/templates/delete)
  - [Pricing List](/docs/v2/sms/pricing)
  <!-- [Service Usage](/docs/v2/sms/usage) -->

- [SMPP](#)

  - [Gateway](/docs/v2/sms/smpp)
  - [Error Codes](/docs/v2/sms/smpp#content-delivery-reports)

- [Verify](#)

  - [Introduction](/docs/v2/verify)
  - [Check](/docs/v2/verify/check)
  - [Search](/docs/v2/verify/search)
  - [Cancel](/docs/v2/verify/cancel)

- [Engage (Voice)](#)

  - [Introduction](/docs/v2/voice)
  - [Click2Call/Number Masking](/docs/v2/voice/c2c)
  - [Outgoing Call](/docs/v2/reach/call)
  - [Text2Speech API](/docs/v2/reach/tts)
  - [Upload Sound File](/docs/v2/reach)
  - [Call Logs](/docs/v2/voice/logs)
  - [Call Recordings](/docs/v2/voice/logs#content-recordings-report)
  - [Call Status](/docs/v2/reach/status)
  - [Webhook](/docs/v2/reach/webhook)
  - [Pricing List](/docs/v2/voice/pricing)

- [Whatsapp](#)

  - [Introduction](/docs/{version}/whatsapp)
  - [Send a message](/docs/{version}/whatsapp/send-message)
  - [Status Info](/docs/{version}/whatsapp/status)
  - [Webhook](/docs/{version}/whatsapp/webhooks)
  - [Pull DLR](/docs/{version}/whatsapp/pull-status)
  - [Optout](/docs/{version}/whatsapp/optout)
  - [Pricing List](/docs/{version}/whatsapp/pricing)
  - [Templates](/docs/{version}/whatsapp/templates)

<!--
- MIP

  - [Introduction](/docs/v2/mip)
  - [Send Notification](/docs/v2/mip/send-message)
  - [Status Info](/docs/v2/mip/status)
  - [Webhook](/docs/v2/mip/webhooks)
  - [Pull DLR](/docs/v2/mip/pull-status)
-->

- [RCS](#)

  - [Introduction](/docs/v2/rcs)
  - [Send Notification](/docs/v2/rcs/send-message)
  - [Status Info](/docs/v2/rcs/status)
  - [Webhook](/docs/v2/rcs/webhooks)
  - [Pull DLR](/docs/v2/rcs/pull-status)
  - [Optout](/docs/v2/rcs/optout)
  - [Pricing List](/docs/v2/rcs/pricing)

- [Link](#)

  - [View Links](/docs/v2/link)
  - [Create Link](/docs/v2/link/create)
  - [Edit Link](/docs/v2/link/edit)
  - [Delete Link](/docs/v2/link/delete)
  - [Show](/docs/v2/link/show)
  - [Visits](/docs/v2/link/visits)
  - [Webhook](/docs/v2/link/webhook)

<!--
- Number Lookup

  - [Verify](/docs/v2/lookup/verify)
    -->

- [Developers](#)

  - [Webhooks](/docs/v2/webhook)
  - [Subscriptions](/docs/v2/subscriptions)
