# Table Row Permissions

Permissions are essential in **Toca** for controlling who can interact with your table data. At the table level, you can restrict access so that only certain **App Roles** can view or modify data. This ensures that other users cannot retrieve or interact with the data without the required role/permissions improving the security of your data and applications.

However, sometimes you need even more granular control. Instead of applying restrictions to the entire table, you may want to **limit access to specific rows** for an individual **App User** or **App Role**. This is where **Table Row Permissions** come in.

---

## Example: Restricting a Table Row to a Specific User

### Step 1: App Setup
I have an app configured with the **Username/Password** authentication option:

![App authentication screenshot](/src/assets/cookbook/app_authentication.png)

### Step 2: Table Setup
I have an automation project with a datastore containing a **Client Data** table, which contains a row that I want to restrict to a specific user:

![Client data table screenshot](/src/assets/cookbook/client_data_table.png)

---

### Applying Row Permissions

I want to restrict a particular row so that it can only be accessed by a single App User (e.g., **John Doe**). To do this, I use the **"Manage Table Row(s) Permissions"** action.

### Step 3: Variables
In my activity, I can use use two key variables to achieve this result:
- **App User ID** → `appUserId`  
*This is the App User ID of the user I would like to manage the table row permissions for*
- **Table Row ID** → `rowId`  
*This is the Row ID of the table row I want to manage*

### Step 4: Configure the Action
Adding the **Manage Table Row(s) Permission** action, configure it as follows:

![Action configuration screenshot](/src/assets/cookbook/action_configuration.png)

- **Table**: `client data`  
  *The name of the table containing the row you want to modify*
- **Operation**: `Add Permission`
- **Rows**: `Single`  
  *You can also choose `Multiple` to update permissions for more than one row at a time*
- **Row ID**: `rowId`  
  *The unique Row ID of the table row you want to modify*
- **User/Role ID**: `appUserId`  
  *Provide either an App User’s ID to assign permissions to one user, or an App Role ID to assign permissions to an entire role*
- **Permission**: `All`  
  *Available options are: `Read`, `Write`, `Delete`, `All`, and `Owner`*

---

## Step 5: Verify Row Permissions

Once the automation runs, the **Permissions** icon at the end of the table row turns **pink**, indicating that row-based permissions are applied:

![Row permissions icon screenshot](/src/assets/cookbook/row_permissions_icon.png)

Clicking the icon shows that the App User **John Doe** has been added with **all** available permissions, exactly as configured in our automation action:

![Row permissions detail screenshot](/src/assets/cookbook/row_permissions_detail.png)

---

## Summary

Using **Table Row Permissions**, you can:
- Assign row-level access to specific **App Users** or **App Roles**
- Control whether they can `Read`, `Write`, `Delete`, or fully own the row as `Owner`
- Combine table-level restrictions with row-level permissions for complete control
