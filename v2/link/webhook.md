# WEBHOOK

The WEBHOOK Push API sends the report of the smart link visits to the client’s URL in `GET` method.

To request such reports, you need to mention URL with any below mentioned replacable variables.

####  REPLACEABLE PARAMETERS

| Name     | Description |
|----------|--------------|
| id | Smart link visit Id generated by us|
| link_id | Smart link Id|
| user_agent | User agent fo the browser |
| browser | Name of web browser `Ex:` chrome, mozilla..|
| browser_version | Version of the web browser `Ex:` 3.9.1|
| platform | Platform of the device `Ex:` Android, Ubuntu, iOS, Windows...|
| device_type | Type of the device `Ex:` desktop, smartphone... |
| device_brand | Brand name of the device  `Ex:` Samsung, OPPO..|
| country | Full name of the country `Ex:` India |
| country_code | Country code  `Ex:` IN|
| region | Region name it will provide `Ex:` Karnataka, Tamil Nadu...|
| city | City name it will provide `Ex:` Bangalore, Mumbai...|
| mobile | Mobile number with country code `Ex:` 891952XXXX|
| created_at | Visited Date in date format (yyyy-mm-dd H:i:s)|

All params should be enclosed between `{}` braces. `Ex:` `{region}`, `{browser}`, `{mobile}`

#### Example Url

```curl
    https://www.domain.com/ack/receive?location={region}&mobile={mobile}&id={id}
```

- The method used for sending the webhook report onto the client’s URL is `GET`.

- The same replacement variables can be used for long url while creating smart link.