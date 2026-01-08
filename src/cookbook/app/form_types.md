# Forms
A **form** is a component used to collect user input and store it in a table or send to an automation for processing.

A form typically combines:
* **UI inputs** (text, number, date, dropdowns)
* **Data storage** (tables)
* **Logic** (actions, scripts, workflows)

There is a variety of input fields that can be used in forms:
* **Text Field:** alphanumeric data, such as names, emails, or short descriptions
* **Select Field:** A dropdown menu allowing users to choose one option from a pre-defined list.
* **Check Box:** A toggle used for binary choices (Yes/No) or for selecting multiple options from a list.
* **Radio Group:** A set of mutually exclusive options where a user can select only one item at a time.
* **File Uploader:** A drag-and-drop or browse area for attaching documents, images, or other files.
* **Auto Complete:** An enhanced text input that suggests matching options as the user types.
* **Date and Time picker:** A specialized interface (often with a calendar/clock) to ensure standardized date and time entries.

<details>
  <summary>Expand for more form components</summary>

* **Range:** A slider control used to select a value or a range of values from a numerical scale.
* **Form Image:** Allows you to input base64 encoded images into your app.
* **Graphical Field:** Allows you to add a graphical input field to your app's forms. This component is especially useful for capturing signatures or other freehand inputs from users.
* **Postcode Field:** A text input optimized for postal codes. This Field can be configured to validate the entered data, display error messages, and integrate with external postcode lookup services.
* **Transfer List**
* **File Downloader:** A specialized button or link used to retrieve documents or exports saved withing a datachip.
* **Interactive Data Table:** A complex component for displaying, filtering, and editing relational data directly within a form.
</details>



Interactive Data Table: A complex component for displaying, filtering, and editing relational data directly within a form.

### 📝 Background Configuration
Let's first create the automation project for confirming and submitting an appointment booking form.  

Create a workspace:  
![](/src/assets/cookbook/buttons/image0.png)

Create an automation project → datastore → table.
![](/src/assets/cookbook/buttons/image1.gif)

Add the columns desired to the table, for example: 
* service 
* appointment date
* staff member

![](/src/assets/cookbook/buttons/image3.png)

Create the backend automations to connect your form. For simplicity, we will use the automation wizard (🪄) placed on the top left:  
![](/src/assets/cookbook/buttons/image4.png)

Select Create a Row and ensure a listener is created as well:  
![](/src/assets/cookbook/buttons/image5.png)

In this example, by default the listener is named "table_name_action" (i.e. `add_appointment_table_row`) but we will rename it to `book_appointment`. This will be used to link the button in the frontend to the backend “add appointment table row” automation.  

Create a list of options for users in the form:
![](/src/assets/cookbook/buttons/image6.png)


And a datastore variable list of staff:  
![](/src/assets/cookbook/buttons/image7.png)

### Create the App UI to Submit Using a Submit Button
![](/src/assets/cookbook/buttons/image8.png)


Example steps:  
- Add a flex layout and a form component:
![](/src/assets/cookbook/buttons/image9.gif)  


- Add your listener to the app using the app settings:  
![](/src/assets/cookbook/buttons/image10-1.gif)
![](/src/assets/cookbook/buttons/image10-2.gif)

- Update your form to use that listener:
![](/src/assets/cookbook/buttons/image10-3.gif)

- Add form fields matching the type of data you are passing through:  
![Example Datetie form field](/src/assets/cookbook/buttons/image11.gif)

- Add a submit button and test in preview:  
![](/src/assets/cookbook/buttons/image12.png)

On submit, the form will indicate whether the booking was successful.