# Workflow Overview

A Workflow comprises an orchestrated and repeatable pattern of activities. In Toca, the Workflow is the highest level of automation. It is the final stage where you put all your activities together to represent your business process. The workflow may be considered a view or representation of the real work.

**Nodes**
Nodes can be dragged onto your workflow canvas.
- Start - Denotes the start point of your workflow. Can only be used once.
- Exclusive - Defines a decision point in the workflow
- Trigger - Allows you to start another workflow
- label - A simple text label with customisable font options.
- Stop - Denotes the point at which the automation should stop. A workflow can have multiple stop nodes.

**Error handling**

Fail on Error: All actions include a checkbox labelled "Fail on error?" If checked, it marks the action as Failed when an error occurs during its execution, indicating an irrecoverable issue. By default, this option is checked for all actions.

Timeout: Certain actions, such as those in the Vision, OCR, or Flow Control categories, feature a timeout property. This property, measured in milliseconds, specifies how long the action can run before it stops itself. Notably, a timeout can be set to -1, indicating that the action should disregard the timeout entirely.

Error on Timeout: Actions with the Timeout property also include an Error on Timeout setting. This setting determines whether a timeout should be treated as an error. Sometimes, a timeout may not signify an error. For example, with an image search action looking for an occasional pop-up, it should continue if the pop-up doesn't appear but handle it if it does.


**Inputs, outputs and context (including AppUserId)**

By adding inputs to an activity, you are telling the activity to expect to be started with some variables. More on [inputs]

To output a value is to say that you want to use that value somewhere outside of that activity. More on [outputs]

These concepts are very important when working with workflows as they are one of the easiest ways to use contextual data across multiple activities. Simply output a datachip from one activity and then configure one or more activities further down the line to expect it as an input.

An example would be: If you were to create an App User in 'Activity A', using the 'create app user' action, you could then output the subsequent 'AppUserId'. Then, further along the workflow, you could tell 'Activity B' to expect 'AppUserId' as an input. 'Activity B' could then, for example, manage the permissions of that App User, or add them to a certain group based on other contextual data.

**Exclusives / Making a decision point** - 

Decision-making in a workflow involves using the Exclusive node. This node allows connections to multiple activities or nodes, each with its own condition. If a condition is met, the workflow follows that specific path.

The data which forms part of the exclusive expression will frequently be an output from an activity somewhere earlier in the workflow. Clicking the variable button and clicking on an activity will show all available outputs. This will include the 'activityFailed' output which has the type: boolean. An example of this being used in an exclusive may look like:

If 
'activityfailed' == true - then follow the path to the stop node

Or
'activityfailed' == false - then continue to the next activity node.

When you have an exclusive node highlighted and have pressed the variable button, you can also click the tab on the left hand side labelled 'datastores' which will show you all datastores and their variables. You can use these datachips as part of expressions in the exact same way that you would an output from an activity.


**Loops in Workflows**

Exclusives aren't just for single decisions; they can create loops too. If, for example, you have a workflow that starts by creating a variable called "counter" and then increments it by 1 in the next activity. The goal is to loop until the counter reaches 10 and then end the workflow. To achieve this, we insert an Exclusive node after the step that adds 1 to the counter. This Exclusive node has two conditions:

If the counter equals 10, proceed to the stop node.

OR

If the counter is less than 10, loop back to the first activity adding 1 to the counter.

Assuming the counter starts at 0, this loop will execute 9 times until the counter reaches 10, ending the workflow. This loop pattern enables more concise activities by moving loops from activities to the workflow; facilitating orchestration directly from the Workflow.

**Workflow Configuration / Reporting level / Email on fail**

To edit a workflow's configuration, click on the cog icon in the top right of any workflow designer.

**Reporting Levels** - 

The reporting level of a workflow designates how much information is returned when it is run. There are circumstances where you may want to decrease your reporting level due to large amounts of data which can build up unnecessarily.

To change the reporting level of a job, enter the workflow designer and access the workflow settings by pressing the cog icon. There are 4 reporting levels which are presented in descending order:

- Debug - This option will provide all data which is available as part of the report including all action data.
- Actions - Will return every action which was run as part of the job but none of its outputs.
- Nodes - Will only show the nodes of the workflow e.g start, activity, exclusive, finish.
- Errors - This, the lowest level of report, will only show the errors which have caused a job to fail.

**On Fail/Error:**
Save a screenshot - this functionality is reserved for GUI bots and will take a screenshot of the bot screen if an error is encountered.

Receive email notification - An email will be sent to the email address of the current user if an error is encountered.

**Activity Nodes**
- Disable - This activity will become greyed out and will be passed over as 'disabled' when the workflow is run.
- Duplicate - This will create a duplicate node of the activity which is not linked to any other nodes.
