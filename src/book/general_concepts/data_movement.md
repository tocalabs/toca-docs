# Moving Data Around

Understanding how data flows around Toca is key to designing an efficient and robust application. Having a good foundational knowledge will also help you understand what you should and shouldn't do when putting together the pieces of your app.

## Linking Apps to Datastores

If you want to display data from your Datastores inside an App, such as displaying data from a table in a table component or a chart or maybe driving a dropdown field with a list variable in a datastore, then you will need to link your App to your Datastore. Doing this will make the datastore a resource of the app and allow you to choose data directly from your linked datastore when configuring components and IPL actions inside your app.

![Apps Linking to Datastore](/src/assets/book/apps_to_datastores.png)

When you load data into a component on your page, particularly data from a **table** or **view**, you should be mindful of how _much_ data you are loading in. For example, if you have a table which has 100,000 rows of data in it and you attempt to display all that data at once in a table component on your page, the performance of the page is likely to be pretty sluggish! Make sure you are always paginating your data where possible, all components which allow you to load tabular data will have options for pagination, allowing you to control how much data you load onto your page at once.

## Linking Automation to Datastores

Reading and writing data to a perisistent store


## Linking Apps to Automation

### Inputs and Outputs


## The Context Object

### Apps

### Automation
