# Building in the Toca Development Kit (TDK)

In the TDK you can build:
- Automation Actions
- Connectors
- App Components
- App Actions

This means that you can bring in new functionality into the platform whenever you want.

- Need your connectors to accept XML rather than JSON? _Just tweak the existing connectors._
- Need a new automation action that calculates the different between two pieces of text? _Build a new Diff Text action in C#._
- Want a menu component that can have a tree structure? _Build your perfect component using React._
- Have a use case for an IPL action that works out the time difference between two dates? _Use TypeScript to define exactly how you want the difference outputted._

The TDK allows you to further the automation capabilities by writing C# and you can further the app capabilities by writing React and TypeScript. You can do this all from the Toca platform, you don't need to install any other technology, no dependencies or libraries, simply open the TDK and get building!

Once you have developed your new functionality in the TDK, you can then build and deploy it to the main platform so that anyone can use it, we'll look at this on the next page. Lastly, if you want to share this functionality across other Toca platforms, you can then bundle it into a pack and publish it to a :docs-link[hub]{id="packs/packs"}.


## Extending Automation

### Building an Action

Let's take a look at building an automation action. There are three main components to an action:
- Inputs - _What inputs will the action have and how is the user going to specify them_
- Logic - _What is the action actually going to do_
- Outputs - _What is the action going to return as a result_

Let's build an action together to see how these three components interact, we'll build an action that takes a datetime and allows you to modify it by a unit of time. We shall call it: `Modify Datetime`!

Let's start by thinking about the inputs we're going to need from the user for the action to work. We'll need them to specify a datetime, the unit of time they want to modify it by and then the quantity for that unit of time. For example, the user might specify `2025-01-01T00:00:00Z` as the datetime, `days` as the unit of time and `+30` as the quantity. With these inputs we'd expect the returned output to be `2025-01-31T00:00:00Z`.

The inputs are specified by dragging the controls from the left hand panel onto the inputs panel. Once you have placed a control down you can configure it. One of the most important configuration values is the Parameters Value - this is the name given to the input that is injected into your action. Let's drag in our 3 controls and configure them.


Now that we have configured our three main inputs, we'll also add a "Fail on Error" checkbox, which tells the action how to behave if something goes wrong.


Now we have all of our inputs, lets focus on the code. Our C# code for this will be relatively simple:
```csharp
var date = DateTime.Parse(dateToModify);

DateTime modifiedDate;

switch (unit.ToLower())
{
    case "days":
        modifiedDate = date.AddDays(valueToAdd);
        break;
    case "hours":
        modifiedDate = date.AddHours(valueToAdd);
        break;
    case "minutes":
        modifiedDate = date.AddMinutes(valueToAdd);
        break;
    case "seconds":
        modifiedDate = date.AddSeconds(valueToAdd);
        break;
    default:
        throw new Exception($"Invalid Unit given: {unit}");
}

AddResult("modifiedDate", modifiedDate, ActionTypes.DateTime);
Action.Status = ActionStatus.Success;
```

The `AddResult` function is the mechanism by which the code can return an output for the action. To make sure that the result has a datachip which users can select, we can add an output to the outputs panel.


Now we've built our action, let's quickly test it to check it is behaving how we want it to. First, select a Bot from the bot panel, this will be the Bot that we can run our testing on. Next, flip the inputs into preview mode and enter some example inputs, then press the play button in the top right hand panel and check the console output. This will return any code errors but also return the result if it runs successfully so we can validate that our logic is correct.

Great, we've just built our first action! See the next page, Deploying from the TDK, to see how we get this action into the hands of the other Toca users.

#### Building Libraries with Action Helpers

When you build lots of Actions, you'll find yourself in a situation where you need to share functionality between actions, this is where helpers come in. You can think of a helper like a library, it is a C# class that you can define yourself and you can then import helpers into actions whereby you can instantiate the helper and call methods from it within your action.

### Building a Connector

Connectors allow you to turn your workflow into an API that anyone can use. However, before the data from the API request makes its way into the acitivities defined in your workflow, there is usually a bit of preprocessing that you want to do to the request. This might include checking an `Authorization` header or `API-Key` value, or parsing the query parameters or even just extracting specific values from the body to then pass through to the workflow. Connectors also allow you to define the response to the API request, including specific status codes, response body and headers.

A Connector is made up of:
- A Handler - This is a single block of code that handles the request when it first comes in.
- Responses - Each connector can have one or many responses, these contain blocks of code which define how the connector should respond.

Let's write a simple connector that takes in a JSON payload from a POST HTTP method and can return with a range of different status codes.

We'll start with the handler:
```csharp

```

We'll build a couple of responses which return different status codes so that users can branch their workflow to allow for returning different codes based on how the workflow progresses.

A 200 OK response:
```csharp

```

A 500 Internal Server Error response:
```csharp

```

Lastly, a 400 Bad Request response:
```csharp

```

## Extending Apps

### Building an App Component

App components are written using React and TypeScript. There are two main points to each app component, the `index.tsx` file, which is the entry point for the component when it runs and the `options.tsx` file which is responsible for rendering and understanding the properties for each component.

These components can import [NPM](https://npm.js) packages if you provide them with a `package.json` file at the root of your app component.

> **Note 📝**
>
> _Unlike automation actions, app components can have multiple files per component. Automation actions only have one file available to each action for you to define your logic._

There are also a series of imports that you can bring in from the Toca ecosystem to help you bring your component to life. These are all documented in the docs panel that exists on the right of the code editor, but the most important are:
- Theming
- Datachip handling
-

We'll build a simple app component that does xyz.

### Building an IPL Action

All IPL actions are developed using TypeScript.
