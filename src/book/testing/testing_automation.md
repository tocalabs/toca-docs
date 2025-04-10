# Testing Automation
When developing or making updates to automations, it's important to make sure that the automation does what we expect it to do, and that our updates aren't breaking things that were working before. For this purpose, the activity designer provides many useful features to make sure that our automations remain as correct as we expect them to be.

## Draft and Published states
Activities and workflows have two main states: draft and published. While editing an activity, when we hit the save button we are making a change to the draft state. This state is ideal for making changes to an activity without breaking a workflow which is in active use. 

![(An activity in draft state](draft_state.png)

When we are satisfied with the changes we have made to the activity, we can press the `Publish` button to push our changes to the published state: 

![An activity in the published state](published_state_activity.png)

The published state cannot be directly edited: it can only be pushed to either by 