# Packs

There are many packs of components that can be added to a Toca platform such as:
- Action packs
- App Components
- App Actions
- Connectors

In order to distribute these packs, these are pushed to a Hub and then each Toca platform can connect to a Hub. Once connected to a Hub, a Toca platform can either push packs to the Hub or download and install packs from the Hub.

A Toca platform can connect to one or more Hubs, allowing you to connect to the default Global Hub as well as private Hubs which might contain packs which have been built internally. A connection to a Hub is referred to as a :docs-link[Feed]{id="admin/feeds"}, which can be configured by a platform Admin user.

A Hub can be thought of as a remote repository which your Toca platform connects to.

![Hub Diagram](/src/assets/hub.png)

Hubs are the mechanism by which you can share packs built in the TDK across multiple Toca platforms, you push to a Hub from the TDK by publishing the pack and then you can install the pack via the Packs page in the other platforms.
