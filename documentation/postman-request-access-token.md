# Request an access token with Postman

> **Warning** 
> 
> Please contact the Sfinx team in order to receive a client id and client secret if you don't have it on hand. You need this in order to gain access to the Sfinx APIs.

* Open Postman
* Create a new Collection
* Go to the Variables tab of the newly created collection
    - Create a variable for the client id 
    - Create a variable for the client secret
    - Click Save
* Go to the Authorization tab of the newly created collection
    - Select OAuth2.0
    - Go to the Configure New Token Section (Configuration Options tab)
        * Token name: name of your choice
        * Grant type: **Auhtorization Code**
        * Callback URL: **https://oauth.pstmn.io/v1/callback**
        * Auth URL: see environment specific *Auth URL* setting below
        * Access Token URL: see environment specific *Access Token URL* setting below
        * Client ID: reference the client id variable
        * Client Secret: reference the client secret variable
        * Scope: see environment specific *Scope* setting below
    - Click Save
    - Click Get New Access Token
    - Provide your Sfinx credentials (or sign up first) and login
    - Click Use Token

Please note you can use this token to make calls from elsewhere (e.g. the Sfinx developer portal).

![Postman OAuth2.0](./../media/postman-oauth.png)

## User acceptance test environment

| Setting                 | Value                                                                                                          |
|-------------------------|----------------------------------------------------------------------------------------------------------------|
| Auth URL                | `https://sfinxuatb2c.b2clogin.com/sfinxuatb2c.onmicrosoft.com/oauth2/v2.0/authorize?p=b2c_1_signup_sfinx_user` |
| Access Token URL        | `https://sfinxuatb2c.b2clogin.com/sfinxuatb2c.onmicrosoft.com/oauth2/v2.0/token?p=b2c_1_signup_sfinx_user`     |
| Scope                   | `https://sfinxuatb2c.onmicrosoft.com/backend-api/Lock.OpenClose`                                               |
