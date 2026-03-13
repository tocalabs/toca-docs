# Remote workspaces

Remote workspaces allow a workspace to be used on more than 1 environment. This is done via a Github repository: changes on one repository can be pushed to the remote repository so they can be pulled onto another.

## Connecting a workspace to a remote

You can connect an existing workspace to a remote repository OR connect to the remote as part of the workspace creation process. In either case you should follow the following steps:

1. Log in to Github and create a new blank respository.
2. Navigate to Github profile -> Settings -> Developer settings -> Personal access tokens -> [Fine-grained tokens](https://github.com/settings/personal-access-tokens). Here create a new token linked to the repository and store it somewhere safe (you cannot retrieve it later so make sure you save it now). Give the token the following permissions:
  * **Administration:** Read-only
  * **Contents:** Read and write
  * **Metadata:** Read-only
3. Either create a new workspace or use the workspace menu on an existing workspace and select `Add remote repository`.
4. Input the repository URL (we will validate it)
5. Input the token in the SSH key field
6. Click connect.

> This can take some time - if it takes longer than 30 seconds (or you close the modal) we'll send you a notification once it's complete.

After successfully connecting to a remote you will see some extra features appear in the user interface.

## Pushing and pulling commits

Once a workspace if configured with a remote you can push committed changes to the repository. Ideally commits should be pushed immediately to avoid conflicting commits from different environments (although you _can_ push commits at any point). Once a commit has been pushed to the remote repository it becomes available to all other environments using that workspace to pull from the remote.

* To **push** commits go to the version control tab in the main sidebar and expand the `Commits` panel and click the `PUSH` button. Alternatively selected `COMMIT & PUSH` when committing a change.
* To **pull** commits from the remote go to the version control tab in the main sidebar and expand the `Remote` panel and click the `PULL` button.

## Using a remote workspace on another environment

The purpose of using remote workspaces is so you can clone that workspace into multiple environments. To clone an existing remote workspace onto another environment follow these steps:

1. Open the workspace menu and select `New workspace`.
2. Switch to the `FROM REMOTE` tab.
3. Input the repository URL and SSH key
4. Press `CONNECT`.

> This can take some time - if it takes longer than 30 seconds (or you close the modal) we'll send you a notification once it's complete.