# Identity Providers

[Identity providers](https://en.wikipedia.org/wiki/Identity_provider) allow you to link identity providers from other platforms such as Active Directory from Microsoft or Google with your Toca platform. Toca can link to any OAuth2.0 or OpenID Connect compatible provider.
This opens the doors to the following features:
1. Platform SSO - Allowing platform users to sign into your :docs-link[Toca platform]{id="admin/maintenance_and_security} with Single-Sign-On (e.g. Log in with Microsoft, Log in with Google)
2. App SSO - Configuring your :docs-link[App Authentication]{id="projects/app/authentication"} to leverage the Identity Providers to allow users to log into an App with their other accounts 
3. :docs-link[Datastore Identities]{id="projects/automation/datastores/identity} - Allow you to perform automation actions on behalf of a user such as Send an Email from your Microsoft Account, Upload a file to Google Drive from your Google account

This works because an Identity Provider acts a bridge that links the Identity Provider with the Toca platform, allowing a secure and authenticated way of leveraging other software from delegated accounts.

To successfully link an Identity Provider with your platform you will require the following details:
- Client ID
- Client Secret
- Token Endpoint
- Authentication Endpoint
- User Info Endpoint _(only required for OpenID type providers)_
- Scopes

You can also provide:
- A name
- An icon

## Examples

The two most common identity providers that you are likely to connect to is Active Directory from Microsoft and Google Identity for Google accounts. Below we will demonstrate how you configure Identity Providers for both providers.

### Microsoft

The instructions here are deliberately light when describing what to do on platforms outside of Toca as these are subject to change, but for more information on what to do with Microsoft, you can read their Quickstart guide [here](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app).

Key information to know:

| URL | Description |
| :--- | :--- |
| `https://{toca platform url}/assets/oauth.html` | Redirect URL required for Datastore Identities to work |
| `https://apps.{toca platform url}/api/auth/callback` | Redirect URL required for Apps to leverage Identity Providers for Auth |
| `https://login.microsoftonline.com/common/oauth2/v2.0/token` | Microsoft Token Endpoint |
| `https://login.microsoftonline.com/common/oauth2/v2.0/authorize` | Microsoft Authorization Endpoint |
| `https://graph.microsoft.com/oidc/userinfo` | Microsoft User Info Endpoint |

1. Go to [Azure Portal](https://portal.azure.com) and head to Active Directory
2. Once there you will need to create an Application Registration which has an application type of `Web application`, using one of the redirect URLs specified in the table above, you will need to add the other redirect URL later from the Overview Page
3. Once created, you will see an Overview page that contains the Client ID, copy that and store it for later
4. Go to the the Certificates & Secrets section of your Application Registration and create a Secret, once created copy the Secret Value (_not_ the Secret ID) and store this for later
5. Go to API Permissions section and add the necessary scopes so your linked Identity Provider can access the right resources
6. Now head back to Toca and head to the Identity Providers page and create a new Identity Provider
7. Give the Identity provider a meaningful name and then paste the Client ID and Client Secret values from earlier into the relevant fields
8. Then paste the Token and Authorization Endpoints from above into the relevant fields*
9. Add your scopes
10. Add an icon if you wish and then submit the form


_* With some Microsoft Application Registrations, they may give you custom Token and Authorisation endpoints which are unique to this specific Application registration. To get these URLs you can select the Endpoints link on the Overview page of your Application Registration in the Azure Portal

### Google

Similar to the Microsoft version, detail will be sparse on how to set up the relevant information on the Google side but you can find out more [here](https://developers.google.com/identity/protocols/oauth2/web-server#creatingcred).

| URL | Description |
| :--- | :--- |
| `https://{toca platform url}/assets/oauth.html` | Redirect URL required for Datastore Identities to work |
| `https://apps.{toca platform url}/api/auth/callback` | Redirect URL required for Apps to leverage Identity Providers for Auth |
| `https://oauth2.googleapis.com/token` | Google Token Endpoint |
| `https://accounts.google.com/o/oauth2/v2/auth` | Google Authorization Endpoint |
| `https://www.googleapis.com/oauth2/v1/userinfo` | Google User Info Endpoint |

1. Head to your [Google Cloud Console](https://console.cloud.google.com/), head to APIs & Services and select Credentials
2. Click Create Credentials and select the OAuth Client ID option
3. Select the "Web application" Application Type
4. Give it a meaningful name and input the two redirect URLs from the table above into the "Redirect URLs" section
5. Click Create and this will return a modal showing your Client ID and Client Secret, copy both these values and save them for later
6. Now head back to Toca and head to the Identity Providers page and create a new Identity Provider
7. Give the Identity provider a meaningful name and then paste the Client ID and Client Secret values from earlier into the relevant fields
8. Then paste the Token and Authorization Endpoints from above into the relevant fields
9. Add your scopes
10. Add an icon if you wish and then submit the form

You can now use this Identity Provider for platform SSO, App Authentication or Datastore identities
