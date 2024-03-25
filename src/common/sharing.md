# Sharing

Sharing allows you to collaborate on projects and apps within Toca with other users on the platform. Click on the share button and define the permissions of who you want to share with.

Entities can be shared with either individual :docs-link[users or groups]{id="admin/users_and_groups"}. Groups are a collection of users. Either can have all of their permissions removed entirely by clicking the 'x'.

**Permissions:** 

When you share an app, project or resource with other users/groups, you can define what level of access they will get, this is controlled through _permissions_.
The following permissions appear in descending order:

- Owner - The highest level of permissions which is assigned by default to the creator of the entity. You can also remove other owners but there must always be at least one owner.
- All - The user can perform any action with the exception of being able to change ownership. With this permission you can also remove permissions from other users.
- Write - Gives the ability to edit entities.
- Publish: Lets the user publish entities such as activities, workflows, and apps.
- Delete: Lets the user delete entities.
- Execute: Allows the user to execute jobs or activities, e.g manually running a workflow or triggering a listener.
- Read: The lowest permission; the user can only observe the relevant data.

**Cascading Permissions**

The addition or removal of permissions will cascade downward from entity to entity (assuming that the user keeps the default check box ticked). For example, if you have an application which relies on data from multiple data stores to function, instead of manually sharing the application and each datastore with another user, cascading permissions will apply the same level of permissions across all entities. The purpose of cascading permissions is to ensure consistency in each aspect of your work. You will always be warned when permissions are going to be changed via cascade.

**Filters on the project page:**
The projects page displays all of the projects and apps which your user has any level of permission. These lists can be filtered using the following options:

Owned by me: shows all projects and apps of which your user is an owner.
Shared with me: Shows all projects and apps of which your user is not an owner.
