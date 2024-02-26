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

App users exist within a container called an "App Team", and each App can have one App Team assigned to it. This allows you to share  

### Username & Password

Registration

### OAuth2/OpenID

Registration



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

