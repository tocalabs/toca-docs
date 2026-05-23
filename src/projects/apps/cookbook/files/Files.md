## Files

In Toca, you can use and store files in **Datastore File Drive (Storage)** as well as in **Datastore Tables**. 

### File Drive

Each datastore contains a File Drive – file storage hosted by your Toca platform. File Drive is similar to a bot's file system but can be used by stateless automation and apps.

* File Drive can contain directories, sub directories etc. so you can organise files the way you need to
* Files and directories can be manually added and deleted via the datastore
* Files and directories can be added and deleted  using automation

> Moving or deleting files may break automation or apps that rely on those files.

![alt text](<../../../../assets/cookbook/files/Image 1.png>)

### File Drive - Automation

File path controls in automation actions can access File Drive files and directories via the **file chooser**. File Drive files are also available via the Datastore panel.

> Up to date versions of actions will be needed for most file interactions on stateless activities.

![alt text](<../../../../assets/cookbook/files/Image 2.png>)
![alt text](<../../../../assets/cookbook/files/Image 3.png>)

Some of the examples of automation actions using File Drive are:

- Copy File
- Delete File
- Move File
- Rename File
- Get Info of CSV/XLSX
- Create Folder
- Delete Folder
- etc.

### File Drive - Apps

Apps can use File Drive files via the **datastore panel** when selecting datachips:

1. Select the File Drive from the `Storage` section at the bottom of the variables list.
2. Point to the file using a file path (either manually entered or selected using the file chooser)

![alt text](<../../../../assets/cookbook/files/Image 4.png>)

File Drive files cannot be subscribed to for updates, so bear this in mind when using them. The main file-related app components are:
- File Downloader 
- File Uploader
  
---
### Datastore Table Files

In datastore tables, there is a column type called **File**. A user can upload various files (e.g. png, jpeg, pdf, gif) that can be further used in automation and apps. 

> Note: files from datastore tables are not stored in File Drive but in the File Manager, which can be accessed from Admin > File Manager.

![alt text](<../../../../assets/cookbook/files/Image 5.png>)

Basic **CRUD** actions can be implemented with table files: create, read, update, and delete. 

![alt text](<../../../../assets/cookbook/files/Image 6.png>)

![alt text](<../../../../assets/cookbook/files/Image 7.png>)

There are multiple scenarios for how these files can be used. For example, take a look at the Bug reporting tool app. There is a **Bug Form** that allows users to add new bugs to 'Bugs' table in a datastore. Each bug form has the option to upload a file as an attachment.  

![alt text](<../../../../assets/cookbook/files/Image 8.png>)

In the background, this form is confugured as a **Form** with the Form Type Listener. The **File Uploader** component is used to upload the file. When the form is submitted, it adds a new row to the table, including the file.

![alt text](<../../../../assets/cookbook/files/Image 9.png>)







