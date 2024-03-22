# Packs

Packs refer to entities which can be added to a Toca platform which add functionality in automation and apps.

There are many types of packs that can be added to a Toca platform such as:
- Action packs
- App Components
- App Actions
- Connectors
- App Action Groups
- App Component Groups

In order to distribute these packs, these are pushed to a Hub and then each Toca platform can connect to a Hub. Once connected to a Hub, a Toca platform can either push packs to the Hub or download and install packs from the Hub.

![Hub Diagram](/src/assets/hub.png)

A Toca platform can connect to one or more Hubs, allowing you to connect to the default Global Hub as well as private Hubs which might contain packs which have been built internally. A connection to a Hub is referred to as a :docs-link[Feed]{id="admin/feeds"}, which can be configured by a platform Admin user.

![Possible Hub Configuration](/src/assets/hub_arrangements.png)

A Hub can be thought of as a remote repository which your Toca platform connects to, if you are familiar with programming then this is similar to the `pip` package manager in Python, `NPM` in JavaScript or `NuGet` in .NET.

Hubs are the mechanism by which you can share packs built in the TDK across multiple Toca platforms, you push to a Hub from the TDK by publishing the pack and then you can install the pack via the Packs page in the other platforms.

### Dependencies

A pack can have dependencies that it relies on to be installed and run correctly, examples of this might be:
- An action pack depending on action helpers
- An App Component Group depending on App components
- An App Action Group depending on App Actions

These dependencies are automatically identified and managed by the Toca Platform and Hub. This ensures that if you want to push a new Action Pack to a Hub and it relies on an Action Helper that is not already on that Hub, then it will automatically push the Action Helper to the Hub at the same time as the Action Pack. This works similarly when you are downloading a pack that relies on another pack, it will automatically install all listed dependencies alongside the pack. 
