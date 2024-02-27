# App Authentication & Authorization

Authentication is a way of controlling who can access your app by requiring users to log into your application.
Authorization then allows you to restrict what users can see and do once logged into your application. You can read more about this [here](https://auth0.com/docs/get-started/identity-fundamentals/authentication-and-authorization).

By enabling authentication, you are asking users to provide information about who they are, usually through a set of credentials.
Once a user is authenticated, then you can leverage the inbuilt authorization framework to control that users access to various parts of your App.

Authentication can be implemented using the following protocols:

| Protocol | Description |
| --- | --- |
| Username & Password | Authentication flow is handled by Toca, each user has a username and password which they use to access the Application. |
| [OAuth2](https://en.wikipedia.org/wiki/OAuth#OAuth_2.0) | Your app links to another identity provider (e.g. Microsoft or Google), allowing users to log into your app using a preexisting account. |
| [OpenID](https://en.wikipedia.org/wiki/OpenID#OpenID_Connect_(OIDC)) | Much like OAuth2 but allows you to gather more information about the user due to the user information provided in this protocol. E.g. User email, profile picture |

Once you have been able to identify who a user is, you can control what they are authorized to view and do. You can control access to the following parts of an App:
- Each page of your app
- Each resource your app links to (Datastores and Listeners)
- Content within your pages

For more info about authentication and authorization see:
- :docs-link[Authentication]{id="projects/apps/auth/authentication"}
- :docs-link[Authorization]{id="projects/apps/auth/authorization"}
