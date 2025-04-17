# Import

Importing to a Toca platform begins by simply choosing an :docs-link[exported]{id="projects/export"} zip file from your machine's file system. An imported project/app will have its name appended with 'imported date/time'.

### Import summary

A summary modal will appear once your import has completed. It will contain an itemised breakdown of everything that has been imported.

A variety of additional functionality has been implemented as part of the import process, but whether or not it is relevant to you is dependent on multiple factors such as: the environment you are importing to, what data your export contains. It is as follows:

### Bot reassignment

A bot reassignment modal will appear upon import if your project contains activities which were assigned to bots which are not recognised by the target platform. To save you the hassle of manually reassigning every activity, you can choose to bulk reassign to a bot assigned to your user. Activities assigned to stateless will never need to be reassigned.

### Resource reassignment

You will be given the option to reassign resources if you attempt to import an app onto an environment where resources with matching names already exist. For example, if you try to import an app export which contains a datastore called 'employees', and a datastore called 'employees' already exists in that environment, you can use the existing datastore instead of importing a duplicate. This affects datastores, listeners and CMS.

### Merge

You will be given the option to merge when the entity which you are trying to import has the same name as an entity on the target env. Merging will keep the entity which currently exists on the system, but add anything else which exists in the export file. You will also have the option to import the entity separately by choosing 'new'.

Merging works by comparing the __names__ of entities on the platform you are importing into and the export you are driving the import from. If it notices that you have an activity/project/datastore/app on the platform that matches those within the Exported zip, it will give you the option to merge. If selected, merging will overwrite the existing entities on the platform with the ones from the import.

### User and groups reassignment

You will be given the option to reassign users and groups if the app which you are trying to import has authentication enabled. If the target environment recognises the users and groups in the export then it will automatically prepopulate them. If it does not then it will give you the option to reassign them.

### Sync dependencies

This will happen when your import contains something which is currently not installed on the target env e.g a specific version of an action, component etc. Everything that was missing will be automatically pulled down from pack manager; requiring no effort from the user.

### Reassign app team

You will be given the option to reassign app teams if the app which you are trying to import has authentication enabled. If the target environment recognises the app teams in the export then it will automatically prepopulate them. If it does not then it will give you the option to reassign them.

### Environment Variables

If any Datastore Parameters were marked as 'Environment Variables' during export, you'll be prompted to either accept their current values or provide new ones.
This is useful for configuring environment-specific settings such as **API keys** or **passwords**.
