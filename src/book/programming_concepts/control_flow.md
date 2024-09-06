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

#### Workflows

### Conditional App Behaviour

#### App Components

#### In Page Logic

## Looping

![Looping Diagram](/src/assets/book/looping.png)

### Count Controlled Loops

### Condition Controlled Loops

### Collection Controlled Loops

### Early Exit from Loops
