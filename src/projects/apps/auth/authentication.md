## Authentication

### App Teams

App users exist within a container called an "App Team", and each App can have one App Team assigned to it. 

An App Team is automatically generated when you set up a new app with authentication but it also gives you the option to assign an existing App Team to your app. This allows you to share preexisting user accounts between Apps, foregoing the need to have users re-register when using the new App. You can change the App Teeam at any point after the Apps creation.
This is particularly useful in scenarios where you are developing several different apps for the same audience, you can create a single App Team and then use it across every other App that has the same target audience.

Imagine you're developing a suite of internal developer Apps and they all have the same target audience, you can create the first App and this will initialise the App team. Then, for any future Apps you create which will be accessed by the same users, you can simply assign the original App Team when setting up the authentication.

### Username & Password

Username & Password authentication is the most basic form of authentication offered in an App, it will allow users to log into an App by a unique username and password that is stored in the platform.
The authentication flow is all handled within the platform as is the list of App users and their information.
Once a user is created, they can be assigned to one or more Groups which will authorize them to access resources and pages within the App.

### OAuth2/OpenID

The OAuth2 and OpenID frameworks are very similar to each other and both allow you to utilise another authentication provider (e.g. Microsoft or Google) for your Apps authentication. If you have ever used an app or website that gives you the option to log in with Google, LinkedIn or Microsoft then this is OAuth2 and OpenID behind the scenes. The reason they are so similar is that OpenID is a standard that implements OAuth2 but builds on top of it as well, guaranteeing additional information about the user.

In Apps, you can use any :docs-link[Identity Provider]{id="admin/identity_providers"} that you have set up in your platform as the authentication provider for your App.

The main difference between OAuth2 and OpenID in Apps is that OpenID guarantees certain information can be retrieved for the user that has logged in such as username, name, date of birth, address, email and more.
This is why when your App only uses OAuth2 there is no username in your App Users table as the platform cannot guarantee that it is provided that information.

#### Scopes & Required Fields

In both OAuth2 and OpenID authenticated apps you need to provide the ProfileURL (can also be known as the User Info endpoint) as this is used to fetch the user ID from the authentication provider you are using.
For example for Google the profile URL is [https://www.googleapis.com/oauth2/v1/userinfo](https://www.googleapis.com/oauth2/v1/userinfo) and for Microsoft it is [https://graph.microsoft.com/oidc/userinfo](https://graph.microsoft.com/oidc/userinfo).

You also need to provide the path to the ID field so if your reponse from the Profile API looks like this:
```json
{
    "sub": "OLu859SGc2Sr9ZsqbkG-QbeLgJlb41KcdiPoLYNpSFA",
    "name": "Mikah Ollenburg",
    "family_name": "Ollenburg",
    "given_name": "Mikah",
    "picture": "https://graph.microsoft.com/v1.0/me/photo/$value",
    "email": "mikoll@contoso.com"
}
```
then the path to the ID field will be `sub`.

You also need to provide the relevant scopes to access some of the user information. Typically you require the `profile` scope to get any name information and you require the `email` scope to get information about the users email.

If you are using OpenID, you must provide the `openid` scope as otherwise it is not considered to conform to the OpenID protocol. With OpenID it is advised to use as a minimum the following scopes `openid profile email`.

You'll also need to provide a path to the email field (this would be `email` from the above JSON) and a path to the name field (this could be either the `name` or `given_name` field in the above JSON).

### Registration and Approval

You can set up the option to allow new users to register their own accounts, this is useful for automatically enabling new users to log onto the system. If you wish to prevent this behaviour then App users must be created manually or through automation.

When new users are registered, you can restrict their access behind an approval system which requires them to be approved in the App's project page. This prevents users from being able to register and immediately start accessing the App, they have to wait until they've been approved.
> Approval is only available for Apps using the `Username & Password` protocol.

Find out more about :docs-link[App Authorization]{id="projects/apps/auth/authorization"}.
