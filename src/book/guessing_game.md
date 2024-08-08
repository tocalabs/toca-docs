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

To add our random number to a datastore, we can use the `Set Datastore Variable` action which can be found in the `Variable` Action Group.

:video{src="/src/assets/book/set_datastore_variable.webm"}
