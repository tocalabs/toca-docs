# Permissions

There are various forms of permissions across the platform which can help you to restrict access to certain resources in the platform. Permissions can effect either platform users (i.e. people who build on the Toca platform) or app users (i.e. users set up on authenticated apps).

## Platform Permissions

### Sharing Permissions

The main place you'll be using permissions is when you :docs-link[share]{id="common/sharing"} a project or resource with another user in the platform. This will let control whether the other platform user can simply view the resource or whether they can modify it. The main resources you can share in the platform are:
- Automation project
- App project
- Datastore

Each resource type has a slightly different set of permissions that you can configure but they all share:
- Read
- Write
- Delete
- All
- Owner

Apps then also allow you to give permission to _Deploy_ and _Publish_ the app, with automation projects allowing you to _publish_ entities within the project.

### Admin Users

The other form of platform permissions is the ability to make someone an admin user of the platform. This will give them access to the admin functions which include:
- Adding, modifying and deleting users
- Adding, modifying and deleting bots
- Creating and deleting action builds
- Viewing statistics about the workflow engine
- Viewing and deleting all listeners and connectors associated with the platform
- Adding, modifying and deleting Identity Providers
- Viewing the health of all backend services, also gives you the ability to restart services and view logs, mainly used for debugging and investigating issues
- Adding, modifying or deleting tokens used by Bots or people using the APIs
- Configuring security settings for login such as password rules and Single-Sign-On set up
- Add, modify and delete external app gateways
- Add, modify and delete feeds for the pack manager
- View and delete all files and folders stored in the platforms file system

To make someone an admin user, another admin user must go to the Admin -> Users & Groups section, identify the user they which to elevate and click on the cog next to the user before finally ticking the admin toggle and clicking `update`.

todo: insert video

> **Note 📝**
>
> _It is recommended that only users that require admin functionality are given admin functionality as there is the potential to do quite a lot of damage if not used properly._

## App User Permissions

When you can figure an app to be authenticated, you also have to set up :docs-link[app groups and roles]{id="projects/apps/auth/authorization"}, these roles can then be used to control what each app user has permission to do and access in the app. This includes what pages they can access, what data they have permission to see and what workflows they can trigger behind the scenes.

### Page Permissions

On an authenticated app, you can control which roles a user has to have to access the page. If a user has the right roles associated with their user then they can view the page, if not they will get redirected to a paeg containing a 401 - Unauthorised error.

To configure permissions on your app pages, head to the settings for an app page and tick the option to _Restrict access_. This will then give you a tickbox for each role defined in your app. Tick the roles which should have access to the page and make sure the roles which should not have access are unticked.

todo: Insert video

### Workflow Permissions

If you have any :docs-link[listeners]{id="projects/automation/workflows/listener"} linked with your app then you can control which roles a user must have to be able to execute the listener, which in turn triggers the workflow associated with the listener to run.

You can either do this during the app creation wizard if you link any listeners with the app when you first create it or you can do it at a later date. To configure these permissions, go to the settings of an app and head to the resources tab. The resources tab will contain both listeners and datastores, so find the listener section and from there you will see a list of listeners already linked with the app as well as a form to link new listeners with the app. When a listener is linked with the app, the roles defined in the app authentication section will appear below each listener. The roles will have two checkboxes next to them, one to allow the execute permission (allows users with that role to run the listener) and a read permission (allows users with this role to read the outputs of the underlying workflow). Typically you will always give a role both execute and read permissions on a listener.

todo: insert video

### Datastore Permissions

Similar to listeners, each datastore linked with an authenticated app will have their own set of permissions. This allows you to define which role can read, write or delete data from entities inside the datastore, most commonly tables. These permissions are then applied to the datastore as a whole and all entities inside the datastore inherit these permissions. If you'd like to set more granular permissions on specific entities within the datastore you can also do this, but by defailt the permissions are applied to the datastore as a whole.

Like listeners you can either configure these permissions during the creation wizard for the app or you can set the permissions in the settings panel for the app. If you head to the settings panel, go to the app resources tab and find the datastores section. You will see all the datastores linked with the app as well as a form allowing you to link other datastores. Once you have linked your datastores, each datastore will appear with a list of all the app user roles below, each role with several checkboxes next it allowing you to define whether a role can read, write or delete from the datastore.

todo: insert video

This means that if a user goes to a page that has a table component which uses a datastore table that they don't have permission to view as the datasource then they will instead see an empty table.


### Row Level Permissions

One of the most powerful permission features in the whole platform is the :docs-link[row level permission]{id="projects/datastores/tables/row_level_permissions"} feature on tables in the datastore. This allows you to define not only which app roles can have permission to individual rows in your table, but also you can specify which app user can view a row. This can be extremely useful for when you have a table or repeating layout component on a page in your app which displays data but you want to filter the data based on what each user should be allowed to see. You could add this filter when you define the datasource in the component but this isn't very secure as someone could easily change the query made to the data and they'd be able to view data that they should not be able to see. This feature instead ensures that the permissions check is done on the backend before any data is returned to the app.

Unlike the other app user permissions, this is not configured within the app, this is instead orchestrated via the :docs-link[Manage Row Permissions]{id="ManageTableRowPermission" type="Action"} automation action. This allows you to dynamically assign permissions to a row of data in your automation. To use this feature you would typically follow a pattern like so:
1. Build a form on your app page which allows a user to enter data which you want too be stored in a table
2. Link the form to a listener and the underlying workflow will take the app user's ID in as an input as well as the data from the form
3. The activity in the workflow will then do the following:
  1. Add Row to Table using the form data inputs
  2. Manage Row Permissions using the app user ID input and the row ID from the Add Row to Table action
4. When the user returns to the page displaying data from this table they will be able to see the new row but other users will not be able to


todo: add video
