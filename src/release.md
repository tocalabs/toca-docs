# 7.7 - Release Notes

## What's New

### General

#### Datastore Interface

The Datastore view has had a significant overhaul in terms of it's look and design, this is mainly to allow user to more easily filter on the values within a Datastore based on name, type, last modified or last created.
The preview of types has also been improved so that more data can be viewed at once and the tools available for each type of value are clear.

![Datastore UI Changes](/src/assets/datastore_ui_changes.png)

#### Cancelled Jobs UI change

Jobs which have been cancelled are now marked with a grey icon instead of a red icon, this is to help visually distinguish jobs which have been cancelled from jobs which have failed.
![Cancelled Jobs](/src/assets/cancelled_jobs.png)

### TDK

#### .NET 8 Update

This release of Toca includes an upgrade to the .NET framework from .NET 7 to .NET 8. This includes and update from C# 10 to C# 12, this means you can use the latest features of .NET and C# when writing Actions, Action Helpers and Connectors within the TDK.

### Apps

#### Table Component

The latest version of the Table component (v1.0.3) is a dramatic overhaul of the existing table component that was available in Apps.
This new version now natively understands table relationships as well as local tables that have been set as an In Page Values. It also includes a host of new styling options, allowing you to customise your table to look exactly as you want it.
You can now also configure the table component so that users can directly manipulate datastore tables via the App or In Page Value tables.

![Table Component](/src/assets/table_component.png)

#### Table IPL Actions

We have added a host of new In Page Logic actions which allow you to directly manipulate datastore tables and local In Page Value (IPV) tables directly from IPL.
This means that you no longer need to build automation to simply add a row to a table or update an existing row. You can also create and manipulate local In Page Value tables using these new IPL actions.
The new actions are as follows and can be found in the new Table group in your IPL editor:
- Create IPV Table
- Add IPV Table Column
- Update IPV Table Column
- Delete IPV Table Column
- Get Table Data with Query - _works on IPV Tables and Datastore tables_
- Update Table Row(s) by Query - _works on IPV Tables and Datastore tables_
- Delete Table Row(s) by Query - _works on IPV Tables and Datastore tables_
- Add Row to Table - _works on IPV Tables and Datastore tables_
- Get Table Information - _works on IPV Tables and Datastore tables_

![Table IPL Actions](/src/assets/table_ipl_actions.png)

## Bug Fixes

Bug fixes mainly covered the following themes:
- Import & Export
- Datastore Table stability and performance when retrieving or manipulating data

> Contact <support@toca.io> for a full list of bug fixes included within this release.

## Deprecated

No functionality has been deprecated in this release.
