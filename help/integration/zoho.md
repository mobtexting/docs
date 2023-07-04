# Zoho Integration

Our platform allows you to seemingly integrate zoho crm.
Follow the steps below for integration guide:

### 1. Create Client

In order to integrate zoho crm with our system a client app needs to be created from the zoho panel.

Visit this url: <https://accounts.zoho.com/developerconsole> to create client.

![alt text](/images/docs/integrations/zoho1.png)

Fill the following details when asked:

Client Name : myclient

Client Domain: mydomain.com

Authorized redirect URIs: {domain}/api/v2/integration/zoho/code

![alt text](/images/docs/integrations/zoho2.png)

and click on create button

![alt text](/images/docs/integrations/zoho3.png)

You'll receive `client_id` and `client_secret`.

### 2. Obtain grant token code

Hit this url in browser to obtain grant token code (replace `(client_id)` with client_id you obtained):

<https://accounts.zoho.com/oauth/v2/auth?scope=ZohoCRM.modules.all&client_id=(client_id)&response_type=code&access_type=offline&redirect_uri={domain}/api/v2/integration/zoho/code&prompt=consent>

### 3. Generate Refresh Token

To generate refresh token:
Make a POST request with the following URL.

https://accounts.zoho.com/oauth/v2/token

#### REQUEST PARAMETERS

| Name          | Descriptions                                           |
| ------------- | ------------------------------------------------------ |
| grant_type    | Enter the value as "authorization_code"                |
| client_id     | Specify client-id obtained from the connected app.     |
| client_secret | Specify client-secret obtained from the connected app. |
| redirect_uri  | {domain}/api/v2/integration/zoho/code                  |
| code          | Enter the grant token generated from previous step.    |

You'll receive `refresh_token`.

### 4. Setting Flow in MOBtexting

![alt text](/images/docs/integrations/zoho4.png)

Fill the details you obtained in previous steps and click save.

![alt text](/images/docs/integrations/zoho5.png)
