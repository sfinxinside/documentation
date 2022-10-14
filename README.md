# Sfinx documentation

## Backend API

> **Warning**
> The current release of the API is just mocked up and is subject to many changes to come.  

Important links

- [Open API spec](https://weu-sfinx-dev-apim.azure-api.net/backend/api/v1/swagger.json)
- [Registration page](https://sfinxdevb2c.b2clogin.com/sfinxdevb2c.onmicrosoft.com/b2c_1_signup_sfinx_user/oauth2/v2.0/authorize?client_id=55157e1e-57b6-477a-8ab2-cba11cf5f257&redirect_uri=https%3A%2F%2Flocalhost%3A7127%2Fsignin-oidc&response_type=code%20id_token&scope=openid%20profile%20https%3A%2F%2Fsfinxdevb2c.onmicrosoft.com%2Fbackend-api%2FLock.OpenClose&response_mode=form_post&nonce=638013535346800600.MTQ0ZjIwODItN2UwZS00ZDE1LTliY2YtNDEyMjk4MmMxMDgzYmI3NGJiYzctYmJjOS00ODRhLTg5OWMtYjBlYjdmODliNzlm&state=CfDJ8M2tU35z5CFLpeQKl9vupCQmfchPS1E18UDYvKQrXKzU2UJemjg13wpcDwuqupBWZqSGd2Hp_nd_GBd-cdftmC0VS3TbJOVglxpm8HnvzPs0Fnjd_r_j2zAYH_b5HnG_QEoFxqR3rsz5O-2b-T9f7UhnuJDGSyKda8oxzkH3UQNg-h3gE8U8m4OgKTuG_K2vHD6gYoF11ACZYNuveRN7xaAl9htHKPDMyMNRc95VMsSc3BGgd8DKTe3-XWeQhlcfp4SRSaR7eRo0mi6slCiQ1v7BulnimXKWY5txA7FsTcig)

### Authentication

In order to call the API in Azure API Management, a user has to pass a valid JWT token, obtained from our Active Directory B2C. There we currently have the user-name / password authentication enabled, but in the future we can open for other identity providers , such as Twitter, Facebook, but also custom OpenId providers, such as itsme.
This section explains how to obtain such a token, with the different client tools.

### Obtain a valid JWT token by using Postman

To use the API, you have to request a client secret to your contact person at Sfinx.  You will need this, to gain access to the API.  Currently we only provide access to our dev environment, which hosts a mocked up version of the API.

**Parameters for dev environment**

| Field                   | Description                                     | Dev                                                                                                        |
|-------------------------|-------------------------------------------------|------------------------------------------------------------------------------------------------------------|
| Auth URL                | The Authorization URL for the actual user flow  | `https://sfinxdevb2c.b2clogin.com/sfinxdevb2c.onmicrosoft.com/B2C_1_signup_sfinx_user/oauth2/v2.0/authorize` |
| Access Token URL        | The URL of AD B2C where tokens will be provided | `https://sfinxdevb2c.b2clogin.com/sfinxdevb2c.onmicrosoft.com/B2C_1_signup_sfinx_user/oauth2/v2.0/token`     |
| Client ID               | A client specific generated id       |                                                                         |
| Client Secret           | A client specific generated secret                |                                                                                                            |
| Scope                   | The requested access and operations to the API  | `https://sfinxdevb2c.onmicrosoft.com/backend-api/Lock.OpenClose`                                             |
| Authorize using browser | Yes                                             |                                                                                                            |

![Postman](./media/postman-oauth.png)