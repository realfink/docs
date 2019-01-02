---
title: Retrieve Users with the Get Users by Email Endpoint 
description: Learn how to retrieve lists of users using the get-users-by-email endpoint. 
topics:
  - users
  - user-management
  - search
contentType: how-to 
useCase:
  - manage-users
---
# Retrieve Users with the Get Users by Email Endpoint 

The [`GET /api/v2/users-by-email` endpoint](/api/management/v2#!/Users_By_Email/get_users_by_email) allows you to search for users using their email addresses. The search looks for an exact match to the provided email address.

## Before you start

To use the user search endpoints, you'll need to obtain a valid [Access Token](/api/management/v2/tokens) and provide it in the header of your call (replace the `YOUR_MGMT_API_ACCESS_TOKEN` placeholder value).

## Syntax

*Required Scopes*: `read:users`

```har
{
    "method": "GET",
    "url": "https://${account.namespace}/api/v2/users-by-email?email=USER_EMAIL_ADDRESS",
    "headers": [{
        "name": "Authorization",
        "value": "Bearer YOUR_MGMT_API_ACCESS_TOKEN"
    }]
}
```

### Sample results 

```json
[
  {
    "email": "john.doe@gmail.com",
    "email_verified": false,
    "username": "johndoe",
    "phone_number": "+199999999999999",
    "phone_verified": false,
    "user_id": "usr_5457edea1b8f33391a000004",
    "created_at": "",
    "updated_at": "",
    "identities": [
      {
        "connection": "Initial-Connection",
        "user_id": "5457edea1b8f22891a000004",
        "provider": "auth0",
        "isSocial": false
      }
    ],
    "app_metadata": {},
    "user_metadata": {},
    "picture": "",
    "name": "",
    "nickname": "",
    "multifactor": [
      ""
    ],
    "last_ip": "",
    "last_login": "",
    "logins_count": 0,
    "blocked": false,
    "given_name": "",
    "family_name": ""
  }
]
```

## Limitations

The Users by Email endpoint is immediately consistent, and as such, we recommend that you use this endpoint for:

* User searches run during the authentication process 
* User searches run as part of the account linking process.

## Keep reading

* 