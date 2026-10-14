What is versioning?

In version 10, we introduced a new version control system to Workspaces. A Version Control System (VCS) is a software tool that tracks and manages changes made to entities within a Workspace over time. It acts as a safety net and collaboration tool for developers, allowing teams to work on the same Workspace simultaneously without overwriting each other's work.

> When you create a Workspace, you are given the option to enable versioning for the Workspace or not. You can always enable versioning later if you decide you want to switch it on.

Key Functionality

* History and Auditing: Keeps a complete log of every change, who made, when and why.
* Reversion: Allows you to revert the Workspace back to a single point in time such as the last previous stable state
* Branching and Merging: Enables developers to create isolated copies ("branches") to build new features or experiment safely, then merge those changes back into the main branch when ready.
* Conflict resolution: Detects and helps resolve conflicting edits when multiple people modify the same part of a file
* Remote repository: Store a remote copy of all of the entities so that the Workspace can be cloned onto other Toca environments

How does the VCS work?

The VCS we use in Toca is based on [Git](https://git-scm.com/). You don't need to understand Git to use the VCS in Toca but there are a few concepts which it is worth getting your head around to get the best use out of it. If you are already familiar with Git then a lot of these concepts will already be known to you but there are a few subtle differences between native Git and Toca's VCS that it is good to understand.

Key Concepts

**Changes**

When you make a change in a Workspace with VCS enabled, any change is tracked and will be displayed in the changes panel. Any of the below counts as a change:
- Creating an entity (Activity, Workflow, App page etc.)
- Updating an entity - *Adding an action to an activity, removing a node from a Workflow, editing a component on an app page*
- Deleting an entity

These changes are stored in a staging area, a draft zone where you can preview and group specific changes before committing them. As Toca is a collaborative development platform, you might also see changes from other users in this staging area. This is useful as you might be working on a task with several others and you want visibility of the changes that the others are making.

> For users who are already familiar with Git you may be wondering about staging your changes. In Toca, we automatically stage your changes, so you don't have to worry about doing the equivalent of a `git add` or `git rm` when creating or removing entities.

**Commits**

When you have got your workspace into a state you're happy with, you can *commit* the changes in your staging area. A *commit* effectively takes a snapshot of your workspace at that point in time and it should represent an atomic unit of change - a complete, working update to the workspace. 

A commit is comprised of:
- The changes made since the previous commit
- The author of the commit
- A message relating to the commit

This allows you to look back at your commit history and see what changes were introduced at each "snapshot", who introduced them and why they introduced them.

You might be wondering why you have to manually commit a group of changes, why don't we just commit each change automatically? Well, the main reason is that in software development, it is better to think about your changes in terms of overall tasks or features that result in a working update to your workspace rather than individual entity changes. For example, if you're adding a navbar to all pages on your app, that will likely result in you creating a block and then editing several pages of your app. If you were to commit each of these individually, this one feature would result in many commits, even though it is conceptually just a single change to the app in your workspace. Instead, we can bundle the changes together into a single commit and give the commit a message like *"Adding navbar to app pages"*. This makes much more sense and will be much easier to understand if you need to comb back through the commit history. It also makes _reverting_ much easier, but we'll come onto this later.

**Branches**


**Remote Repositories**

As Toca's VCS is built on top of Git, you can connect your workspace to a remote repository. A remote repository is simply an external database that will store a _remote_ copy of your Workspace. This means you have a backup of your activities, workflows, apps and datastores. You can create a remote Git repository using services like GitHub, GitLab or Azure DevOps. Once your workspace is connected to a remote repository, you can take advantage of the features that these other services provide such as:
- Branch policies
- Pull/Merge requests
- Security policies
- Pre-commit hooks
- CI/CD pipelines

To connect a 

**Pushing**

**Pulling**

**Reverting**


What is tracked in the version control system?


Best Practices

**Working on a feature**


**Promoting from one Toca platform to another**


**Hot patching a live release**
