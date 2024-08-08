# Building a Guessing Game

We're going to jump straight into building and deploying an application in Toca by building a guessing game. This will introduce you to a few common concepts by using them in a real world project such as implementing decision logic and building Apps.

We're going to implement a classic beginner project: a guessing game. Here are the rules: the program will generate a random number between 1 and 100 and the user will attempt to guess the number. If the guess is too low or high, the application will indicate as much. If the guess is correct, it will report back with a congratulatory message and give you the option to start a new game.

## Setting Up a New Project

This project will require both an Automation project and an App project, the automation will keep track of the user's guesses and the App will act as the interface that the user interacts with.

### Automation

Head on over to the projects page and create a new Automation project, give it an appropriate name so you can easily find it in the future.

:video{src="/src/assets/book/create_automation.webm"}

For our automation, we're going to need it to do a couple of things:
- Generate a random number between 1 and 100 and store it somewhere
- Check the users guess and compare it to the generated number and indicate whether the guess is too high, too low or correct.

Let's get started by creating an Activity, and we'll assign the activity to a Stateless bot as none of the automation we are building requires a Desktop environment. The first activity we create will generate and store our random number.

:video{src="/src/assets/book/create_activity.webm"}

> #### Action Groups
>
> If this is the first time you've opened an Activity, you'll need to add some Action Groups to your Activity Designer. This allows you to customise which Actions you have at your finger tips within the Designer.
>
> :video{src="/src/assets/book/add_action_groups.webm"}

Let's place down some Actions within our Activity to define our flow of logic. We'll need an action that generates a random number between 1 and 100 first. Fortunately, there is an Action that does _just that_ called `Random` which we can find in the `Numeric` Action Group!

:video{src="/src/assets/book/random_action.webm"}

Now that we have generated our random number, we need to place down an Action that will store this value so we can reference it later. For this, we need to write this number to a **Datastore**, this is sort of like a database and will let us store values persistently.

To add our random number to a datastore, we can use the `Set Datastore Variable` action which can be found in the `Variable` Action Group. In this Action, we'll select a Datastore to write the number to, give the number a name so that we can easily identify it and for the value we'll need to grab the result from the `Random` Action.

:video{src="/src/assets/book/set_datastore_variable.webm"}

You'll notice a few things from the clip above. Firstly, we created a new Datastore from the Action, this is a convnenience function which means you don't have to explicitly create the Datastore from the Project's homepage. Secondly, to select another Action's result as an input to this Action, we selected a green datachip: :datachip-action[equationResult]{type="Number"}. This method of selecting results via their Datachips is common across the whole Toca platform. We'll discuss this more in the :docs-link[Datachips and Variables]{id="book/programming_concepts/datachips_and_variables"} chapter.

We can now save the Activity and press Start Activity to test the Actions run as expected from start to finish.

:video{src="/src/assets/book/run_activity.webm"}

Great! We have built our first automation that generates and stores a random number!

Now, onto the next step, building an activity that will take a users guess as an input and tell us if it is correct or not.

Let's create a new activity that will run on a Stateless Bot.

:video{src="/src/assets/book/check_guess_activity.webm"}

Unlike the first Activity we built, this one is going to take an Input which will represent the user's guess. We also want to return some text from our Activity that will indicate to the user if their guess is correct.

Let's add the Input first.

:video{src="/src/assets/book/add_activity_input.webm"}

Now that we have defined our Input to the Activity, we need to construct the logic to handle if the user's guess is correct or not. Before we get stuck into the logic, the first thing we need to do is define a Variable which will represent the message we are reporting back to the user. Our logic will look similar to the following:

```
1. check if guess is greater than stored number
  1.1 If YES, set message to "Guess was too high, try again!"
2. check if guess is lower than the stored number
  2.1 if YES, set message to "Guess was too low, try again!"
3. check if guess is equal to the stored number
  3.1 if YES, set message to "Congratulations! You guessed the number correctly."
```

We can use the `If Then` Action to perform the checks and we can use the `Set Variable` Action to create and update the message throughout the Activity. Lastly, we'll return the message as an Output of the Activity.

:video{src="/src/assets/book/check_guess_activity"}

> In the video above, we used the "Duplicate Action" button on the actions to place our logic down a bit more quickly.
