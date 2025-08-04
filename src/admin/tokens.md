# Tokens

Tokens are keys or Personal Access Tokens (PATs) that enable external systems to integrate and authenticate with your Toca platform without the need to sign in and authenticate each request. Linux Bots use Tokens as their mechanism of authentication with the core platform.

You can create a token and give it an expiration date if desired and then associate the Token with a user.
There are two types of user a token can be assigned to:
1. System User - Currently there is one option here which is a "Bot User", this should be used when you are creating a Token for a Linux Bot. This Token will then have the right privileges and roles required to perform all the tasks that a Bot has to.
2. Toca User - You can assign a token to a platform user in which case the token will take on the same privileges and roles that this user has.

After creating a token and assigning it to the relevant user, external integrations will need to add the following header `X-Toca-Token` to their HTTP request along with the Token value. Alternatively, they can use this as a way of authenticating with the Core platform.

For example, normally a platform user would authenticate with the platform by providing the following payload in the request to `/api/1/Authentication/validate`:
```json
{
  "username": "{user name}",
  "password": "{password}"
}
```

And you would get a response along the lines of:
```json
{
  "sessionId": null,
  "serviceId": null,
  "status": "Success",
  "exception": null,
  "content": {
    "token": "ey..."
  }
}
```
Instead of the payload example above, you can swap out the users credentials for a token so the payload would now look like this:
```json
{
  "pat": "123abc..."
}
```

This allows you to authenticate with the Toca platform without explicitly using the users credentials.
