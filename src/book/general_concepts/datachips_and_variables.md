# Datachips and Variables

Datachips are the mechanism in Toca for using a value that has come from elsewhere, be it from a Datastore or a previously run automation action. Datachips are visually represented by little chips (hence the name!) and they are colour coded and contain the corresponding :docs-link[data type]{src="book/general_concepts/datachips_and_variables"} as well as the name of datachip.

Here are some examples of what they look like:

| Datachip Example                                      | Description                                                                                                 |
| :---------------------------------------------------- | :---------------------------------------------------------------------------------------------------------- |
| :datachip-variable[my_number_variable]{type="Number"} | This pink datachip represents a variable which is a Number type and it is called `my_number_variable`.      |
| :datachip-action[action_result]{type="Boolean"}       | This green datachip represents a result that is the output of an automation action which is a boolean type. |
| :datachip-datastore[datastore_variable]{type="Table"} | Lastly, this blue datachip represents a value that is stored in a datastore which is a table.               |

A datachip can represent either a static result or a variable and we'll learn the difference between these two later on in this article. We'll also take a look at how and where you can use these chips throughout the platform.

## Datachips

### Where you can use them

You can use a datachip in the platform anywhere you see a `{x}` in an input field. Once clicked, you can then choose where to get your datachip from. You can typically use a datachip in any form of input field that you come across in both Automation and Apps.

Let's take a closer look at where you can use datachips and also where they can come from!

#### Automation

In Automation projects, there are two main places you can use datachips; these are as inputs to actions and also as inputs to both exclusive and trigger nodes in a workflow.

In activities, you can select a datachip from the following places:
- Datastores - Use a value that is stored in a Datastore which is linked to your Project
- Activity Inputs - Any inputs which are injected into your Activity when it starts can be accessed by any action
- Activity Variables - Use a Variable that has been created throughout your Activity
- Action results - Use an output from any Action which precedes the one you are selecting a datachip for

Let's have a look at how you go about this from the activity designer:


In Workflows you can select datachips from the following places:
- Datastores
- Workflow Inputs
- Activity Outputs



#### Apps

In an app, there are two main places you can use datachips:
- App Component properties
- App Action inputs

This allows you to drive the configuration for your app components, including their content and how they appear, from values which come from elsewhere in the platform. It also allows you to reference values such as datastore variables inside your app actions so you can build an IPL flow which might add a row directly to a datastore table.

In apps, the way you select a datachip is very similar to doing so in automation. Look out for any field which has a `{X}` button and when you select that, you will be presented with a small window that shows you all the places you can select a datachip from. These places are:
- Datastore - _Use a datastore variable from any datastore that you have linked with your App_
- User - _If app is authenticated, you can select datachips which represent information about the current user_
- Form Result - _Use results returned from workflows triggered by listeners on the current page_
- URL Query - _Any query parameters passed into the URL of the current page_
- Context - _Shown if there is context available, usually from a dynamic page or data driven layout component_
- In Page Value - _Any in page values defined in the IPL flows of the App_


### How you can use them

Datachips are often used to represent the whole value for a particular field but in some cases they can also be used inline along with text. This is often only applicable to text fields, but when possible it can be a powerful tool. Imagine you are making a series of API calls and you have the base URL as a variable :datachip-variable[base_url]{type="String"}, you then want to add the API route after the base URL variable. The ability to interpolate a datachip in text fields can be truly powerful.

## Variables

Datachips represent two types of value: a static value that will not change and a variable value, one that will change. In automation, values that can change are called Variables are denoted by a pink datachip. In apps, values that can change are called In Page Values. These variable values are extremely useful as it allows you to update a value as you run through a block of logic.


## Subchips
