# Automation


An Automation Project is a place to create, store and manage your automated processes. They contain:

* :docs-link[Activities]{id="projects/automation/activities/activity"} - Individual automation tasks such as "Open a browser and log in to web app" or "Process data and add it to a table". These are your basic building blocks of automation.
* :docs-link[Workflows]{id="projects/automation/workflows/workflows"} - Orchestrate your activities by combining them together in a sequence. This is where you put your building blocks together to form something more consequential.
* :docs-link[Datastores]{id="projects/automation/datastores/datastores"} - Read and write to a persistent data layer from your activities
* :docs-link[Schedules]{id="projects/automation/schedules"} - Run your workflows on a routine basis

![Automation Hierachy](/src/assets/automation_project.png)

Automation is a very broad term but in Toca, automation refers to the ability to perform parts of, or all of, a business process with no human involvement. Your Toca platform will come with 1 or more virtualized workers known as Bots and these Bots can autonomously perform tasks up to 24 hours a day.

To find out more about Bots read the :docs-link[docs]{id="bots/bots"}

One of the most important things to do before embarking on your automation project is to choose a business process that is well-suited for automation. Processes which are good targets for automation exhibit the following characteristics:

*   Repeatable
*   Clearly defined rules
*   Can be broken down into smaller steps

You might build an automation project which serves as the backend for an App you are building, or your automation project might serve as a collection of desktop automation tasks for automating a business process, or it might contain both!
