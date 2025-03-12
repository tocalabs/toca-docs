# 7.9 - Release Notes

This is a small incremental release on top of the 7.8 release with a focus on bug fixes, improved error messages and performance.

## What's New

### General

#### Job Queues Explained

If you run a Workflow and your job is in the "Queued" state, you can now hover over the spinning queued icon and you will receive an explanation of why your job is queued.

![Job Queue Explanation](/src/assets/releases/queued_job.png)

#### App Error Levels

Once an app is deployed, there is always the possibility of errors being thrown when you attempt to fetch data from datachips. This could be because the permissions have changed and a user no longer has access to see the data or maybe the table being referenced in a Repeating Layout has been deleted. Previous to the 7.9 release, the App user would get a generic error message but now you can control how granular the error messages are for the end user. This new option can be found in App -> Settings -> Misc .

![App Error Levels](/src/assets/releases/app_error_levels.png)

#### Error Messaging

The error messages returned from particular areas of the platform have been improved to be more clear and more instructive on how to resolve the issue encountered.
The two areas which have been focussed on for this has been in the App Designer and then when adding Identities. We recognise these as two places where you are most likely to come across an issue so these have been our starting point for improving the error messages across the platform.

## Bug Fixes

A number of bug fixes were included in this release across the platform.
There was a particular focus on addressing bugs relating to perceived quality of the product.

Some noteworthy fixes include:
- Deprecated Identity Providers can now be reenabled
- New versions of TDK Components can now be created from any previous version, not just the latest version
- Updating default Activity input values no longer requires a refresh of your page
- App Slugs can now be reused after an app with the slug has been undeployed
- You can now rename Datastores
- You can now query job reports based on the new trigger type of _Recovery Workflow_

> Contact <support@toca.io> for a full list of bug fixes included within this release.

## Deprecated

- The Dynamic Services feature has been sunsetted and therefore removed from the Admin section of the platform.
- You can no longer download the activity console as a CSV

## Previous Releases

- :docs-link[7.8]{id="releases/7_8"}
- :docs-link[7.7]{id="releases/7_7"}
- :docs-link[7.6]{id="releases/7_6"}
- :docs-link[7.5]{id="releases/7_5"}
