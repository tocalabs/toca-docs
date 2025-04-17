# Export

Export and :docs-link[Import]{id="projects/import"} is a vitally important aspect of the Toca ecosystem which allows you to not only backup your data locally, but also to transfer it to other Toca platforms.

To export a project is to request a compressed file containing all of the data which you have specified. The export can then be found in the Exports section of your platform where it will be downloadable indefinitely.

When you choose to export you will be shown a modal labelled 'Select Export Content', with a list of everything that can be exported. The majority of the time you will want to export the project in its entirety to ensure the integrity of the end result.

A project can be exported individually or in relation to an app. It is highly likely that an app will have extraneous resources which it relies on to function. This includes things such as listeners and datastores which are frequently contained within projects. In this case, exporting an app will include every project which is linked to it.

### Datastore Sanitisation

In the event that you would like to export a project but are concerned about sensitive data inside your datastores, you have the option to sanitise them. All datastore parameters i.e variables, tables, will have their data replaced with anonymised auto-generated data of the same type.

### Select Datastores to Export without Table Data

There are occassions where you would just like to export the tables within a datastore without any rows of data inside them. This could be because they contain sensitive data or you could be moving your project to from a Development environment to a Production environment and you don't need to carry the data across. This is also a useful feature if you have lots of table data as that can really slow down the export process, so checking this option would allow you to expedite the process.

## Environment Variables

When exporting a project, you have the option mark `Text`, `Boolean`, `Number`, and `Password` Datastore Parameters as 'Environment Variables'.
When this project is imported, users are given the option to either accept the current value of each Environment Variable or provide a new value.
This allows you to configure environment-specific settings like **API keys** or **passwords**.
