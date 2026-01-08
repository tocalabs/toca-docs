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
* **Transfer List**: Shows two sets of lists, with checkboxes over each option, you can then move options between these lists, either individually or in bulk.
* **File Downloader:** A specialized button or link used to retrieve documents or exports saved withing a datachip.
* **Interactive Data Table:** A complex component for displaying, filtering, and editing relational data directly within a form.
</details>

## Form Types
A form is rarely an isolated element; its architecture depends on how it interacts with the rest of the system. While the most common pattern is a Listener Form which sits idle until a "Submit Button" clicked, other use cases may benefit from a different form interaction type:
1. **Datastore:** directly synchronized with a Datastore table.
2. **In-Page Values:** Captures user input for immediate use within the current page logic, without necessarily sending that data to a listener or a backend table.
3. **Table:** Treats an entire data grid as an editable surface. It allows for inline editing, where rows can be toggled between "view" and "edit"
4. **User Login:** specialized authentication form focused on credential validation. It handles the secure exchange of user identity for session tokens or access permissions.
5. **User Registration:** A Creation Form that handles the complex logic of onboarding a new identity into the system.
6. **Change Password:** A specialized Security Update Form designed to protect sensitive account credentials.

In the following sections, we will discuss the peculiarities of each form type and the specific scenarios where they are best applied.

### The Event Listener Form
The Event Listener Form is the standard "Request/Response" model. It gathers data and waits for a specific trigger (the Submit button) to execute a backend automation.

Imagine you’re building a scheduling app where users can book services with available staff. On the Create Appointment page, users should be able to:

1. Select a service  
2. Choose a date and time  
3. Pick a preferred staff member  
4. Confirm their booking  

#### Background Configuration
First, we need to create the automation project and the database structure for an appointment booking system.

1. Create a workspace: ![](/src/assets/cookbook/form_types/image0.png)

2. Create an automation project → datastore → table.
![](/src/assets/cookbook/buttons/image1.gif)

3. Add the columns desired to the table, for example service, appointment date and staff member.
![](/src/assets/cookbook/buttons/image3.png)

4. Create the backend automations to connect your form.
For simplicity, we will use the automation wizard 🪄 placed on the top left: 
![](/src/assets/cookbook/buttons/image4.png)

5. Select Create Table Row and ensure a listener is created as well:
![](/src/assets/cookbook/form_types/image5.png)

In this example, by default the listener is named "table_name_action" (i.e. `add_appointment_table_row`) but we will rename it to `book_appointment`.

>Note: This will be used to link the button in the frontend to the backend “add appointment table row” automation. 

6. Create a list of options for users in the form:
![](/src/assets/cookbook/form_types/image6.png)


7. And a datastore variable list of staff:  
![](/src/assets/cookbook/form_types/image7.png)

### Create Listener form
1. Add a flex layout and a form component:
![](/src/assets/cookbook/form_types/image9.gif)  


2. Add your listener to the app using the app settings:  
![](/src/assets/cookbook/form_types/image10-1.gif)
![](/src/assets/cookbook/form_types/image10-2.gif)

3. Update your form to use that listener:
![](/src/assets/cookbook/form_types/image10-3.gif)

4. Add form fields matching the type of data you are passing through:  
![Example Date form field](/src/assets/cookbook/form_types/image11.gif)

5. Add a submit button and test in preview:  
![](/src/assets/cookbook/form_types/image12.png)

On submit, the form will indicate whether the booking was successful.

After some styling you could have something similar to this:
![](/src/assets/cookbook/form_types/image8.png)

You can check if the values have been sent correctly to the back end by looking into the "Reporting" section:
![](/src/assets/cookbook/form_types/image9.png)

