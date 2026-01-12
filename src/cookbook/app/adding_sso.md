# Single Sign-On (SSO) for Your App
Single Sign-On (SSO) allows users to authenticate once and gain access to your app without needing to manage separate usernames and passwords. With SSO in toca.io, you can integrate your application with an external identity provider (IdP), such as Okta, Azure AD, Google, or Auth0.

By enabling SSO for your app, you can:
- Improve user experience with frictionless sign-in
- Centralize user authentication and identity management
- Enforce enterprise-grade security policies (MFA, password rules, access controls)
- Reduce password-related support and maintenance overhead

SSO is especially useful for:
- Internal tools used by employees
- Customer-facing apps for enterprise clients
- Multi-tenant applications requiring controlled access

Once configured, toca.io delegates authentication to your identity provider, and trusted user identity information is securely passed back to your app, allowing you to control authorization and access within your workflows.

You can set us SSO for the toca platform and for your individual apps. In this docuemntation we will set up SSO for your app rather than the platform ( for details on the platform go to the Admin → Users and Teams → SSO Providers)

## Set Up and Add an identity provider
You can learn details on how to do this in our <a href="https://github.com/tocalabs/toca-docs/blob/main/src/admin/identity_providers.md#identity-providers"> Identity Providers Documentation</a>.

You will need to go to Admin → Identity Providers and add your identity provider
![alt text](/src/assets/cookbook/adding_sso/image0.png)
Here is an example: 
![alt text](/src/assets/cookbook/adding_sso/image1.png)
Add the identity provider to your app.

You can add it on app creation through the creation wizard on the workspace page: 
![alt text](/src/assets/cookbook/adding_sso/image2.gif)

Or if it's an existing app you can enable authentication in the app settings: 
![alt text](/src/assets/cookbook/adding_sso/image3.png)




