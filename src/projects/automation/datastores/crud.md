# Generate automation

A wizard to create basic autmoation for creating, reading, updating and deleting data for a specific table.

## 1. Select which automations

The first thing you're asked is to select which automations you want to create. By default creating. updating and deleting will be selected.

You will also be asked which project you want to add the automation to (ie where it should put the workflows and activities). By default the current project (if applicable) will be selected.

## 2. Configure each automation

The wizard will the cycle through each automation, allowing you to configure each according to your needs.

### Workflow and activity names

These will be the names for the workflow and activity that will be created for each automation. The wizard will pick an appropriate default value.

### Inputs

These will be the inputs for the activity (and listener and/or connector if selected), and will be based on the table's columns. Depending on which automation if being configured the exact options will change. The wizard will make a best-guess of which should be selected.

### Listener

Listeners are mainly used to trigger automations from apps. If enabled, you will need to provide a unique listener name (the wizard will automatically pick a unique name), which forms part of URL used by the app. The wizard will automatically configure the listener with the selected inputs and other options.

If enabled there will be an example of how to use the listener on the final screen of the wizard.

### Connector

Connectors are used to trigger automations from external services such as webhooks. If enabled, you will need to provide a connector route (the wizard will automatially pick one), which forms part of the connectors URL. The wizard will automatically configure the connector, adding it to the workflow and configuring a response.

If enabled there will be an example of how to use the connector on the final screen of the wizard.

## 3. Confirm your settings

Before creating the automation, the wizard will provide an overview. To proceed with creating the automation, click `GENERATE AUTOMATION`.

## 4. Creating your automation

The wizard will then proceed with creating your automations. It will first check all the automation actions (and connectors if applicable) are available. It will then loop through activities, workflows, listeners and connectors, creating them as applicable.

Once complete you will see a `How to use` section (if you selected any listeners or connectors), which will provide examples of how you can trigger your automation via `cURL`.

Your automation will now have been created and accesible via the project screen.
