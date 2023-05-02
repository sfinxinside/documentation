# 3PL integration workflow

- [3PL integration workflow](#3pl-integration-workflow)
  - [Customer setup](#customer-setup)
    - [Register users with their invitation codes](#register-users-with-their-invitation-codes)
    - [Users should install and link their locks](#users-should-install-and-link-their-locks)
  - [Organization members setup](#organization-members-setup)
    - [Add members to an organization](#add-members-to-an-organization)
  - [Plan a delivery and generate keys](#plan-a-delivery-and-generate-keys)
    - [Assign keys for locks to a member of the organization](#assign-keys-for-locks-to-a-member-of-the-organization)
  - [Open a lock, while delivering the home service](#open-a-lock-while-delivering-the-home-service)

## Customer setup

Customer of the organization should be set up for Sfinx.  This is described in this section:

### Register users with their invitation codes

When an organization wants to pre-register its customers, a common requirement, is to link the customer number (or delivery address reference...) to that specific customer, so that the customer can be referenced with a reference, known by the organization. 

In order to achieve this, please follow the [following document](../orgs/invitations.md).

### Users should install and link their locks

When the users click their registration link, they will be redirected to the on boarding wizard.  This wizard is described in the [following page](../portal/invitation.md)

## Organization members setup

An organization can register and set up users to become a member of the organization.  This is typically required for employees, drivers, nurses, cleaning personnel, etc...  This section describes how to do this.

### Add members to an organization

Adding members to an organization is easy and described in [this guide](../orgs/members.md).
By doing so, the drivers, nurses, employees, etc will be linked to your organization.

## Plan a delivery and generate keys

When users are registered and linked to the organization, it is possible to request and assign keys to members of your organization.

For this, the following steps should be executed:

### Assign keys for locks to a member of the organization

The API operation `POST /organizations/{{SfinxOrganizationId}}/keys` should be called, with the following JSON body content:

```json
{
    "lockReference": "ReferenceKnownByOrg",
    "memberEmailAddress": "driver@email.com",
    "keyRequest": {
        "oneTimeKey": true,
        "label": "OrganizationName"
    }
}
```

This will generate a key (if allowed by the lock owner) for the lock that is linked to the correct reference in the organization.  That key will be assigned to the right user (based on the given e-mail address).  Obviously, all data should be matching.

## Open a lock, while delivering the home service

_This will be documented soon._