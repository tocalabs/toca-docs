# Versioning

Versioning of Toca entities uses a three tiered system.

**Draft** - By creating an entity for the first time you are creating a draft version. Everytime you edit an entity you are editing the draft version.

**Published** - A published version is created by publishing a draft version. Published versions of any entity cannot be modified. The published version is what typically represents your live or "production" version.

**Previous** - The last version that was published before the most recently published version. Previous versions of any entity cannot be modified.

If you decide against the changes you have made then you can revert back to the previous version. Do this by opening the previous version and pressing 'revert'.

By viewing the published version of an entity you will be able to see when it was published last.

**Activities**

Activities work exactly as described above. The only thing that can be done whilst in the activity designer and viewing a published/previous activity is interact with the GUI bot screen.

**Workflows:**

Workflow versions adhere to the three tiered model as described above. A workflow can be run in any of the three states. To do this, switch versions and manually run the workflow. When looking at the job overview in reporting, the version of the workflow which was run will be denoted underneath the 'Publish State' column.

You can only create a schedule by using the published version of a workflow. If your project has no published workflows then the scheduler will prompt you to publish one.

In a workflow, you can change individual activity nodes so that they use either the draft or the published version. A draft activity inside a workflow can be recognised by the grey pencil icon on the activity node.

If your workflow contains activities which are set to their draft versions, then attempting to publish that workflow will publish those activities. You will be warned that this will happen.

**Apps:**

App versions similarly adhere to the three tiered model as described above.

An entire app is versioned by default and as such you can choose to deploy the individual app states should you wish to. An App is versioned as a whole rather than versioning individual pages as this would become very complicated to keep track of. Instead, pages of a `Draft` app are always in `Draft` and pages in a `Published` app are always `Published`. When you publish the your App, it will simultaneously publish all of the pages as well.

**Listeners & Connectors**

Both listeners and connectors can also have versions.

If a listener or connector is associated with a workflow and that workflow is published, so will the listener or connector.

By opening up the editing modal of a listener or connector you will be able to see all 3 states of the entity (should they exist).
