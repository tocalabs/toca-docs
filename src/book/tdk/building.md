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

#### Building Libraries with Action Helpers

### Building a Connector


## Extending Apps

### Building an App Component


### Building an IPL Action
