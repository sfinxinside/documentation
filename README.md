# Sfinx documentation

## Sfinx developer portal

All Sfinx APIs are exposed through the Sfinx developer portal: https://developer.sfinxinside.com

At the time of this writing, there is a Sfinx user acceptance test environment available for third parties in order to start integrating with the Sfinx backend.

Please sign up to the sfinx developer portal to get access to the Sfinx APIs to develop your scenario. Click [here](./documentation/developer-portal-signup.md) for more information on how to sign up to the Sfinx developer portal.

## Subscribe to a Sfinx product

Once signed in to the Sfinx developer portal, you can get a list of all Sfinx products and APIs available for you. In order to consume an API, you need to subscribe to the product that offers the desired API. Click [here](./documentation/developer-portal-subscribe-product.md) for more information on how to subscribe for a Sfinx product through the developer portal.

## Call an API through the Sfinx developer portal

Click [here](./documentation/developer-portal-make-api-call.md) for more information on how to make an API call through the Sfinx developer portal.

## Authentication

In order to call the API in Azure API Management, a user has to pass a valid JWT token, obtained from our Active Directory B2C. There we currently have the user-name / password authentication enabled, but in the future we can open for other identity providers , such as Twitter, Facebook, but also custom OpenId providers, such as itsme.

Click [here](./documentation/postman-request-access-token.md) for more information on how to request an access token with Postman.
