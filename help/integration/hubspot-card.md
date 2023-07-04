# MOBtexting SMS With Hubspot Integration

Our platform allows you to seemingly integrate Hubspot crm.
Follow the steps below for integration guide:

### 1. Create Client 

In order to integrate hubspot crm with our system a client app needs to be created from the hubspot panel.

Visit this url: <https://app.hubspot.com/signup/developers> to create client.

<!-- ![alt text](/images/docs/integrations/hubspot1.png) -->

Fill the following details:

App Name : AppName

Authorized redirect URIs: {domain}/integration/oauth/hubspot


<!-- ![alt text](/images/docs/integrations/hubspot2.png) -->

and click on save button.

<!-- ![alt text](/images/docs/integrations/hubspot3.png) -->

You'll receive `App_id`, `client_id` and `client_secret`.

### 2. Obtain grant token code

Hit this url on browser to obtain grant token code (replace `(client_id)` with client_id you obtained):

<https://app.hubspot.com/oauth/authorize?client_id=(client_id)&scope=contacts&access_type=offline&response_type=code&approval_prompt=auto&redirect_uri={domain}/integration/oauth/hubspot/>


### 3. Generate Refresh Token

To generate refresh token:
Make a POST request with the following URL.

https://api.hubapi.com/oauth/v1/token

#### REQUEST PARAMETERS

| Name          | Descriptions                                           |
| ------------- | ------------------------------------------------------ |
| grant_type    | Enter the value as "authorization_code"                |
| client_id     | Specify client-id obtained from the connected app.     |
| client_secret | Specify client-secret obtained from the connected app. |
| redirect_uri  | {domain}/integration/oauth/hubspot                |
| code          | Enter the grant token generated from previous step.    |

You'll receive `refresh_token`.

### 4. Create Card API for SMS Plugin

Once you created app in developer account you can get `APP_Id` and `Developer_api_key`.

<!-- ![alt text](/images/docs/integrations/hubspot4.png) -->

https://api.hubapi.com/crm/v3/extensions/cards/(app_id)hapikey=(developer_api_key)

Make POST request with this data the following URl. This card will create your hubspot account.

    `['fetch' => 
        ['objectTypes' =>  [0 => 
            [ 'name' => 'contacts',
                'propertiesToSend' => 
                [                                
                ],
            ],
        ],
        'targetUrl' => (target_url),
        ],
        'display' => (object)[ ],
        'title' => 'MOBtexting SMS',
        'actions' => (object)[ ],
    ]
    `    
`targetUrl : {domain}/api/v2/integration/hubspot/targeturl`

This TargetUrl will call primary action function.

    `'primaryAction' => 
    array (
    'type' => 'IFRAME',
    'width' => 890,
    'height' => 748,
    'uri' => "(iframe_uri)",
    'label' => 'Send SMS',
    'associatedObjectProperties' => 
    array ('phone', 'firstname', 'lastname', 'email', 'hs_object_id'),
    )`
   
 `iframe_uri : {domain}/iframe/hubspot/`

    
This Primary Action will open iframe option with user `phone` number, `name` and `email`.


### 4. Setting Flow in MOBtexting

Login with `mobtexting account` and click on `_Developers` option on navbar and select `_integrations'.
On right side click `Create` button and choose `Hubspot Card`.
    
<!-- ![alt text](/images/docs/integrations/hubspot5.png) -->

It will ask to choose your account for install. Once you installed can see `MOBtexting SMS` Card on your `HUBSPOT` account.


<!-- ![alt text](/images/docs/integrations/hubspot6.png) -->





