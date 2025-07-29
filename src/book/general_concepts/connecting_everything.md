# How Everything Connects

Understanding how data flows around Toca is key to designing an efficient and robust application. Having a good foundational knowledge will also help you understand what you should and shouldn't do when putting together the pieces of your application.

![How everything connects](/src/assets/book/everything-connecting.png)

## Linking Automation to Datastores

We'll first take a look at how you can link your automation to your data layer. Your automation can only see datastores that exist as part of the current project so to add a datastore to your current project you can either:
1. Create a new Datastore within your automation project
2. Link an existing datastore with your current automation project

Let's take a quick look at how we can do this.

### Create a new Datastore

When you are viewing your current automation project, you'll see at the top of the project home page there is an "Add Datastore" button in the Datastore column. Clicking on this will open a wizard which allows you to create a new datastore or link an existing one.

To create a new datastore, make sure the New tab is highlighted in the wizard, give your datastore a meaningful name and description so you can easily find it later. Hit the `CREATE` button and you're good to go, you've just created a new datastores that is part of your automation project.


### Link an Existing Datastore

Datastores can be shared across multiple automation projects, this is useful for sharing data between projects such as credentials to third party systems for example. To link an existing datastore to your current automation project, head to the home page of your automation project and click the "Add Datastore" button at the top in the Datastore column. This will open a wizard which has two tabs: "New" and "Existing"; Click on the "Existing" tab and select a Datastore from the dropdown which contains a list of other projects and their datastores.


Once you have linked a Datastore you can then use variables from within your Datastore in your automation activities and workflows! You can perform actions such as adding data to tables in your datastore, using passwords and identities from your Datastore to make authenticated API calls or use your Datastore as a remote file drive for processing files!

## Linking Apps to Datastores

If you want to display data from your Datastores inside an App, such as displaying data from a table in a table component or a chart or maybe driving a dropdown field with a list variable in a datastore, then you will need to link your App to your Datastore. Doing this will make the datastore a resource of the app and allow you to choose data directly from your linked datastore when configuring components and IPL actions inside your app.

![Apps Linking to Datastore](/src/assets/book/apps_to_datastores.png)

When you load data into a component on your page, particularly data from a **table** or **view**, you should be mindful of how _much_ data you are loading in. For example, if you have a table which has 100,000 rows of data in it and you attempt to display all that data at once in a table component on your page, the performance of the page is likely to be pretty sluggish! Make sure you are always paginating your data where possible, all components which allow you to load tabular data will have options for pagination, allowing you to control how much data you load onto your page at once.


## Linking Apps to Automation

If you want to run an  automation workflow from an App, then you need to link your workflows to your App. This will allow you to:
- Trigger a workflow based on a user interacting with your app
- Define a form in your app that a user can set inputs for and trigger a workflow
- Display the outputs of a workflow in your App when the workflow finishes

Rather than linking with a Workflow directly, workflows are triggered via something called a :docs-link[listener]{id="projects/automation/workflows/listener"}. A listener turns your Workflow into an API that can be called from your App, and it will understand what inputs the listener requires and what outputs will be returned that are then available for the app to use.

### Running Workflows via Listeners

A listener is something you can add to the start node of your workflow, it allows you to run the workflow by making a simple API call. You can then link a Listener with an App, this will then allow you to configure :docs-link[Form Layout]{id="18ac9843-6616-46b5-a965-b1b6b93326b2" type="AppComponent"} components to trigger the listener when the form is submitted or use the :docs-link[Execute Listener]{id="cab4b93a-75d2-4dfb-8ffa-38b3e9356479" type="AppAction"} app actions to run the listener through some IPL on your page.

To connect a listener to your app follow these steps when creating a new App:
1. When you get to the "Linked project resources" section of the App Creation wizard, click in the Add Listener auto complete field.
2. A list of all your listeners will appear before you, if you have already created a listener then you can select the listeners you want
3. If not, scroll to the bottom of the auto complete suggestions and there will be an option to create a new listener
4. Click `+ New Listener` and this will then allow you to select a workflow to add the listener to. Follow the wizard until the listener is created


If you want to connect a listener to a pre-existing app then:
1. Head to the Settings tab on your App's project page
2. Click on the App Resources tab on the settings section
3. Click in the Add Listener auto complete field and then follow on the steps laid out


> **Note** 📝
>
> Once you have linked a listener with your app, you can set permissions on it if your app has :docs-link[authentication]{id="projects/apps/authentication"} configured. This will let you control what roles user must have in order to trigger the listener.

### Inputs and Outputs






## The Context Object

### Apps

### Automation
