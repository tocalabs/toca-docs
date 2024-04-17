# Row Level Permissions

Row level permissions allow you to set up access policies to individual rows of data in a table.
This can be useful when you want to display some data in your App but you only want users to see the data that they have permission to see.
Row level permissions work by allowing a row to be accessed either by:
- Toca platform user
- Toca platform user group
- App Role
- App User

> N.B. You can only assign App related permissions to table rows if the datastore is listed as a resource of the App in question.

Row level permissions are the most secure way of limiting access to data as the permissions are checked when data is requested or updated on the server side.
You can think of permissions as an extra condition that is checked when the row is updated or read:
```sql
SELECT id, actor_name, date_of_birth FROM actors
WHERE id = {row_id}
AND permissions CONTAINS {user_permission};
```

The level of access to a particular row can be controlled by selecting any of the following permissions:

| Permission Name | Description |
|--- | --- |
| Read | Allows row of data to be read |
| Write | Allows data in the row to be updated |
| Delete | Allows the row to be deleted |
| All | Shortcut for giving Read, Write and Delete permissions |
| Owner | Allows you to edit permissions on the row of data and add and remove roles/users from accessing the row |

> N.B. Any rows where permissions are not explicitly set default to inherit the datastore permissions

### Setting Permissions

If you do not explicity set any permissions on the rows within a table, then the rows will inherit their permissions from the table's permissions. However, when you want to set the permissions on rows explicitly you can do this in two different ways:
1. Manually update the row via the table viewer within the datastore
2. Use the :docs-link[Manage Row Permissions]{id="ManageTableRowPermission" type="Action"} action to set the permission of a row from within an :docs-link[Activity]{id="projects/automation/activities/activity"}. This can also be used in conjunction with the :docs-link[Get App User]{id="GetAppUser" type="Action"} action to set a row level permission to a particular App role.

