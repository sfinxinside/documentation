# Third party logistics - API integration guide

This document describes the different steps that are needed to set up integration as a 3PL partner that wants to integrate Sfinx into the existing logistics workflows.  

For the integration and set up of everything, we recommend to use the UAT (User Acceptance Test) environment of Sfinx.  After a review of the solution, an integration can be promoted to our production environment, by adjusting the API endpoints, credentials and login endpoints.

The following steps have to be done and will be described in more detail:

- [Third party logistics - API integration guide](#third-party-logistics---api-integration-guide)
  - [Register an account on the Sfinx environment](#register-an-account-on-the-sfinx-environment)
  - [Register on the Sfinx API development portal (optional)](#register-on-the-sfinx-api-development-portal-optional)
  - [Subscribe to the API product](#subscribe-to-the-api-product)
    - [Set up Postman for the oAuth authentication](#set-up-postman-for-the-oauth-authentication)

## Register an account on the Sfinx environment

Follow the right steps on [the onboarding page](../portal/registration.md) to create your user name and password on the Sfinx platform.

> **Recommendation**: when not implementing the API calls on behalf of the end user (but as a trusted party), we recommend to also create a 'service account' for which the credentials can be used to make API calls.

## Register on the Sfinx API development portal (optional)

Follow the right steps on [the API developer portal page](../api/developer-portal-signup.md) to create your user name and password for the Sfinx API portal.

> **Warning**: the user name and password is a different one from the log on to the Sfinx environment.

## Subscribe to the API product

Also make sure to subscribe to the right product, as described [here](../api/developer-portal-subscribe-product.md).

> **Reminder**: Write down the Subscription key from the portal, as you will need it to make calls to the API.

### Set up Postman for the oAuth authentication

The easiest way to test the API, is by using [Postman](https://www.postman.com).  
You will need three specific secure values that are generated for you, in order to request API Access tokens:

- **Subscription key**: the key that was generated in the previous step
- **Client ID**: this is an id that identifies your (3PL) application as an API consumer
- **Client Secret**: this is the secret value that is linked with your API application

If you have these values, you can following the right steps to [set up Postman for your access token](../api/postman-request-access-token.md).

> **Summary**: if you successfully completed the previous steps, you are now able to securely call our API by using a secure access token.