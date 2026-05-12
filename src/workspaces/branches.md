# Workspace branches

Workspaces are versioned using branches. Every workspace will have 1 or more branches, each independent of the other. Automation and apps can be created or updated on one branch without affecting other branches.

## Main branch

Workspaces are created with a `main` branch. This is a special branch - it is the default branch, intended for your production apps and automations. Some features (such as scheduled workflows) will only run on your `main` branch, while other actions (such as app deployments) can be run from any branch.

## Other branches

In addition to the `main` branch your workspace can have as many other branches as you wish. These other branches can be used to develop new apps and automation without affect your `main` branch.

For example you may wish to create a new branch for each new feature you develop, deleting the branch once the feature is merged into `main`. Or you may have a `dev` branch which you use for all your development, merging into `main` periodically. You could even combine the two by having single-feature development branches which are merged into a `beta` branch for testing before going into `main`.

You can also use branches to create snapshots of your branches, making it easier to revert back to previous versions of a workspace, or so you can reference older versions more easily.

### Creating new branches

To create a new branch you need to pick one of the workspace's existing branches to _fork_. The new branch will be cloned from the existing committed version of that existing branch. You can do this via the `more` menu on the version control panel.

> When forking we will use the committed version of branch. **Uncommitted changes will be ignored.** 

### Merging branches

There are lots of reasons you will want to merge branches. For example:

* You have completed development on a new feature and want to push it into your `main` branch
* You want to test features from 2 branches to ensure they work together
* You want keep a development branch up-to-date with changes that have been merged into you `main` branch (good practice to avoid merge conflicts with long-running development)

You can merge branches using the `Merge branch` option in the `more` menu on the version control panel:

1. You will be prompted to select a `Target branch`. This is the branch you want to merge INTO another branch (eg the development branch you want to merge into `main`).
2. Select the `Destination branch`. This is the branch you are merging into (eg in the above example this would be `main`).
3. Decide if you want to delete the target branch after the merge.
  * For example if this branch was created _just_ for developing the new feature you're merging in you may want to delete the branch to avoid it continuing to appear in the UI.
  * However if you want the branch to remain after the merge (eg if it's a generic `dev` branch you're doing lots of development in) then don't select this option.
4. Click the `CREATE` button.

### Merging conflicts

Occasionally a conflict will occur when attempting to merge 2 branches. This typically happens when an entity (an activity, app page etc.) has been modified in both branches since the newer branch was created. If a conflict occurs during a merge you have the following options:

* **Use target branch version** When a conflict occurs it will use the version of the entity that exists in the target branch. The version in the destination branch will be overwritten.
* **Use destination branch version** When a conflict occurs it will use the version of the entity that exists in the destination branch. The version in the target branch will be ignored.
* **Advanced** If the workspace has a remote reprository you can use a Git client or IDE to perform a manual conflict resolution.