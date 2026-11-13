# General Concepts

Welcome to the "General Concepts" chapter. This is your foundational guide to understanding the Toca platform and how its core components work together to build powerful applications. Whether you're a seasoned developer or completely new to the world of low-code, this chapter will provide you with a mental model for thinking about Toca and its unique approach to application development.

At its heart, Toca is about three interconnected pillars: **Apps**, **Automation**, and **Datastores**.

* **Apps** are your user interfaces—the front-end of your application. This is what your users interact with. They contain the buttons, forms, tables, and visual elements that define the user experience.
* **Automation** are the logic and processes that power your applications—the back-end. They perform the actions triggered by your users or by a schedule, such as sending emails, calculating values, or integrating with other systems.
* **Datastores** are where your information lives. These are the databases that hold your application's data, providing a structured way to manage and retrieve the information your apps and automation need.

These 3 pillars are all wrapped in a container called a **Workspace**. A Workspace should represent a particular project or collection of applications that are related.

In Toca, these three pillars are not isolated; they are deeply connected. An App might trigger an Automation to process data from a Data Store. That Automation might then update a different Data Store and send a notification back to the user's App. This seamless integration is what makes Toca so effective for building end-to-end solutions.

To help you get started, we'll first translate these Toca concepts into familiar terms. We will explore how Toca's Apps, Automation, and Datastores relate to the conventional ideas of **front-end**, **back-end**, and **database**. This will provide a common ground for understanding the platform's architecture.

Next, we will introduce the essential building blocks of all logic and processes: **control flow**, **data types**, and **variables & datachips**.

* **Control flow** dictates the order and conditions under which your logic is executed. This is how you introduce decision-making and logic into your applications.
* **Data types** are the categories of information you work with, such as text, numbers, dates, or boolean (true/false) values. Understanding these types is crucial for handling and manipulating data correctly.
* Finally, we'll cover **variables and datachips**. Variables are temporary storage containers that hold data during an automation's execution, while datachips refer to the way you use results and data from elsewhere. Mastering these concepts is key to passing information between different parts of your application and creating dynamic, data-driven experiences.

By the end of this chapter, you will have a clear understanding of Toca's fundamental architecture and the tools you need to start building your own robust and interconnected applications.
