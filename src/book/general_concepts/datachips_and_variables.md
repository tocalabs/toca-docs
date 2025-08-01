# Datachips and Variables

Datachips are the core mechanism in Toca for utilizing values that originate from external sources, such as a Datastore or the output of a previously executed automation action. Visually, Datachips are represented by small, color-coded "chips" (hence the name\!). Each chip clearly displays its corresponding data type and name.

For a deeper dive into data types, you can refer to the article on :docs-link[data types]{id="book/general_concepts/data_types"}.

Here are some examples of what Datachips look like:

| Datachip Example | Description |
| :--------------- | :---------- |
| :datachip-variable[my_number_variable]{type="Number"} | This pink datachip represents a variable of type `Number`, named `my_number_variable`. |
| :datachip-action[action_result]{type="Boolean"} | This green datachip represents a `Boolean` result from an automation action. |
| :datachip-datastore[datastore_variable]{type="Table"} | This blue datachip represents a `Table` value stored in a Datastore. |

A Datachip can represent either a static result or a variable. We'll explore the distinction between these two later in this article, along with how and where you can effectively use these chips throughout the Toca platform.

## Datachips

### Where You Can Use Them

You can use a Datachip in Toca wherever you see the `{X}` icon in an input field. Clicking this icon allows you to select the source of your Datachip. Datachips are typically usable in any input field you encounter within both Automation and Apps.

Let's explore the specific contexts where you can use Datachips and their origins.

#### Automation

Within Automation projects, Datachips are primarily used in two places: as inputs to actions and as inputs to both exclusive and trigger nodes in a workflow.

In **activities**, you can select a Datachip from the following sources:

  * **Datastores:** Use a value stored in a Datastore linked to your project.
  * **Activity Inputs:** Access any inputs injected into your Activity when it starts.
  * **Activity Variables:** Utilize a variable created throughout your Activity.
  * **Action Results:** Use an output from any action that precedes the one you are configuring.

Let's see how this works from the Activity Designer:

*[Consider adding an image or GIF here demonstrating the selection process in the Activity Designer.]*

In **Workflows**, you can select Datachips from these sources:

  * Datastores
  * Workflow Inputs
  * Activity Outputs

#### Apps

In Apps, Datachips are primarily used in two main areas:

  * App Component properties
  * App Action inputs

This capability allows you to dynamically configure your app components, including their content and appearance, using values sourced from elsewhere in the platform. It also enables you to reference values, such as Datastore variables, within your App actions, allowing you to build In-Page Logic (IPL) flows that might, for example, directly add a row to a Datastore table.

Selecting a Datachip in Apps is very similar to Automation. Look for any field with a `{X}` button. When you click it, a small window will appear, displaying all available Datachip sources:

  * **Datastore:** Use a Datastore variable from any Datastore linked to your App.
  * **User:** If the app is authenticated, you can select Datachips representing information about the current user.
  * **Form Result:** Use results returned from workflows triggered by listeners on the current page.
  * **URL Query:** Any query parameters passed into the URL of the current page.
  * **Context:** (Shown if context is available, typically from a dynamic page or data-driven layout component.)
  * **In Page Value:** Any In-Page Values (IPVs) defined within the App's IPL flows.

### How You Can Use Them

Datachips are often used to represent the entire value for a particular field. However, in some cases, they can also be used inline with text. While typically applicable only to text fields, this can be a powerful tool.

For example, imagine you are making a series of API calls. If you have the base URL stored as a variable like :datachip-variable[base_url]{type="String"}, you can then append the API route directly after this variable. The ability to interpolate a Datachip within text fields offers significant flexibility.

## Variables

Datachips represent two types of values: static values, which remain constant, and variable values, which can change.

In Automation, values that can change are called **Variables** and are denoted by a pink Datachip. In Apps, values that can change are called **In Page Values (IPVs)**. These variable values are incredibly useful as they allow you to update a value dynamically as a block of logic executes.


## Subchips


Subchips allow you to drill down into the value behind a datachip and extract a specific item within that value. This can be incredibly powerful when dealing with more complex data objects such as lists, JSON or tables. This allows you to do things such as get an individual item in a list or a cell from a table.

When you pick a datachip, if it is a type that supports subchips then look out of the little chevron. Click on the chevron and it will open the subchip selector for that type, each type has it's own subchip selector so for a list you can choose what position in the list you want to fetch your item from, for a table you can select what column/row/cell you want and for JSON you can select which property you would like. Use the selector to specify what you want and this will then place down a datachip but the text inside the datachip will denote that you have opted to specify a subchip.

You can use subchips in both automation and apps, this versatility means you can avoid having to add extra steps of logic to extract these inner values. Wherever you can select a datachip in the platform, you'll be able to take advantage of subchips.

The main types that subchips are useful for are:
* **Tables:** You can select an individual cell, a row or a column
* **List:** You can select an individual item at a specific position in the list
* **JSON:** Use [JSONPath](https://en.wikipedia.org/wiki/JSONPath) syntax to select a node in your JSON value

You can also use subchips in the following other types but typically you'll come across this less unless you're doing a lot of desktop automation:
* **Bounding Box:** Get the X, Y, Width or Height properties
* **Coordinates:** Extract the X or the Y property
