# App Authentication & Authorization

Authentication is a way of controlling who can access your app by requiring users to log into your application.
Authorization then allows you to restrict what users can see and do once logged into your application.

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

The OAuth2 and OpenID frameworks are very similar to each other and both allow you to utilise another authentication provider (e.g. Microsoft or Google) for your Apps authentication. If you have ever used an app or website that gives you the option to log in with Google, LinkedIn or Microsoft then this is OAuth2 and OpenID behind the scenes.
In Apps, you can use any :docs-link[Identity Provider]{id="admin/identity_providers"} that you have set up in your platform as the authentication provider for your App.

The main difference between OAuth2 and OpenID in Apps is that OpenID guarantees certain information can be retrieved for the user that has logged in such as username, name, date of birth, address, email and more.
This is why when your App only uses OAuth2 there is no username in your App Users table as the platform cannot guarantee that it is provided that information.


### Registration and Approval

You can set up the option to allow new users to register their own accounts, this is useful for automatically enabling new users to log onto the system. If you wish to prevent this behaviour then App users must be created manually or through automation.

When new users are registered, you can restrict their access behind an approval system which requires them to be approved in the App's project page. This prevents users from being able to register and immediately start accessing the App, they have to wait until they've been approved.
> Approval is only available for Apps using the `Username & Password` protocol.

## Authorization

### Users, Groups and Roles

The authorization framework uses the concept of Groups and Roles to manage access to resources and content in your app.

A **Role** is a named permission that can be placed on resources or content to restrict the level of access e.g. Manager, Contributor, Viewer

A **Group** is a collection of one or more roles and a user is assigned to one or more groups. Some examples of groups might include "Head of Department", "Senior Engineer", "Junior Engineer" 

A user can then have one or more groups assigned to them and the roles are additive, meaning a user will always have every role from all the groups they are assigned to.

![App Users, Groups and Roles Diagram](/src/assets/app_auth.png)

In the above example, Graydon is assigned to both the `Line Manager` group and the `Senior Engineer` group and as a result, he has access to all the roles.
Guido is only assigned to the `Senior Engineer` group, but as the `Senior Engineer` group is associated with both the `Contributor` and `Viewer` roles, he has both those permissions.
Finally, Anders is assigned to the `Junior Engineer` group so only has the `Viewer` role attributed with his user.

#### Default Group for New Users

#### Default Group for Unauthenticated Users

### Page Permissions

If your app has authentication enabled, then you have the option to restrict access to every page in your appllication.
Each page only has one permission required to view it:
- **Read**

You can assign specific Roles in your app to have the Read permission on each page, for example you might have a page that allows managers to approve annual leave and you only want users who have the `Manager` role to be able to view the page. 

If a user does not have a role associated with their user that grants them Read access to the page then when they try to view it they will be directed to a `401 - Unauthorized` if they are logged in or the `Login` page if they are already logged in.

> N.B. If your App contains a login page then make sure you have not restricted access to this page as otherwise unauthenticated users will never be able to access the login page!

### Resource Permissions

Once your app has authentication enabled, you are able to restrict access to the resources you have linked with your App.

The following permissions are available on each resource type:

| Resource | Permissions | Description |
| --- | --- | --- |
| Listener | Read | **Read** allows the user to view the outputs of the listener in the App |
| Listener | Execute | **Execute** allows the logged in user to execute the listener to run a workflow |
| Datastore | Read | **Read** allows the logged in user to view data from the datastore in the App |
| Datastore | Write | **Write** allows the logged in user to directly write into the datastore | 

By assigning Roles from your app the above permissions you can restrict the capabilities of each group of users. For example, this would be useful if you have a workflow that approves a pay rise and you want to restrict this to only be executed by users who have the `Manager` role.

If a user does not have permission to view content from a datastore then they will simply not see the content and if they attempt to execute a listener when they do not have permission to do so then it will fail to execute.
