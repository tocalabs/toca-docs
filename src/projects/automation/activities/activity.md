# Activities 

Activities are the most fundamental component of your Automation projects. They form the reusable blocks with which you can build bigger and more complex automation by assembling them into Workflow. 

It is best practice to keep Activities focused on a specific aspect of the process you are automating, and building up complexity through combining many Activities in a :docs-link[Workflows]{id="projects/automation/workflows/workflow"}.

You can create activities assigned to the Stateless or a GUI :docs-link[Bot]{id="admin/bots"}, the Bot that is associated is the one that will run the Activity. 

> If you have no Bots assigned to your user then you cannot create an Activity as you have no resources to run the activity on.

## Error handling

When any action runs, it outputs a chip called `actionStatus`, which indicates the outcome of the action. This chip can be used in conditions (like `If Then`) to drive automation logic based on the action's success or failure.
The `actionStatus` chip can have one of the following values:
- `Success`: The action completed successfully.
- `Failed`: The action failed to complete and [Fail on Error](#fail-on-error) is checked, meaning execution stops.
- `ContinuedWithErrors`: The action failed to complete, but [Fail on Error](#fail-on-error) is unchecked, meaning execution continues.
- `SuccessWithTimeout`: The action timed out but [Error on Timeout](#error-on-timeout) is unchecked, meaning execution continues.
- `Cancelled`: The action was cancelled by the user or in the action code.

Since execution stops when an action fails, you'll most commonly want to use the `actionStatus` chip to check for `ContinuedWithErrors` or `SuccessWithTimeout` values (or the inverse: `actionStatus != "Success"`). These values indicate that the workflow continued but that something went wrong and may require corrective logic.

For example, let's say you have an `API Caller` action that retrieves data from a third-party service. If that service is temporarily unavailable, you might want to retry the call a few times before giving up.
The below example illustrates how `actionStatus` could be used in this scenario to retry an `API Caller` action up to 5 times until it succeeds, with a `Debug` action logging that the action was retried, each time it fails.
![Action Status Usage Example](/src/assets/action_status_usage_example.png)

The following Action properties can be set to control how errors are handled:

### Fail on Error: 
All actions include a checkbox labelled `Fail on error?` If checked, it marks the action as Failed when an error occurs during its execution, indicating an irrecoverable issue. By default, this option is checked for all actions.

### Timeout
Certain actions, such as those in the Vision, OCR, or Flow Control categories, feature a `Timeout` property. This property, measured in milliseconds, specifies how long the action can run before it stops itself. Notably, a timeout can be set to `-1`, indicating that the action should disregard the timeout entirely.

### Error on Timeout
Actions with the Timeout property also include an `Error on Timeout` setting. This setting determines whether a timeout should be treated as an error. Sometimes, a timeout may not signify an error. For example, with an image search action looking for an occasional pop-up, it should continue if the pop-up doesn't appear but handle it if it does.

