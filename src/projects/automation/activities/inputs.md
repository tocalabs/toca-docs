# Inputs

By adding inputs to an activity, you are telling the :docs-link[activity]{id="projects/automation/activities/activity"} to expect to be started with some variables. Depending on the data type you select, you may also be able to give an input a default value. 

When you define an input, it will appear in the :docs-link[variables]{id="projects/automation/activities/variables"} tab and can be used as a variable within that activity. Like variables, an input can be described using the same $$ notation. To learn more about variables, visit [link]

The data inputs can come in many different ways. Examples include:

**Start with inputs:** This will open a modal which lets you manually define all inputs before running the activity as a whole. This is particularly useful during the development process of your automation.

:docs-link[**Via a workflow:**]{id="projects/automation/workflows/workflow} If previous activities in a workflow contain data which you want to reuse, simply output it and use the same name of the outputted variable as an input in a later activity. You can also manually start a workflow with inputs by clicking the 'run workflow' dropdown.

:docs-link[**Listener:**]{id="projects/automation/workflows/listener"} If you create a listener in the workflow designer, it will automatically have the inputs from every activity populated. If you add more activities to the workflow and want them to be further incorporated into the listener, simply edit the listener and click the magic wand button.
