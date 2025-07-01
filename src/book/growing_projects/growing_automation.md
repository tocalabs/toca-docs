# Growing Automation Projects

When your automation project starts to grow, there are a usually a couple of things that you start to feel:
1. Individual activities and workflows can get too large
2. There is often reusable behaviour stuck inside larger activities or workflows

Luckily, there are several tools and features which help to deal with both of these things.

## Exclusives in Workflows

Activities are not the only place in automation that you can add flow control logic, you can also add decision points and even implement loops within a Workflow. This means that if you are looping over a large list or table of data in your automation, you don't just have to put all of this logic inside a single looping action in an activity. You can extract this control flow to the workflow level, allowing you to break your activities up into smaller and more manageable pieces. This is why :docs-link[exclusive nodes]{id="projects/automation/workflows/exclusive"} in workflows are so powerful!

### Decision Points

Exclusive nodes allow you to specify conditions on each branch that leaves the node so that you can specify under which scenario each branch should be executed. This is similar to the :docs-link[If Then action]{id="IfThen" type="Action"} but the difference being that you can specify multiple different branches of execution with an exclusive.

The benefit of this is that it allows you to break up what might be a large activity with lots of If Then actions into lots of smaller activities where the conditional flow of execution is handled by the Workflow. Breaking up your activities into smaller units of automation can be beneficial as it gives you the option of reusing these smaller, less niche activities in other workflows.

To create a decision point in a workflow, drag an exclusive node onto the workflow and draw all the possible paths of execution that could follow on from the exclusive node. When you click on the exclusive node, you'll then see in the properties panel on the right hand side a list of text boxes which allow you to define the conditions that need to be met for each branch. Define your conditions by righting an evaluation statement such as: Left Hand Side (LHS) == Right Hand Side (RHS).

> **Note 📝**
>
> If you have multiple conditions which are met in an exclusive then it will only go down the branch for one of them. Due to this, you probably shouldn't rely on this behaviour.

### Looping

You can also use exclusive nodes to define loops in your workflow by drawing one of the paths from your exclusive to an activity that preceeds the exclusive node. This allows you to repeat activities multiple times in a workflow until your loop is complete and you reach another condition. This saves you from having to have a single looping action in activity (such as :docs-link[For Each]{id="ForEachV2Copy" type="Action"}, :docs-link[For Each Row]{id="ForEachTableRow" type="Action"} or :docs-link[For Each JSON Object]{id="ForEachJsonObject" type="Action"}) with many actions nested beneath it. Instead, you can divide the behaviour that should happen inside the loop into several smaller activities and then configure your workflow to do the loop.

To set up an exclusive in such a way that it should loop, you need to set up your exclsuive as you would normally but one of your paths should point to a node that preceedes the exclsuive node and then you should have another path with a break condition on it, i.e. a condition that means the workflow will exit the loop. Think your conditions through and make sure that you haven't built a loop that will run forever!

> **Note 📝**
>
> _Looping at the Workflow level will perform each loop a bit slower than doing it at the activity level but provided you are not doing something time critical, in most scenarios this will still run fast enough to be practical.

## Run Workflow


## Copy Activity to Project
