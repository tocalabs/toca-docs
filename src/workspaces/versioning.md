# Versioning

## Changes

When you create, update, or delete entities (eg activities, workflows etc.) in a workspace, these appear as `changes`. You can leave ithem like this, but is has some drawbacks:

* Changes are only in the database - the versioning system doesn't know about them yet.
* Multiple changes to the same entity will be grouped together as a single change - there is no way to know how many times it has been changed, or by whom.

When a branch has changes you will see it in a few places in the user interface: in the bottom bar, in the version control panel of the main sidebar, and on the workspace homepage.

### Diffing a change

If an entity has a change, you can see a diff between it and the committed version of the entity either by clicking on the version information in the bottom right of the screen, or by clicking on the change in the version control panel. The diff will show you the properties that have changed.

### Discarding changes

If you want to undo a change (before it has been committed) you can do so via the version control panel. Each change will have the option to `Discard change`. This will discard the change and revert it to the last committed version of the file.

## Commits
fix
Once you have finished creating, updating, or deleting an entity (or multiple entities) you can commit the change. This will associate the change with a specific user, a date, and a commit message describing what and/or why the change was made. To commit change do the following:

1. Go to the version control panel (and expand the `Changes` panel if the workspace has a remote repository)
2. Select which changes you want to commit. You can commit as many (or as few) changes as you wish in a single commit.
3. Write a message describing what changes you have made and why. It is not always obvious what the purpose of a change was from the data alone, so a good commit message can be very important.
4. Click `COMMIT`. If you're workspace has a remote repository you will also have the option to `COMMIT & PUSH` which is recommended to keep the remote up-to-date.

### Commit history

You can see a list of commits for your current branch via the `History` option in the version control panel `more` menu. Clicking on a commit will show you a list of all the changes associated with that commit, and you can select entity to see the difference.

You can see the same list of commit but for a specific entity by clicking on the version information on the bottom right of the screen. (If the entity has changes it will take you directly to a diff view).

### Pushing and pulling commits

If your workspace has a remote repository you can push commits you have a made to the remote, and pull commits made in other environments. :docs-link[Read more about remote workspaces]{id="workspaces/remote"}.