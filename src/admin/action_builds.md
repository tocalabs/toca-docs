# Action Builds

This section of the platform allows users to:
- View all action builds available on the platform
- Create new action builds for Stateless Bots & GUI Bots
- Delete action builds

An action build represents a single compiled library (DLL) which contains all the current automation actions that are published on the platform. An action build can be loaded in by both Stateless and GUI Bots to give them access to the actions on the platform.
These action builds are what allow you to create new actions on the Toca Development Kit and then distribute these new actions across your Bots in realtime.

There are separate action builds for Stateless and GUI bots as the actions available to each type of Bot differ. For more information about the differences between Stateless and GUI bots read :docs-link[here]{id="bots/bots"}.

![Action Build Diagram](/src/assets/action_build.png)

When you have either pulled in a new action pack from the :docs-link[Pack Manager]{id="packs/packs"} or a new action has been approved in the TDK, it is a good idea to execute an action build as the new action(s) won't be available for use on your Bots until you have built an Action Build and loaded the new build onto your Bot.
