# Datastores

Datastores are storage containers which you can throw almost anything into. They can store tables, files, images, variables, and Identities and they can even securely store passwords.
Each Automation project can have one or more Datastores inside it. This allows you to keep unrelated variables and data separate from each other and keep everything organized.
Datastore variables are case-sensitive.

### Data from a Datastore

Datastores are organised into 4 categories:

- **Database** containing :docs-link[tables]{id="projects/automation/datastores/tables"} and :docs-link[views]{id="projects/automation/datastores/views"} – structured data in columns and rows, with assigned types and relationships between tables to maintain data integrity.
- :docs-link[**Variables**]{id="projects/automation/activities/variables"} containing simple values such as text, number, coordinates etc.
- **Storage** containing :docs-link[File Drive]{id="projects/automation/datastores/file_drive"} for file storage.
- **Auth** containing passwords (encrypted and not logged anywhere - recommended for credentials or sensitive information) and :docs-link[Identities]{id="projects/automation/datastores/identity"}.

Automation and Apps can read from and write to datastore.
