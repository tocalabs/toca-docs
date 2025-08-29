# Deploying TDK Components

In the :docs-link[previous article]{id="book/tdk/building"}, we took a look at how you can develop and build TDK components such as automation actions, connectors and app components. The article will take you through how you can deploy the components from the TDK to the main platform so that anyone can use what you've built!

## Automation TDK Components

### Actions

#### Review Action

Once you are happy with your action, you can submit it for review. The TDK has an inbuilt review section that will show you all TDK components that have been submitted for review. This will show you a difference between the version submitted for review and the previous version, so that you can easily see what has changed between the two versions. From here, another user can review your action and either accept it or reject it with a comment to indicate why. You cannot review a component that you yourself have submitted for review, the review can _only_ be performed by another user.

:video{src="/src/assets/book/reviewing_tdk_component.webm"}

To submit an action for review, open the action in the TDK and click the "Submit for Review" button in the top right hand corner of the screen. To review an action, head to the "Pending Review" section from the TDK homepage, make sure you have "Actions" selected and then find the action you want to review. There is a button to approve and a button to reject the action, both are positioned in the top right of the review page.

:video{src="/src/assets/book/submitting_action_for_review.webm"}

> **Tip ✨**
>
> _If you run an action build whilst an action or action helper are submitted for review, it will build these components so that you can check that they build successfully before approving them._

#### Add Action to a Group

Once an action has been approved, you can add it to an Action Group. Adding an Action to an Action Group defines which group the action appears in when users are looking for it in the Activity Designer, for example the :doc-link[Set Variable]{key="SetVariableV2" type="Action"} action appears in the Variable group.

To add your action to an action group, head to the TDK homepage and either Create a new action group or open existing action group. Once you have opened the action group, search for the new action in the panel on the left and drag it into the group panel on the right hand side. Once you have placed the action in the right place, save the group using the save button in the top right hand corner.

:video{src="/src/assets/book/adding_action_to_group.webm"}

#### Run an Action Build

Once you have added your action to your group, you can run an action build. An action build takes all of the actions which are approved and compiles them into a single `DLL`, including their NuGet dependencies and any helpers they rely on. There is an action build for each type of Bot, GUI and Stateless. This action build can then be loaded onto the Bots connected to your Toca platform.

You can only run an action build if your user holds the Admin role. This is because an action build has the potential to cause disruption to the main platform as you could load a new action build might have had actions removed that your automation is relies on, so it should only be done by someone who knows what they're doing. If you are an admin user, you can head to the main platform, go to the Admin section and then the Action Builds subsection. From here, you can view a list of all previous action builds, including the details of what actions were added/removed between each build. Head to the tab for the type of build you want to perform (GUI or Stateless) and hit the build button in the top right hand corner. This will start compiling all your actions, this can take quite a while (up to 5 mins) and can be very resource intensive, so our advice is to do this when the platform is not being used very heavily.

:video{src="/src/assets/book/run_action_build.webm"}


#### Update Action Build on Bot

Once your action build is complete, you need to load it onto the Bot. Like running an action build, this is an Admin only function and is done from the main platform. Doing this will load the new DLL onto the Bots and let you use any new actions included in the build, but will also mean that only actions which were removed in the new buildwill no longer be available to use.

To load a new build onto a Bot, head to the Admin section and the Bots subsection. From here, click on each bot that you want to update. On the Summary tab for each bot, there is a Bot build ID and a Stateless build ID field, each of these fields will only be populated if you have the corresponding Bot service running (GUI and/or Stateless). If there is a new build available, you can press the refresh icon and this will load the latest action build onto the Bot.

> **Note 📝**
>
> _In almost all cases you'll want to update all bots to the latest action builds, this is so that all your bots have the same actions available. This is especially prominent with Stateless bots as a stateless bot can be chosen at random to run automation so making sure that all stateless bots have the same actions is imperative to ensure your platform operates predictably._


:video{src="/src/assets/book/updating_bot_build.webm"}

### Action Helpers

Action Helpers are built into the same action builds as the actions, so you don't need to build them separately or add them to any groups, but you still need to submit them for review and get them approved before they can be used in actions.

> **Tip ✨**
>
> _Like actions, action helpers will be built in action builds when they are "In Review", this allows you to check your helper code compiles before approving it._

### Connectors

#### Review Connector

Much like an action, a connector must be submitted for review and approved before you can use it in the main platform. To submit a connector for review, make sure you have saved your latest changes by clicking the save button in the top right and then submit for review by clicking the "Submit for Review" button. When you do this, the connector will check it can compile behind the scenes and will error if it cannot, showing you the error in the snackbar message at the bottom of the screen. You can review a connector in the same place that you review all TDK components, head to the TDK homepage and then click on the "Pending Review" button and make sure you have Connectors selected in the dropdown in the top left corner.

#### Build Connectors

To build a connector, you must be an admin user. If you are an admin user, head to the Admin section on the main platform and go to the Listeners & Connectors subsection. Head to the connectors tab and click the build icon at the top right of the list of connectors that are currently in use. This will build all connectors that are approved on the platform and load them into the API gateway so that they can be used. If any errors occur then the errors will be reported back to you when the build finishes. Once your connector is built, a user can insert it in any workflow.

:video{src="/src/assets/book/building_connectors.webm"}

## App TDK Components

### App Components

#### Build App Component

When you develop an App component, you will want to test that at the very least your code builds. To do this, make sure you have saved your latest changes to the component by clicking the save button in the top right hand corner and then click the build button which appears next to the save button. This will build the component in isolation and you can see any warnings or errors in the Problems tab which appears underneath the code section. This will not only verify your component builds successfully, but also once built that bundle will be used by the platform once the app component is approved. This means that before you submit your app component for review, you should _always_ save the latest changes and build the component.

:video{src="/src/assets/book/building_app_component.webm"}

#### Review App Component

Like actions and connectors, you need to submit a connector for review and it must be approved before it can be used in the main platform. Once you have saved and built your component, click on the "Submit for Reivew" button which appears in the menu at the top right corner next to the build button.

#### Add Component to a Group

Once a component has been built, reviewed and approved, you can then add it to a new or existing group. Doing this will mean that your new component appears in one of the groups in the Components panel within the App Designer. This makes your new component easier to find and more organised.

To add an app component to a group, head to the TDK homepage and either create a new group which has type of app component or open an existing one. Once you have opened the group, search for your new app component in the panel on the left and drag it into the group panel on the right. Once you have dragged your app component into the group, make sure you save the group by clicking the save button in the top right.

:video{src="/src/assets/book/adding_app_component_to_group.webm"}

### App Action

#### Build App Action

Like app components, before submitting your component for review, make sure you save your latest changes and build the app action. If there are any issues when building your app action they will appear in the Problems panel that appears under the code section. The save and build buttons are located in the menu in the top right hand corner of the app action page.

#### Review App Action

Once your app action has built successfully, you can submit it for review by clicking on the "Submit for Review" button which is located next to the build button.

#### Add App Action to a Group

When your app action has been built and approved, you can then add it to a app action group. This is the same as adding an app component to a group, but the group will contain app actions rather than app components. From the TDK homepage you can either open an existing group or create a new one. Once you have opened the group, drag your app action from the panel on the left into the group panel on the right. When you have placed the app action in the best place, you can then save your group by clicking the save button in the menu in the top right hand corner. With your group saved, platform users will now see your new app action in the group in the IPL Designer!
