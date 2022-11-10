# Auth Service

This service is responsible for authentication of users and to manage authentication methods.

## Routes

### GET `/auth/guest`

### GET `/auth/github`

### GET `/auth/microsoft`

This routes is used to authenticate a user with these providers:

- guest
- github
- microsoft

### GET `/auth/github/callback`

### GET `/auth/microsoft/callback`

It's the route that the provider will redirect the user after the authentication.

### GET `/auth/logout`

This route is used to logout the user.

### POST `/auth/ldap?name=<authName>`

### POST `/auth/basic?name=<authName>`

These routes are used to authenticate a user with ldap or basic auth.
In both cases the request body must contain the following fields:

#### Example

In this example we using the basic auth and the auth name is `authn-basic`.

```bash
auth/basic?name=authn-basic
```

```json
{
  "username": "username",
  "password": "password"
}
```

#### Response

```json
{
  "id": "krateo",
  "displayName": "krateo",
  "username": "krateo",
  "provider": "basic",
  "email": "krateo@krateo.io"
}
```

```cookie
krateoplatformops=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6ImtyYXRlbyIsImRpc3BsYXlOYW1lIjoia3JhdGVvIiwidXNlcm5hbWUiOiJrcmF0ZW8iLCJwcm92aWRlciI6ImJhc2ljIiwiZW1haWwiOiJrcmF0ZW9Aa3JhdGVvLmlvIiwiaWF0IjoxNjY4MDY3NDY1LCJleHAiOjQyNjAwNjc0NjUsImlzcyI6IjEzYjQ2NTkzZmU3MDRjNTc5NjZmZjQxZGNhOWRjNDhiIn0.Cp_vMDev5_S8hlD2UE2fBHl2jXLDUx-feRp5CZM_L-4; Max-Age=2592000; Domain=krateo.site; Path=/; Expires=Sat, 10 Dec 2022 08:04:25 GMT; HttpOnly; Secure; SameSite=Strict
```

### GET `/strategy`

This route returns alla the available authentication methods.

#### Reponse

```json
{
  "list": [
    {
      "metadata": {
        "name": "authn-basic",
        "uid": "19690619-db0c-43c6-a4ef-ec1ba7181891"
      },
      "spec": {
        "color": "blue",
        "icon": "fa-solid fa-key",
        "name": "basic",
        "strategy": "basic",
        "type": "form"
      }
    },
    {
      "metadata": {
        "name": "authn-guest",
        "uid": "4071ed97-9d1d-4027-8d5f-4cca2c798625"
      },
      "spec": {
        "color": "blue",
        "icon": "fa-solid fa-lock",
        "name": "guest",
        "strategy": "guest",
        "type": "redirect"
      }
    }
  ],
  "count": 2
}
```

### GET `/strategy/:name`

This route returns the authentication method with the given name.

#### Example

```bash
/strategy/auhtn-basic`
```

### POST `/strategy`

It is used to create a authentication strategy.

### DELETE `/strategy/:name`

It is used to delete an authentication strategy.

### GET `/user`

Parse cookie and return the json of the user.

#### Response

```json
{
  "id": "guest",
  "username": "guest",
  "provider": "guest",
  "email": "guest@krateo.io"
}
```

!!! Note

    Services respond with valid JSON, so, if the response is an array, it will be wrapped in the `list` property.

    If the response contains the `list` proerty it will add the property `count` with the number of items in the list.
