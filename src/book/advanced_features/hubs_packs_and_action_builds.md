# Packs, action builds and hubs

## Packs

Packs are bundles of code which make up the building blocks of Toca. Packs are categorised according to their function:

| Pack Type     | Description                                                                                            |
| :------------ | :----------------------------------------------------------------------------------------------------- |
| Action        | Parts which make up activities, comprising inputs, and code to run on bots                             |
| Action Helper | Allows for reusable logic between actions, and the ability to define classes                           |
| Action Group  | Organises actions in the activity designer                                                             |
| Action Pack   | Organises actions so that they can be installed as a bundle from the Pack Manager                      |
| Connector     | A webhook entrypoint to a workflow                                                                     |
| App Component | A building block of apps                                                                               |
| App Action    | TODO                                                                                                   |
| App Layout    | TODO                                                                                                   |
| Group         | Organises app components, app actions and app layouts together for easy download from the Pack Manager |
| Release Pack  | Organises packs of every type together for easy download from the Pack Manager                         |
| Bot Service\* | Data or programs which continuously run on bots, in order to enable the running of actions             |

Packs can be created in the :docs-link[reference documentation]{id="admin/users_and_groups"}TDK
> \* Bot services are created and distributed by the Toca team, and cannot be created in the TDK.

## Action builds

As actions comprise C# code, they cannot be ran directly and must be compiled before bots can run them. To do this, we can run an *action build*.

