# Stash and Pop

Stashing your changes allows you to move your current set of uncommitted changes out of a branch and into a store from which you can _pop_ it later.

## Stashing

You can think of stashing as taking the changes out of your branch and putting it is a _save for later_ pile. At any point in the future you can look back at your _save for later_ pile and re-apply those changes.

Reasons you may want to stash your changes:

- You made changes to the wrong branch and want to move them to the right one.
- You want to merge changes into your current branch and want to do it with a _clean_ branch.
- You want to quickly test your branch without your changes, but also without have to discard them.

To stash your current uncommitted changes simply select `Stash` from the versioning menu.

You can stash as many times as you like – each stash will be a separate item with it's own list of file changes, metadata and message.

Stashes are branch-agnostic (i.e. they're listed with other stashes even if they're from other branches) but specific to a workspace and environment – you cannot use stashing to move data to another workspace or environment.

## Popping

Popping is simply re-applying the changes from a stash onto your current branch.

To pop a stash simply select `Pop` from the versioning menu. All of the stashes from your current workspace will be listed, and all of themgit can be _popped_ onto your current branch via the `Pop stash` button. You can also see a list of the file changes for the stash and diff them against the version on your current branch.

Stashes are branch-agnostic – they can be applied to _any_ branch, so it's a good way to transfer changes from one branch to another without having to commit them.

Stashes can be popped onto a _dirty_ branch (i.e. a branch with uncommitted changes) but they will fail if there are any conflicts (typically when the same entity has been modified in both places). Conflicts may still occur if the branch is _clean_ but in this case you will be given the option to resolve them.
