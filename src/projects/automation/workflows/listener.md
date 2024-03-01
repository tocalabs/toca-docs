# Listener 

A listener allows you to run the workflow from other parts of the platform such as running a workflow from an App or running a workflow from another workflow.
A listener resides on the Start node as it is a way of starting a workflow, along with manually running a workflow or running it via a :docs-link[Schedule]{id="projects/automation/schedules"}.

Behind the scenes, a listener acts like a callable API and is actually triggered by making a POST API call to the listener with the expected inputs.
It allows you to specify a name, **which must be unique**, an API key if you wish to secure the listener and a series of inputs that are then passed into the workflow.

Once called, a listener will return a unique job ID that represents the instance of the workflow that is now running, this can be used by the other parts of the platform to track the progress of the job.

Listeners are designed primarily for internal use, for example they are used by Apps to run a workflow and they can be used in conjunction with :docs-link[Trigger]{id="projects/automation/workflows/trigger"} nodes to run workflows from other workflows. To trigger a workflow externally, it is recommended to use :docs-link[Connectors]{id="projects/automation/workflows/connectors"}.

