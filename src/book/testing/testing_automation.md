# Testing Automation
When developing or making updates to automations, it's important to make sure that the automation does what we expect it to do, and that our updates aren't breaking things that were working before. For this purpose, the activity designer provides many useful features to make sure that our automations remain as correct as we expect them to be.

## Draft and Published states
Activities and workflows have two main states: draft and published.

### Activities 

![Switching between states in an activity](activity_states.gif)

While editing an activity, when we hit the save button we are making a change to the draft state. This state is ideal for making changes to an activity without breaking a workflow which is in active use. 

When we are satisfied with the changes we have made to the activity, we can press the `Publish` button to push our changes to the published state. If we are unsatisfied with a new published version (perhaps we have published a draft version by mistake) we can also revert to the previous published version.

``` 
Note that published versions of activities are also the versions of those activities which are used in published workflows.
```

### Workflows

![Switching between states in an activity](workflow_states.gif)

Similar to activities, workflows also have draft and published states. Note that draft workflows will use draft versions of activities, and published workflows will use published activities.

```
Draft states' connector routes/endpoints will be suffixed with /draft.
```

## Testing activity inputs
When we have an activity that takes inputs, it can be useful to feed the activity some dummy inputs to test that it does what we expect. Here we will discuss two common testing methods.

### Debug group
As activity inputs are used as variables within an activity, we can manually set them with a `Set Variable` action, and toggle this action on/off depending on whether we are testing. If we have multiple input variables to test, we can create multiple `Set Variable` actions and put them into a `Group`, which we can then enable when we are testing.

### Test boolean
Another way to implement tests is to add a boolean input to all activities we want to test, and we can call it `test` or similar. 