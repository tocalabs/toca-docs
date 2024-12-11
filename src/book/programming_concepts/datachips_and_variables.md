# Datachips and Variables

Datachips are the mechanism in Toca for using a value that has come from elsewhere, be it from a Datastore or a previously run automation action. Datachips are visually represented by little chips (hence the name!) and they are colour coded and contain the corresponding :docs-link[data type]{src="book/programming_concepts/datachips_and_variables"} as well as the name of datachip.

Here are some examples of what they look like:

| Datachip Example | Description |
| :--: | :--- |
| :datachip-variable[my_number_variable]{type="Number"} |This pink datachip represents a variable which is a Number type and it is called `my_number_variable`. |
| :datachip-action[action_result]{type="Boolean"} |This green datachip represents a result that is the output of an automation action which is a boolean type. |
| :datachip-datastore[datastore_variable]{type="Table"} |Lastly, this blue datachip represents a value that is stored in a datastore which is a table. |

A datachip can represent either a static result or a variable and we'll learn the difference between these two later on on this page. We'll also take a look at how and where you can use these chips throughout the platform.

## Datachips

### Where you can use them

You can use a datachip in the platform anywhere you see a `{ x }` in an input field. Once clicked, you can then choose where to get your datachip from. You can typically use a datachip in any form of input field that you come across in both Automation and Apps.

Let's take a closer look at where you can use datachips and also where they can come from!

#### Automation

In Automation projects, there are two main places you can use datachips; these are as inputs to Automation Actions and also as inputs to both Exclusive and Trigger nodes in a Workflow.

In automation activities, you can select a datachip from the following places:
- Datastores - Use a value that is stored in a Datastore which is linked to your Project
- Activity Inputs - Any inputs which are injected into your Activity when it starts can be accessed by any action
- Activity Variables - Use a Variable that has been created throughout your Activity
- Action results - Use an output from any Action which precedes the one you are selecting a datachip for

In Workflows you can select datachips from the following places:
- Datastores -

#### Apps

### How you can use them

#### Interpolation



## Variables

### Mutable vs Immutable
