# File Drive

Each datastore contains a File Drive – file storage hosted by your Toca platform. File Drive is similar to a bot's file system but can be used by stateless automation, bot pools, and apps.

* File Drive can contain directories, sub directories etc. so you can organise files however you need to.
* Files and directories can be manually added and deleted via the datastore.
* Files and directories can be added and deleted programmatically using automation.

> Moving or deleting files may break automation or apps that rely on those files.

### Automation

File path controls in automation actions can access File Drive files and directories via the file chooser. File Drive files are also available via the Datastore panel.

> Up to date versions of actions will be needed for most file interactions on stateless activities.

### Apps

Apps can use File Drive files via the datastore panel when selecting datachips:

1. Select the File Drive from the `Storage` section at the bottom of the variables list.
2. Point to the file using a file path (either manually entered or selected using the file chooser).

File Drive files cannot be subscribed to for updates, so bear this in mind when using them.