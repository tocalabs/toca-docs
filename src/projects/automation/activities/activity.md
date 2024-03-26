# Activities 

Activities are the most fundamental component of your Automation projects. They form the reusable blocks with which you can build bigger and more complex automation by assembling them into Workflow. 

It is best practice to keep Activities focused on a specific aspect of the process you are automating, and building up complexity through combining many Activities in a :docs-link[Workflows]{id="projects/automation/workflows/workflow"}.

You can create activities assigned to the Stateless or a GUI :docs-link[Bot]{id="admin/bots"}, the Bot that is associated is the one that will run the Activity. 

> If you have no Bots assigned to your user then you cannot create an Activity as you have no resources to run the activity on.

**Error handling**

Fail on Error: All actions include a checkbox labelled "Fail on error?" If checked, it marks the action as Failed when an error occurs during its execution, indicating an irrecoverable issue. By default, this option is checked for all actions.

Timeout: Certain actions, such as those in the Vision, OCR, or Flow Control categories, feature a timeout property. This property, measured in milliseconds, specifies how long the action can run before it stops itself. Notably, a timeout can be set to -1, indicating that the action should disregard the timeout entirely.

Error on Timeout: Actions with the Timeout property also include an Error on Timeout setting. This setting determines whether a timeout should be treated as an error. Sometimes, a timeout may not signify an error. For example, with an image search action looking for an occasional pop-up, it should continue if the pop-up doesn't appear but handle it if it does.

