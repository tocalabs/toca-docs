# 7.10 - Release Notes

The theme of this release is all around productivity! The release brings in a lot of new functionality that enhances existing features within the platform, making it easier and faster to build things!

## What's New

### Apps

#### Translations

Multilingual Apps are now natively supported in Toca! 🌍
With this new feature, you can now add support for multiple different languages in your Apps by defining translation tables and then using Translation Datachips to represent the text to be translated in the app components.

#### Data Sidebar

The App Designer now has a Data sidebar that allows you to drag datastore tables & views, as well as listeners, directly onto the page you're designing. This will then take you through a wizard which will attempt to automatically place the corresponding components down for you. For example, if you drag a listener onto the page from the Data sidebar and the listener has inputs with types text, datetime and file then the wizard will suggest a Text Field component, a Date and Time picker and a File Uploader.

#### Layout Standard Library

#### App Login Redirect

App users will now be automatically redirected to page of an App they were originally trying to access, even if they needed to log into the App. This means that you can send an App user a link to a specific page of the App and after they have logged into the App, they will be directed straight to the page the link pointed to.

#### IPL Minimap

Your In Page Logic flows are now much easier to navigate with a minimap that can be dragged or scrolled to move along your flow.

#### New Components

**Carousel**

**Custom Button**

**Stepper**

**Calendar Component**

### Automation

#### Data Processor Generative AI

**Explain Flow**

**Build Assistant Flow**

#### Table Automation Wizard

Whenever you create a Table in a Datastore, you most likely also need some automation to go along with it that will add data, update data, fetch data and delete data in your table. This pattern of automation is found in almost every automation project which contains a Datastore with tables. This feature aims to speed up the development of this Create, Read, Update and Delete (CRUD) automation.

The wizard will take you through several steps, allowing you to specify what behaviour you'd like to automatically generate the automation for

#### Workflow Auto Sort

Tired of rearranging your Workflow so that it looks neat and the lines are all aligned correctly?

Well, now you no longer have to! There is a new button in the Workflow Designer that will automtically tidy your Workflow up for you.

#### Email Action Enhancements

The :docs-link[Send Email]{id="SendEmail", type="Action"} (v2+ onwards) action now allows you to send an email to multiple people, cc, bcc and add attachments. This is a big improvement as previously you could only use the email to send an email to a single inbox and it did not support attachments or cc'ing & bcc'ing people.

#### Workflow Minimap

### General

#### Global Documentation Search

#### Pipeline Storage Improvements

Pipeline/Reporting Data is now stored much more efficiently, leading to it taking up less disk space when it is stored and additionally it should be much quicker to delete this data.

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

Nothing has been deprecated in this release.

## Previous Releases

- :docs-link[7.9]{id="releases/7_9"}
- :docs-link[7.8]{id="releases/7_8"}
- :docs-link[7.7]{id="releases/7_7"}
- :docs-link[7.6]{id="releases/7_6"}
- :docs-link[7.5]{id="releases/7_5"}
