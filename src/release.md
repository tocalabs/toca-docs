# 7.6 - Release Notes

## What's New

### Apps

#### Deploy an App to multiple targets

You are now able to deploy an App to multiple different app slugs/deploy targets at once, this also includes the ability to deploy multiple different versions of your App simultaneously. Previously, it was only possible to deploy either the `Draft` or `Published` version of an App at once, but now with this feature you can have both versions deployed at the same time on different `URL's`. 

![Multiple App Deploy Targets](/src/assets/new-deploy-targets.png)

#### Custom CSS to App Component Properties

Within the properties of App Components, you can now use custom CSS for the following:
- Size
- Width
- Height
- Minimum Height
- Margin
- Padding

Now that these fields accept CSS properties, this allows you to set a property to use any valid CSS value and unit (e.g. `1.5rem`) rather than having to use the settings available.


![CSS App Component Properties](/src/assets/css-property.png)

#### Test App Authentication within Preview Mode

Within the App Designer, you now have the option to enter "Preview Mode" as an App User. This allows you to simulate using the App on behalf of an App User which means you can test that your login is working as expected as well as testing that your permissions are working correctly. You can pick from any existing App User, even if they have completely different Groups and Roles. This is also useful for debugging issues that your App Users might be facing when something is not working as expected, as now you can go through the App as that user.


![App User Preview](/src/assets/app-user-preview.png)

#### Documentation across the platform

The platform now comes with built in documentation so you can learn about features and functionality without ever having to leave the application. This includes documentation within the platform itself, usually available by selecting the little `( i )` information icon next to entities. It also includes documentation for actions, app components, app actions and connectors.

This also applies to when you are creating new entities within the Toca Development Kit, you are now required to add documentation before submitting your component for review. This ensures that all entities will continue to be documented.

The platform documentation is also hosted in [GitHub](https://github.com/tocalabs/toca-docs) and this is a public repository so you are welcome to browse the documentation from there and even contribute if you wish to.

Keep your eyes peeled for the info icon that signifies documentation!

![Documentation Example](/src/assets/docs_example.png)

#### Export datastore tables without the data

A quality of life improvement to the Export feature, you can now choose to export the tables without any rows in them, this will still export the table definition so that the column definitions will be maintained but will not export any of the rows within the tables. This is useful if the tables contain data that is only going to be overwritten anyway or if your tables contain sensitive data.

The new option will appear at the end of the Export options.

![Export No Data option](/src/assets/export_no_data.png)

#### Transfer table data

There is now a tool available within the datastore view that will allow you  to transfer data from one table in a datastore to another table in a datastore. This is useful when you are migrating data between projects or copying data. This will also work across different datastores, so no need for your tables to be within the same datastore. 

> You can also use this tool to quickly clear a table by setting the target and source table as the same and ticking the option to wipe the table before migrating the data!

![Data Transfer tool](/src/assets/data_transfer.png)


### Bug Fixes

Bug fixes mainly covered the following themes:
- Import & Export
- Performance
- Running workflows

> Contact <support@toca.io> for a full list of bug fixes included within this release.


### Deprecated

- The option to set up polling within Apps when retrieving data from datastores has been removed as this has been superseded by the new "Subscribe to changes" feature. App components that used this option have been migrated to use the "Subscribe to changes" feature as part of this version.
