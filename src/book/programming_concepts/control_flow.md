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



### Conditional Automation

### Conditional App Behaviour

#### App Components

#### In Page Logic

## Looping

![Looping Diagram](/src/assets/book/looping.png)

### Count Controlled Loops

### Condition Controlled Loops

### Collection Controlled Loops

### Early Exit from Loops
