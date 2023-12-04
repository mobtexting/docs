@if(isset($branding) && isset($branding->options) && isset($branding->options['docs.postman']))
[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/{collection})
@endif


- [Introduction](#)

    - [API Overview](/docs/{version})
    - [Authentication](/docs/{version}#content-authentication)
    - [Rate Limits](/docs/{version}#content-rate-limits)
    - [Status Code](/docs/{version}#content-http-status-codes)

- [Verify](#)

  - [Introduction](/docs/{version}/verify)
  - [Validate Token](/docs/{version}/verify/check)
  - [Search Token](/docs/{version}/verify/search)
  - [Cancel Token](/docs/{version}/verify/cancel)

- [Messaging](#)

  - [Introduction](/docs/{version}/sms)
  - [SMS Length Summary](/docs/{version}/sms/length-summary)
  - [Send Notification](/docs/{version}/sms/sendsms)
  - [Send Template Notification](/docs/{version}/sms/template)
  - [Post](/docs/{version}/sms/post)
  - [Webhook](/docs/{version}/sms/webhook)
  - [Pull DLR](/docs/{version}/sms/pull-dlr)
  - [View Senders](/docs/{version}/sms/senders)
  - [Create Sender](/docs/{version}/sms/senders/create)
  - [Show Sender](/docs/{version}/sms/senders/show)
  - [Edit Sender](/docs/{version}/sms/senders/edit)
  - [Delete Sender](/docs/{version}/sms/senders/delete)
  - [View Templates](/docs/{version}/sms/templates)
  - [Create Template](/docs/{version}/sms/templates/create)
  - [Show Template](/docs/{version}/sms/templates/show)
  - [Edit Template](/docs/{version}/sms/templates/edit)
  - [Delete Template](/docs/{version}/sms/templates/delete)
  - [Unsubscribers](/docs/{version}/sms/suppressions/unsubscribers)
  - [Template Blocklist](/docs/{version}/sms/suppressions/templates)
  - [Pricing List](/docs/{version}/sms/pricing)
  <!-- [Service Usage](/docs/{version}/sms/usage) -->

- [SMPP](#)

  - [Gateway](/docs/{version}/sms/smpp)
  - [Error Codes](/docs/{version}/sms/smpp#content-delivery-reports)

- [Whatsapp](#)

  - [Introduction](/docs/{version}/whatsapp)
  - [Send Notification](/docs/{version}/whatsapp/send-message)
  - [Send Template Notification](/docs/{version}/whatsapp/template)
  - [Status Info](/docs/{version}/whatsapp/status)
  - [Webhook](/docs/{version}/whatsapp/webhooks)
  - [Pull DLR](/docs/{version}/whatsapp/pull-status)
  - [Optout](/docs/{version}/whatsapp/optout)
  - [Pricing List](/docs/{version}/whatsapp/pricing)
  - [Templates](/docs/{version}/whatsapp/templates)
  - [Unsubscribers](/docs/{version}/whatsapp/suppressions/unsubscribers)

- [RCS](#)

  - [Introduction](/docs/{version}/rcs)
  - [Send Notification](/docs/{version}/rcs/send-message)
  - [Send Template Notification](/docs/{version}/rcs/send-template)
  - [Status Info](/docs/{version}/rcs/status)
  - [Webhook](/docs/{version}/rcs/webhooks)
  - [Pull DLR](/docs/{version}/rcs/pull-status)
  - [Optout](/docs/{version}/rcs/optout)
  - [Pricing List](/docs/{version}/rcs/pricing)
  - [Template](/docs/{version}/rcs/template)
  - [Unsubscribers](/docs/{version}/rcs/suppressions/unsubscribers)

- [Engage (Voice)](#)

  - [Introduction](/docs/{version}/voice)
  - [Click2Call/Number Masking](/docs/{version}/voice/c2c)
  - [Outgoing Call](/docs/{version}/reach/call)
  - [Text2Speech API](/docs/{version}/reach/tts)
  - [Upload Sound File](/docs/{version}/voice/sounds)
  - [Call Logs](/docs/{version}/voice/logs)
  - [Call Recordings](/docs/{version}/voice/logs#content-recordings-report)
  - [Call Status](/docs/{version}/reach/status)
  - [Webhook](/docs/{version}/reach/webhook)
  - [Pricing List](/docs/{version}/voice/pricing)
  - [Unsubscribers](/docs/{version}/reach/suppressions/unsubscribers)
  - [VoiceId List](/docs/{version}/voice/voices)

- [Link](#)

  - [View Links](/docs/{version}/link)
  - [Create Link](/docs/{version}/link/create)
  - [Edit Link](/docs/{version}/link/edit)
  - [Delete Link](/docs/{version}/link/delete)
  - [Show](/docs/{version}/link/show)
  - [Visits](/docs/{version}/link/visits)
  - [Webhook](/docs/{version}/link/webhook)

- [Studio](#)

  - [Introduction](/docs/{version}/studio)

- [Developers](#)

  - [Webhooks](/docs/{version}/webhook)
  - [Subscriptions](/docs/{version}/subscriptions)
  - [Events List](/docs/{version}/event)
