# Control Flow

When building out the logic in your application, there are two main building blocks that are incredibly useful. The first is the ability to control which block of logic is executed based on a condition. The second is being able to repeat a block of logic until a condition is met.


## Making Decisions

![Making a Decision](/src/assets/book/conditional.png)

Being able to make your application behave differently based on the outcome of a condition is incredibly useful for both Automation and Apps. Imagine you have some automation which is going through a table of students and your automation needs to sort each student into a school house. Conditional logic makes this really easy as we can create a set of conditions based on the traits of each student.

Below is an example of how this might work:

```python
if "bravery" in student.traits:
    house = "Gryffindor"
if "loyaltly" in student.traits:
    house = "Hufflepuff"
if "intelligence" in student.traits:
    house = "Ravenclaw"
if "cunning" in student.traits:
    house = "Slytherin"
```

In Apps, this is useful because you might want to hide or obscure parts of your application based on a condition. For example, you might only want to make a button clickable if a user has previously ticked the option to accept the Terms & Conditions of your application.

### Conditional Automation

#### Activities

We've actually already seen how you can implement conditional logic in Automation when we built our :docs-link[Guessing Game]{id="book/guessing_game"}. In that example, we used conditional logic to check a user's guess to see whether it was higher, lower or equal to the number they had to guess so that we could return a useful message to the user. Let's quickly revisit that and dive into the `If Then` action.

The :docs-link[If Then]{id="IfThen" type="Action"} is the most common way to introduce decisions into your automation activities. It allows you to specify a condition and then nest actions underneath it which will only be run if the condition is true.

:video{src="/src/assets/book/ifthen_conditional.webm"}

In the clip above, we can see that we create a number variable equal to 25, and we then add an If Then action to check whether our number is greater than 25. We then placed a Stop Activity action down and importantly we nested this action underneath the If Then. This means that it will only run the Stop Activity action if the condition is evaluated to true.

The first time we run it, it does not run the Stop Activity action and we can see the result of the If Then is false. Once we change the value of our number variable to 26, this means the condition now evaluates to true and the Stop Activity action runs as expected.

> **Note** 📝
>
> It can be useful to perform the some conditional logic if a condition is _not_ true, this is usually referred to as an `else` statement, i.e. if condition is true do this, else do this other thing. Whilst there is no specific Else action, there is a way you can achieve the same effect using the result of an `If Then` action.
> :video{src="/src/assets/book/ifthen_else_conditional.webm"}

#### Workflows

You can also introduce decisions to your Workflows, this allows your workflow to travel down different paths of execution and run different activities. In a Workflow, you will usually be checking the output of an activity to make that decision. To add conditional logic to your workflow you need to add an :docs-link[Exclusive node]{id="projects/automation/workflows/exclusive"} and then connect the exclusive up to two or more outcome paths. This will allow you to provide a condition for each path of execution.

:video{src="/src/assets/book/ifthen_workflow.webm"}

> **Warning** ⚠️
>
> If more than 1 condition evaluates to true in an exclusive, it will only execute the first condition that it evaluates to true, so don't rely on this behaviour. You can avoid this by always making sure that all of your conditions are _exclusive_! Additionally, if none of your conditions evaluate to true, the Workflow will stop there and error.

You can also have your Workflow travel down a default path of execution if none of the conditions evaluate to true. To do this, you simply need to use the `else` keyword in your exclusive condition.

![Else Exclusive Workflow](/src/assets/book/else_workflow.png)

The above example would travel down the `else` branch if :datachip-variable[my_number]{type="Number"} is 25 or less.

### Conditional App Behaviour

You can add conditional behaviour to your Apps as well, this is particularly powerful if you want to conditionally show and hide components on a page. You can implement conditional logic in Apps at both a component level and within In Page Logic (IPL).

#### App Components

The most common way of conditionally showing / hiding content on your App page is to use the :docs-link[Conditional content]{id="55d766c9-5879-418f-83b0-853436362769" type="AppComponent"} component. This component will only display the components that you nest inside it if the condition that you set is true.
Let's see this in action with some basic conditions:

:video{src="/src/assets/book/conditional_content.webm"}

In this simple example, we are using the Conditional Content component to control whether we display some text content or not, we are then previewing the App with different conditions to check that it is working.

The Conditional Content component becomes really powerful when you start to use datachips in your condition so you can drive the condition dynamically.

#### In Page Logic (IPL)

If you have got some IPL on your App page and you need to introduce a decision point to your logic then the IPL mechanism for this is an _exclusive_ node, just like a Workflow in Automation! The exclusive node in IPL works very similarly to the one in a Workflow in that you link it up to 2 or more possible execution paths and you place a condition on each execution path, and whichever ones evaluate to true will be travelled down.
Let's take a look at how that might work with a basic example where we'll generate a random number and then update the text on a button depending on if the random number is higher or lower than a threshold value.

:video{src="/src/assets/book/ipl_exclusive.webm"}

As we can see from the above video clip, after clicking on the button a number of times, we get different labels.

## Looping

![Looping Diagram](/src/assets/book/looping.png)

Being able to repeat some logic for a set number of times can be very useful. Imagine you need to multiply every number in a table column by 100 to turn it into a readable percentage, to do that you would need to loop over each row in the table, mutliply the existing cell and update it once multiplied. The logic to multiply the number and update the table cell will be the same for every row in the table, so it would be great if we could repeat that logic for every row in a table without having to duplicate our logic. Fortunately, that is exactly what loops allow us to do!

Ultimately, all loops will repeat until a particular condition is met but as you'll find, there are many ways of configuring that condition.

### Count Controlled Loops

The easiest type of loop to understand is a count controlled loop, this is a loop that will repeat {x} times. The most obvious example of this is the :docs-link[Repeat]{id="Repeat" type="Action"} action which allows you to specify a repeat number and any actions nested underneath the Repeat action will be repeated that many times. This can be useful in scenarios where you know you need to do something a definitive number of times.

### Condition Controlled Loops

### Collection Controlled Loops

### Early Exit from Loops
