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

Once configured, the platform delegates authentication to your identity provider, and trusted user identity information is securely passed back to your app, allowing you to control authorization and access within your workflows.

You can set up SSO for the toca platform and for your individual apps. In this documentation we will set up SSO for your app rather than the platform (for details on the platform go to Admin → Users and Teams → SSO Providers).

## Set Up and Add an identity provider

You can learn details on how to do this in our [Identity Providers Documentation](https://github.com/tocalabs/toca-docs/blob/main/src/admin/identity_providers.md#identity-providers).

1. Go to Admin → Identity Providers and add your identity provider.
![Add Identity Provider](/src/assets/cookbook/adding_sso/image0.png)

2. Example view:
![Example Identity Provider](/src/assets/cookbook/adding_sso/image1.png)

3. Add the identity provider to your app, you can do this:

- On app creation through the creation wizard on the workspace page:
![App Creation Wizard](/src/assets/cookbook/adding_sso/image2.gif)

- For an existing apps, in the app settings:
![App Settings Authentication](/src/assets/cookbook/adding_sso/image3.png)

You can read more about the parameters at [App Authentication & Authorization](https://github.com/tocalabs/toca-docs/blob/main/src/projects/apps/authentication.md).

4. Once set up, deploy the app and navigate to the URL:
![App Redirect to IdP](/src/assets/cookbook/adding_sso/image4.png)

The app should automatically redirect you to your identity provider to sign in.
