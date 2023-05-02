# Invite organization members to on board 

Organizations can add users to their members, meaning they can reference the users and assign keys to them.  There are two roles defined: 

- `Member`: a regular user that is using keys to perform its job
- `Administrator`: a power user for the organization that can perform administrative tasks

## Workflow

1. The organization can pre-register members with their e-mail address.
2. Users should sign on with the same e-mail address as pre-registered.

> **Remark**: the registration url that should be sent to the customers to on board, is the following: https://portal.sfinxinside.com/organization/member

## Pre-register members

In order to pre-register members, there are two possibilities:

### Upload members in the portal

In the portal, when you are administrator of an organization, you can upload or add members in the portal.

1. Navigate to the organization dashboard.
2. Click on Users tab of the navigation.
3. Click the `Upload user invitations` button and provide your csv, containing the e-mail addresses, the reference of the customer (or address) and a personal message.

The CSV file should follow the pre-defined structure, and a sample file can be found [here](./files/members.csv).

The following fields are possible to add to the CSV file:

- `GivenName` : first name of the user.
- `FamilyName` : last name of the user.
- `Role` : Member, or Administrator (see above)
- `Email` : the e-mail address of the user.
- `Phone` : (optional) the phone number of the user.

> **Remark** : it is also possible to manually add members, by clicking the `Register member` button.

### Generate customer invitation codes through the API

Use the [Sfinx API portal](https://uat.developer.sfinxinside.com) to look for the Operation `POST /organizations/{organizationId}/members`.  This operation will pre-provision the users.
