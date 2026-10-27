# 10.0: Odin - Release Notes

Introducing version 10 of Toca – a paradigm shift in the way you manage and version your Toca workspaces. The old publish states and import/export have gone, replaced with a full Git integration.

This release is also jam-packed with other new features so if you don't have time to review all the changes now remember you can always get back to this intro via your user profile -> Misc.

## What's New

### Workspace Versioning

In any complex environment, having a full audit trail of who changed what when is very powerful. Having the ability to revert back to a previous snapshot in time for your work. Being able to back up your workspace to a 3rd party server. That is the promise of Toca's new Version Control System (VCS). Out goes the _Draft/Published/Previous_ states and in comes our Git based VCS. With this change, there is a new bottom bar that now underpins every screen in Toca offering you easy access to the most common version related features.

You can find out more about the new VCS :docs-link[here]{id="book/general_concepts/versioning"}.

#### Migration of existing projects

In order to seamlessly update your workspaces to the new VCS, a migration has taken place under the hood whereby all:
- Draft resources now live in a branch called `dev`
- Published resources now exist in a branch called `main`
- Previous resourced reside in the `legacy` branch

### New App Explorer

The explorer panel in the App Designer has had a big visual uplift and now supports a host of new useful features such as:
- Component search
- Improved performance on larger pages
- Highlight strip
- Right click context menu

Be sure to check it out!

### Passkey authentication

There is now a new way to sign into your Toca platform, you can use a _Passkey_. A passkey is a passwordless alternative and they typically use biometrics, PIN codes or push notifications to authenticate your user. You can configure a passkey for your account in your Profile section of the platform.

> Passkeys are enabled platform wide in the Security page of the Admin section.

### Flexible Table views

Views now support a few new features which make them much more useful and easier to work with. These are:
- Ability to use functions in the `GROUP BY` and `HAVING` sections
- Free-form inputs when you're crafting your column definitions: combine columns, functions and free text in a single input.
- We have also improved the View interface so that you can now sort and query it directly from the Datastore page.

### Retention Periods

If left unattended, your Toca platform can start to consume quite a lot of disk space. This is usually due to the hundreds of thousands of reports which are generated each time a workflow runs. 

To keep these reports in check, a workflow now has a _retention_ period setting. This allows you to have granular control over how long each workflow's reports will be kept on the system. The default is 30 days so if you want your data to stick around for longer than that then make sure to edit the relevant workflow settings!

### Various Quality of Life improvements

#### User roles simplified

A user can now have up to 3 roles:
- Developer
- TDK Developer
- Administrator

This replaces the complex roles system that existed before. Each user will be accurately migrated to the new roles automatically.

#### Querying tables for null

You can now query for `NULL`  values much more easily when you select the `IS` or `IS NOT` operator in the query builder.

We have also made improvements to the table query builder in the App Designer. The user can now define what ought to happen if part of their query cannot be resolved. This allows you to build in much more predictable behaviour for your app.

#### Pin Admin pages to main navigation panel

When you are an administrator of a Toca platform, there are pages you will frequently visit such as the **Admin > Bots** page or the **Admin > Users** page. It can become annoying having to go to the Admin section just to open these pages. Now though, you can pin specific pages to your main navigation panel so you can instantly access them. _Look out for the pin icon next to each page in the Admin section!_

#### Right click context menus

You can now right click on the platform in most places to perform an action. Try right clicking in the following places:
- On the list of your activities
- On the explorer panel in your App designer
- On the Automation header in the main navigation panel


## Bug Fixes

A number of bug fixes were included in this release across the platform.

> Contact <support@toca.io> for a full list of bug fixes included within this release.

## Deprecated

Project / App Export and Import has been deprecated and replaced with the new Workspace VCS and Data Export/Import tools. You can find out more about how this works by reading our :docs-link[VCS page]{ id="book/general_concepts/versioning" }.

--- 

You can read about these features in more detail by going to the Misc section of your Profile page and pressing the play icon next to the word "Odin".

**Happy Building!**

---

## Previous Releases

- :docs-link[9.0]{id="releases/9_0"}
- :docs-link[8.2]{id="releases/8_2"}
- :docs-link[8.1]{id="releases/8_1"}
- :docs-link[8.0]{id="releases/8_0"}
- :docs-link[7.10]{id="releases/7_10"}
- :docs-link[7.9]{id="releases/7_9"}
- :docs-link[7.8]{id="releases/7_8"}
- :docs-link[7.7]{id="releases/7_7"}
- :docs-link[7.6]{id="releases/7_6"}
- :docs-link[7.5]{id="releases/7_5"}
