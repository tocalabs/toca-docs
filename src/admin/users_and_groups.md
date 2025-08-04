# Users & Groups

This area of the platform allows users with the Admin role to administrate other platform users. From here you can:
- Create new users
- Update existing users
- Change user permissions
- Update user passwords
- Disable and delete users
- Approve new platform users
- Create Groups of users
- Update Groups of users
- Disable and delete user groups

> The users and groups which are managed from this area of the platform relate solely to users of the Toca platform, this has no impact on app users.

## Users

Platform users can have their access to various parts of the platform controlled through Roles. _This is different to sharing, Roles will override sharing._

| Role | Description |
| :--- | :--- |
| Project | Access to automation projects |
| Workflow | Access to create, read and update automation workflows |
| Schedule | Access to create, read and update workflow schedules |
| Dash | Access to Apps |
| Data Store | Access to Datastores |
| Profile | Access to update their profile settings, for users who register in the system via Single-Sign-On, this is by default the only Role they have until they are approved |
| Authentication | Access to authenticate |
| Execution Engine | Ability to run automation workflows |
| Object | Ability to save Files in the platform |
| Cryptography | Ability to encrypt and decrypt sensitive variables such as _Passwords_ in Datastores |
| Web Packager | Ability to deploy an App |
| Preview | _Deprecated_ |
| Email | Ability to send emails, either via the Send Email action or use functionality like sending an email alert on workflow failure |
| Pack Manager Push | Push components from the Toca Development Kit to the Hub |
| Activity | Access to create, read and update automation activities |
| Agent | Access to Bots, both GUI and Stateless |
| Listener | Access to create Connectors |
| Publish Dash | Access to deploy an App |
| Pipeline | Access to reporting and pipeline data |
| Export | Ability to export an App or Automation project |
| Tdk | Access to the Toca Development Kit |
| Document | Ability to save and retrieve images in Automation projects |
| Import | Ability to import either Automation or App projects |
| Identity | Ability to create and use Identities in Datastores |
| Types | Used to view types in the system such as Tables, Lists etc. |
| Download | Used to pull down Bot services |
| Pack Manager Pull | Used to install packs from the Pack manager |
| Admin | Gives user access to all roles listed above but also access to the Admin panel on the platform |

A good general rule of thumb is that anyone who is not an Administrator should get all Roles _except_ for `Admin`, any users which are considered Administrators should get _only_ `Admin`.

### Approval

If a user signs into the platform for the first time via Single-Sign-On and the platform Administrator requires users to be approved, then a user will sit in a hold state where all they can access is their own profile settings. They will remain here until a platform Administrator approves the user via the Approval tab on the Admin -> Users & Groups page.

## Groups

Groups are predominantly used in the :docs-link[sharing]{id="common/sharing"} functionality, as this allows you to easily share projects, apps and resources with many users at once.

Imagine you are building a project and you want to give all the developers working on your project `Read`, `Write` and `Execute` permissions. You might then create a Test Group containing testers and they might only have `Read` and `Execute` permissions. By grouping the users into "Developers" and "Testers" you can easily share the right entities with them quickly and efficiently.

![User Groups Diagram](/src/assets/user_groups.png)
