# Datastores 

Datastores are storage containers which you can throw almost anything into. They can store tables, files, images, variables, and Identities and they can even securely store passwords.
Each Automation project can have one or more Datastores inside it. This allows you to keep unrelated variables and data separate from each other and keep everything organized. 
Datastore parameters are case-sensitive. Datastore parameters refer to variables, passwords, files, Identities and tables. 

### Data from a Datastore

**Variables** - Store a named value with an associated type such as text, number, coordinates, image, etc. 
**Passwords** - Securely store a password, this value is encrypted and won't be logged anywhere. Recommended for credentials or sensitive information
**Files** - Persistely store a file so that it can be accessed by automation or apps
**Identities** - Link a digital identity so that you can use automation actions on behalf of a user such as sending an email from your Outlook account or uploading a file to your Google Drive
**Tables** - Store data in a structure of columns and rows, assigning data types per column and adding relationships between tables to maintain data integrity


* To find out more about Tables read the :docs-link\[Tables]{id="projects/automation/datastores/tables"}
* To find out more about Identities read the :docs-link\[Identity]{id="projects/automation/datastores/identity"}

 Automation and Apps can read from and write to datastore.

