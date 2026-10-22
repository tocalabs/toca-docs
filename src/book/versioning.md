# What is versioning?

In version 10, we introduced a new version control system to Workspaces. A Version Control System (VCS) is a software tool that tracks and manages changes made to entities within a Workspace over time. It acts as a safety net and collaboration tool for developers, allowing teams to work on the same Workspace simultaneously without overwriting each other's work.

> [!NOTE]
> When you create a Workspace, you are given the option to enable versioning for the Workspace or not. You can always enable versioning later if you decide you want to switch it on.

## Key Functionality

* History and Auditing: Keeps a complete log of every change, who made, when and why.
* Reversion: Allows you to revert the Workspace back to a single point in time such as the last previous stable state
* Branching and Merging: Enables developers to create isolated copies ("branches") to build new features or experiment safely, then merge those changes back into the main branch when ready.
* Conflict resolution: Detects and helps resolve conflicting edits when multiple people modify the same part of a file
* Remote repository: Store a remote copy of all of the entities so that the Workspace can be cloned onto other Toca environments

## How does the VCS work?

The VCS we use in Toca is based on [Git](https://git-scm.com/). You don't need to understand Git to use the VCS in Toca but there are a few concepts which it is worth getting your head around to get the best use out of it. If you are already familiar with Git then a lot of these concepts will already be known to you but there are a few subtle differences between native Git and Toca's VCS that it is good to understand.

### Changes

When you make a change in a Workspace with VCS enabled, any change is tracked and will be displayed in the changes panel. Any of the below counts as a change:
- Creating an entity (Activity, Workflow, App page etc.)
- Updating an entity - *Adding an action to an activity, removing a node from a Workflow, editing a component on an app page*
- Deleting an entity

These changes are stored in a staging area, a draft zone where you can preview and group specific changes before committing them. As Toca is a collaborative development platform, you might also see changes from other users in this staging area. This is useful as you might be working on a task with several others and you want visibility of the changes that the others are making.

> For users who are already familiar with Git you may be wondering about staging your changes. In Toca, we automatically stage your changes, so you don't have to worry about doing the equivalent of a `git add` or `git rm` when creating or removing entities.

### Commits

When you have got your workspace into a state you're happy with, you can *commit* the changes in your staging area. A *commit* effectively takes a snapshot of your workspace at that point in time and it should represent an atomic unit of change - a complete, working update to the workspace. 

A commit is comprised of:
- The changes made since the previous commit
- The author of the commit
- A message relating to the commit

This allows you to look back at your commit history and see what changes were introduced at each "snapshot", who introduced them and why they introduced them.

You might be wondering why you have to manually commit a group of changes, why don't we just commit each change automatically? Well, the main reason is that in software development, it is better to think about your changes in terms of overall tasks or features that result in a working update to your workspace rather than individual entity changes. For example, if you're adding a navbar to all pages on your app, that will likely result in you creating a block and then editing several pages of your app. If you were to commit each of these individually, this one feature would result in many commits, even though it is conceptually just a single change to the app in your workspace. Instead, we can bundle the changes together into a single commit and give the commit a message like *"Adding navbar to app pages"*. This makes much more sense and will be much easier to understand if you need to comb back through the commit history. It also makes _reverting_ much easier, but we'll come onto this later.

### Branches

Branches in Toca provide lightweight, isolated environments within a workspace where you can build, experiment, and test low-code workflows, app interfaces, and integrations without affecting your production application or disrupting fellow team members.

#### What is a branch?

In Toca, think of a branch as a parallel copy of your workspace. When you create a workspace, you start on a default primary branch (`main`), which represents the stable, deployed state of your project.

Creating a new branch creates an independent line of development anchored to a specific point in your project's history. Any changes you make—such as modifying a workflow, adding datastore variables, or updating app pages—exist exclusively within that branch until you choose to merge them back into the main branch.

```
[Feature Branch] ---> (Add New Integration) ---> (Update UI)
      /                                                       \
[main] -------------------------------------------------------------> (Merge & Deploy app)
```

So, when would you actually use a branch?

| Use Case | Description |
| :-- | :-- |
| Feature development | Build new apps, activities or datastore variables in complete isolation before launching them live. |
| Hotfixes & Bug Fixes | Safely isolate a critical bug fix on a separate branch, test it thoroughly, ande deploy it to production without bundling unfinished features. |
| Experimentation | Prototype complex automation or IPL logic without risk. If an approach fails, simply delete the branch. |
| Parallel collaboration | Enable multiple builders or teams to work on distinct modules of the same Toca workspace simultaneously without overwriting each other's configurations. |

> Tip 
> In Toca, you can see what branch you're in the bottom bar of the interface. From here you can switch branch and create new branches.

### Merging

So, you've got your branches, your isolated development, but how do you get your changes into your `main` branch? Well, this is where merging comes in. Merging is the process of combining the changes made on one branch into another - most commonly bringing your tested feature or fix back into  your primary workspace branch (`main`). 

You can merge a branch by going to the VCS panel and opening the menu and selecting *Merge branch*.

### Conflicts

When you perform certain actions such as merging or pulling, you might get conflicts. A conflict indicates that there have been changes on both your source branch and the target branch and the underlying VCS isn't sure which change it should pick. 

> This could happen if the same property of an entity is changed on both branches, for example you change the bot assigned to an activity on both branches or you change the words in a text component on an app page in both branches. It is good to be mindful of how conflicts can happen so that you avoid them more easily. 

When conflicts occur, you will be presented with a list of the conflicts and you will be given three choices:
1. Choose only the changes from the source branch - *This will discard all changes that correspond to the conflict from the target branch and overwrite it with changes from the source branch.*
2. Choose only the changes from the target branch - *This will discard all changes that correspond to the conflict from the source branch and overwrite it with changes from the target branch.*
3. Manually resolve the conflicts yourself - _**Advanced** This allows you to pick the changes manually, you can combine changes from both branches but this should be done with extreme caution._
          

Here are some tips for reducing the likelihood of a conflict when you perform a merge:
- **Keep branches small:** Merge your work frequently in smaller increments. Small, focused merges are much faster to review and significantly reduce the chance of a merge conflict.
- **Test before merging:** Always preview and test your app and automation on your working branch prior to initiating a merge into your `main` branch.
- **Sync regularly:** Periodically pull updated from `main` into your feature branch so that your working branch never falls too far behind the rest of your team.
- **Delete completed branches:** Once a feature branch or bug fix branch has been successfully merged, delete it to keep your workspace tidy and focused.

### Reverting

One of the great features of a comprehensive VCS is the ability to go back to a previous version when things go wrong. This is where _reverting_ comes in. Reverting allows you to go back to a particular commit on your branch, i.e. a particular snapshot in time.

Why might you revert? Maybe you've inadvertently merged some  changes that have broken the app in your `main` branch. Maybe you're trying a new feature but it hasn't worked as you expected and so you need to rollback.

To revert to a particular commit, go to the VCS panel and in the menu click on *History*. This will show you a full chronology of every commit that has happened on your branch, if you select a commit it will show you what changes were introduced in that commit and you can then revert to that point in time.



### Remote Repositories

As Toca's VCS is built on top of Git, you can connect your workspace to a remote repository. A remote repository is simply an external database that will store a _remote_ copy of your Workspace. This means you have a backup of your activities, workflows, apps and datastores. You can create a remote Git repository using services like GitHub, GitLab or Azure DevOps. Once your workspace is connected to a remote repository, you can take advantage of the features that these other services provide such as:
- Branch policies
- Pull/Merge requests
- Security policies
- Post-commit hooks
- CI/CD pipelines

To connect a remote repository, you must first create the repository in your Git service provider (e.g. GitHub). Make sure you initialise the repository as _empty_. Once you have created your repository, copy the HTTPS git URL. It will typically end with `.git`. You will also need a Personal Access Token (PAT), this is the thing that authorises Toca to communicate with the remote repository. You can connect your workspace to a remote repository via the Workspace settings.

> Note
> PAT's tend to have a lifespan of 6 to 12 months depending on how you generate it, so make sure you take note of the expiration date. You can update the PAT in the workspace settings at any time. Toca will also display a useful error if the PAT token has expired.

#### Pushing

Once connected to a remote repository you can _push_ your changes to the remote repository. Pushing is the act of taking the commits in your local branch and pushing them to the remote repository, it will only push the commits that have happened since the last time the branch  was pushed. This means that if it's the first time you're pushing a branch, it will push all of the changes that have ever happened on your branch.

When should you push?
- **End of a build session:** Ensure your latest work is safely uploaded to the remote repository.
- **Ready to transfer changes to another environment:** Make sure any changes you want to pull onto another environment are on the remote repo.

#### Pulling

Pulling is the opposite to pushing, it is the act of pulling changes that are on your remote repository that are not yet on your Toca workspace. This means you can pull changes that have been pushed from another environment.

When should you pull?
- **Start of your day**: Get the latest version of the branch before you begin building.
- **Pulling changes onto a different environment:** If you're pulling changes from your Dev system onto your production system.

> Note
> There is a non-zero chance that you'll get a conflict when you pull. This is because pulling is effectively merging the remote branch with your local branch, so you can end up with merge conflicts if you've edited the same properties locally and on the remote branch. You can handle this as you would a regular merge conflict.

## What is tracked in the version control system?

We've tried to take a sensible approach in what we can feasibly track and not track in our VCS and in the end it comes down to the following rule: If it's **code** then it is tracked, if it is **data** then it is not tracked.

If an entity is _tracked_ by the VCS, it means that any modification (adding, updating or removing) to an entity is then noticed by the VCS and you can commit the modifications. If something is not tracked then it means modifications will not appear in the changes panel and you cannot version modifications related to this.

The following entities **are** tracked:
- Workspaces
- Read Me
- Automation Projects
  - Activities
  - Workflows (including Listeners and Connectors)
  - Schedules
- Apps
  - Pages (components and IPL)
  - Blocks
  - App settings
  - App themes
  - App resources
- Datastores
  - Table models (schemas)
  - View models (configuration)
  - Variables
  - Credentials (Just the credential name, not the value)

What is **not** tracked:
- Datastore table data
- Datastore credential values (passwords & identities)
- App users
- App roles
- App groups

### An important note on Datastore data

When working on different branches you may want to change the schema of your datastore tables without impacting what is running on your `main` branch, you may want to add some test data to your tables to make sure that special characters don't break your automation without muddying the data in your `main` branch. We want to make sure that Toca supports these use cases.

To accommodate this, each branch has it's own copy of your datastores behind the scenes. This means that you can alter your tables, views and variables safe in the knowledge that it is not going to impact any other branches. You can also add test data to your tables and file drives without altering data used in other branches. Neat!

This does come with the side effect of increased disk space usage, so be mindful to delete your branches when you are no longer in need of it, this will keep your workspaces tidy in the interface and on the backend.

**Migrations**

So what happens if you alter a table on one branch, let's say you add some columns and delete some other columns, and then merge that into a branch without those alterations?

Well, whenever you make a change to the schema (structure) of a table, a migration is calculated behind the scenes and saved alongside the change to the model of the table. When you merge the branch you made changes on with a branch that does not have these changes yet, the VCS calculates which migrations need to be run and will then run through them sequentially, meaning the table on your target branch is then modified correctly to replicate the model on your source branch.

**Variables vs other Datastore data**

Within a datastore, there is a slight difference to how each type of variable is tracked and it's important to be aware of the differences.

The _name_ and _type_ of every variable is tracked, but the actual values (the _data_) is where the difference lies.

| Type | What is tracked? | Tool to transfer data |
| :-- | :-- | :-- |
| String, Number, Boolean, JSON, List, Bounding Box, Grid, Coordinates | Name, type and value | All properties tracked in VCS |
| Table | Name, type and table schema | Data transfer/export tool |
| View | Name, type and view configuration | Views don't have data, they draw from table data |
| Files | N/A | Data transfer/export tool|
| Password | Name and type | Requires manually setting |
| Identity | Name and type | Requires manually setting |

You may be wondering why do we track these differently and the answer comes down to how we have seen these different types used.
- Table data and files usually represent transient user driven data, should be unique per environment/branch
- Variables often represent configuration, booleans used to represent feature flags, numbers used to represent maximum number of retries and text used to represent templates used by automation
- Passwords and identities often represent environment specific API keys, passwords or 3rd party accounts

In the future we want to offer more granular control over which variables are tracked and which are not but these are the rules we have settled with for now.


### Data Transfer & Export

We recognise that you will often want to move data across your different Toca environments or even across your different branches. Each branch has it's own copy of a Datastore, this means you can do things like add columns, change column types, remove columns on a branch all without impacting the data on other branches. When you create a branch you'll be given an option to copy the data over from the origin branch. When you delete a branch it will also remove the data associated with that branch, so make sure you keep your branches tidy to avoid redundant data clogging up your system. If you want to copy data across your branches at another point in time, head to the Workspace menu and select the `Data tranfer` tool.

There is also a data export feature that allows you to export datastore table data and files in CSV, SQL or JSON format and you can then import it into your other Toca environments. This, in conjunction with the ability to push and pull, completely replaces the export & import feature in previous Toca versions. You can find the data export tool in the Workspace menu.


## Best Practices

### Working on a feature


### Promoting from one Toca platform to another


### Hot patching a live release
