# Toca as a Technology Stack

When you develop and build a software application, you need to think about what technologies you are going to use to put the application together. If you liken building an application to putting together a meal, you need to decide what ingredients you're going to use and if you need to use any tools like a food processor to make it. The ingredients and methods you use represent the stack you've used to create your dish!

## What is a tech stack?

A tech stack is typically defined as a combination of technologies such as databases, tools, libraries and frameworks that are used together to build and run a software application.

A tech stack for a web application often consists of the following parts:
1. A Programming Language - _What language are you going to use to define the logic in your application?_
2. A Framework - _Are there any frameworks you can use which might speed up development?_
3. Libraries - _Is there any logic you can reuse from elsewhere which reduces the amount of work you have to do?_
4. Front-end Technologies - _What technology are you going to use to develop your user interface?_
5. Back-end Technologies - _What technology are you going to use to develop your server-side logic?_
6. Databases - _How and where your data is going to be stored?_
7. Infrastructure - _Where your application is going to run from?_

When you're building a web application, you often have to worry about all of the items above and it's not uncommon for you to use totally different technologies to develop your user interface (the front-end of your application) and to develop your server-side logic (the back-end of your application). This leads to added complexity and often means you need multiple people who understand all of the different parts of your stack.

With Toca, the technology is consistent across all elements of the stack so the complexity and overhead is greatly reduced. This being said, it still offers a great deal of flexibility and configurability so whilst it is simpler to build an application on Toca, you can still put together large and complex apps.

## Full Stack Development Framework

Whilst there are many platforms out there which offer a low-code _Drag'N'Drop_ interface to put together software, there are very few which offer the breadth of features that Toca does. In Toca you can build software across the full range of the stack: front-end, back-end and data.

![The Toca Stack](/src/assets/book/toca_stack.png)

- Apps in Toca cover just about all you need to design your user interfaces and define the interactivity on each page.
- Automation covers all the server-side logic, including interactivity with the database layer and running flows triggered by users on your App.
- Datastores cover your database needs by allowing you to build tables and views.
- Lastly, Toca will also host and run the application that you build on it so no need to worry about sorting out infrastructure for your project when it's ready for release!


### Frontend Stack: Apps

Apps are put together with **pages** where each page represents a distinct page in your web app. On each page, you need to place down **components**, components represent UI widgets such as a chart or navbar. Each component can then trigger some logic from an event that happens to the component such as being clicked on, this logic is defined with **IPL actions** _(IPL stands for In Page Logic)_.

![Composition of an App Page](/src/assets/book/app_stack.png)

Apps can be locked down behind log in and registration pages or they can be publicly accessible. Apps can also display data from the data layer of the stack by linking a Datastore with an App. You can also allow users to run server-side logic by linking Apps with Workflows defined in the Automation layer.

### Backend Stack: Automation

In Automation, you define blocks of logic known as **activities**, which consist of one or more **actions**, where each action performs a specific automation task such as adding a row to a table or making an API call. Activities are then placed into overarching flows called **workflows**. These workflows can then be run manually, on a schedule, triggered by a user of your App or run via an API call.

![Composition of an Automation Project](/src/assets/book/automation_stack.png)

Automation can then link to Datastores which represent the data layer in the Toca stack. This allows you to read and write to tables and variables stored in Datastores from your automation.

### Data Stack: Datastores and CMS

There are two main ways of storing persistent data in Toca and which one you use will depend on your use case. If you are building an App that is very content heavy such as a blog site or a glossy coorporate website, then you may require a **content management system (CMS)** to manage the content and articles you want to display in your app. If your data is more transient and you need to store data that frequently needs to be updated then you are likely to need a **datastore**. Inside a **datastore** the most common way to store data is using **tables** and **views**. If you need to store smaller bits of data persistently then you can store singular **variables** as well as credentials such as OAuth **identities** and **passwords**.

![Composition of CMS and Datastores](/src/assets/book/datastore_cms_stack.png)

You can then link your App and Automation to your data layer, allowing you to drive chart components in your app from the data in a datastore table or add new rows to your datastore from your automation.
