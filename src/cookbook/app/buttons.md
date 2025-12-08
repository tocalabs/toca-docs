# Custom Button

A **Custom Button** provides complete **flexibility and control**.
It has no predefined behavior, you decide exactly what it should do through **actions**, **workflows**, or **navigation rules**.

This makes it perfect for creating **tailored user interactions**, such as:

* Running automations or calling external APIs
* Navigating to a different page
* Triggering conditional logic or displaying popups
* Executing tasks independently from form submissions

Additionally, a custom button lets you **embed other components within it**, such as icons, loading indicators, or dynamic status messages, giving you both **functional and visual freedom** in your app design.

---

## Variants

Custom buttons include a **variant** property that enables a wider range of styling options:

- **Button (default)** – Configurable size, click, hover effects, and corner rounding  
- **Div** – Supports mouse click and hover events; behaves like a clickable container  
- **Paper** – Includes mouse click and hover events, as well as elevation

✅ **Best for:** Actions that go beyond saving data, such as *“Book Appointment”*, *“Generate Report”*, *“Send Email”*, or *“Open Modal”*

---

## Form Button Scenarios

Imagine you’re building a scheduling app where users can book services with available staff. On the **Create Appointment** page, users should be able to select a service, choose a date and time, pick a preferred staff member, and confirm their booking, all in one smooth flow.

### 📝 Background Configuration

Used to confirm and submit an appointment booking form.  
Create the backend automation:  

Create an automation project → datastore → table:
![](src/assets/cookbook/buttons/image1.png)

![](/src/assets/cookbook/buttons/image2.png)

Add the columns desired to the table, in this case 

* select a service,   
* choose appointment datetime,   
* staff member
![](/src/assets/cookbook/buttons/image3.png)

Create the backend automations to connect your form. For simplicity, we will use the automation wizard (🪄) placed on the top left:  
![](/src/assets/cookbook/buttons/image4.png)

Select **Create a Row** and ensure a listener is created as well:  
![](/src/assets/cookbook/buttons/image5.png)

In this example, by default the listener is named "table_name_action" (i.e. `add_appointment_table_row`) but we will rename it to `book_appointment`. This will be used to link the button in the frontend to the backend “add appointment table row” automation.  

Create a list of options for users in the form:
![](/src/assets/cookbook/buttons/image6.png)


And a datastore variable list of staff:  
![](/src/assets/cookbook/buttons/image7.png)


### Create the App UI to Submit Using a Submit Button
![](/src/assets/cookbook/buttons/image8.png)


Example steps:  
- Add a repeating layout and a form component:
![](/src/assets/cookbook/buttons/image9.gif)  


- Add your listener to the app using the app settings ⚙️ and update your form to use that listener:  
![](/src/assets/cookbook/buttons/image10.gif)

- Add form fields matching the type of data you are passing through:  
![Example Datetie form field](/src/assets/cookbook/buttons/image11.gif)

- Add a submit button and test in preview:  
![](/src/assets/cookbook/buttons/image12.png)

On submit, the form will indicate whether the booking was successful.

### Create the App UI to Submit Using a Custom Button
At this stage, you’ll replace the standard submit button with a custom button and configure to have a confirmation box before submitting the information.

Unlike a submit button, a custom button in Toca provides much greater visual and functional control, allowing you to tailor both its appearance and behavior to fit your app’s workflow.

As previously mentioned custom button allows you to:
- Add other components inside it (like icons, loaders, or status messages).
- Control exactly what happens on click, rather than immediately submitting the form.
- Connect it to specific logic flows or automation (e.g., “Check Availability” before “Book Appointment”).
- Customize its appearance, colors, animations, and layout, to better fit your app’s design.

Try to play around with some of the components and change the look of your button. 

**Tip**
When using Text components, it is often recommended to **encase them within a Flex layout**. This is because Flex components enable:
- **Horizontal or vertical alignment** of multiple elements  
- **Consistent spacing** between text and other components (like icons or badges) 
- **Better control** over positioning and grouping within the UI

Here's an example custom button configuration
![Custom button with Flex component and icon, the flex contains text](/src/assets/cookbook/buttons/image13.png)

Unlike a submit button, custom buttons are not directly linked to the form component. If you try to preview the button and click on it, nothing will happen by default.  

To resolve this, we need to change the form type from `Listener` to `In Page Value`.
![alt text](/src/assets/cookbook/buttons/image14.png)
What this does is, instead of submitting the values, the form saves them in a temporary, in-page variable. This variable can also be configured to session or temporary storage. For more details on how this works, please refer to the In Page Logic documentation.  

The form component also has a prefix setting, which is particularly useful to prevent variable name collisions when you have multiple in-page values. The configured prefix is added to your variable names automatically.

Map the created variables to the form fields: 
![alt text](image15-1.png)

Preview the form and select some values, exit the preview, we need to do this so the chips values are selectable when configiring your button event.  

Now that your form is configured we need to update the button to use the values set by the form and call the listener, you can do this by opening the events section on the button.
![alt text](/src/assets/cookbook/buttons/image15.png)

Add a `click event` and an `execute listener event` 
![alt text](/src/assets/cookbook/buttons/image16.png)

Insert the in page values created by the form component, if you can't select them in the drop list you can type them
![alt text](/src/assets/cookbook/buttons/image17.gif)
Don't forget to add the prefix configured in your form.

Test Your form in preview. 
You can check if the form has been triggered correctly in Reports.
![alt text](/src/assets/cookbook/buttons/image18.gif)

#### Add a Confirmation Box to Prompt the User

Now we’ll add a confirmation box to prompt the user before performing an action.

##### Steps

1. **Open the button event settings**  
   Go back to the button’s event configuration and add a "confirmation dialog".

2. **Add a custom message**  
   Create a custom confirmation message.  
   You can insert dynamic values from the page or form to make the message more personalized.
   In this example we have inserted on of the form's in page values.

3. **Customize button text**  
   The dialog buttons default to OK and Cancel, but you can change these labels to match your desired wording.
   Regardless of the wording, the logic will return true for a positive response (e.g., OK) and false for a negative response (e.g., Cancel).

4. **Add an exclusive node**  
   Add an exclusive node to control how the logic flows based on set criteria.  
   In this case, use the confirmation dialog result to determine whether the event listener should be triggered or not.

![alt text](/src/assets/cookbook/buttons/image19.png)
![alt text](/src/assets/cookbook/buttons/image20.gif)

Tip: you could also add a snackbar notification for informing users that their action has been cancelled or has succeded 
![alt text](/src/assets/cookbook/buttons/image21.png)
![alt text](/src/assets/cookbook/buttons/image22.gif)

## Open modal using an icon button 
Often, a button doesn’t need any text.  

Icon buttons allow you to:  
- Select from a series of pre-defined icons.  
- Apply the site’s theme to the icon automatically.  
- Avoid manually customizing icons or uploading images.  

This approach helps keep icon sizes and appearance uniform across the entire site, ensuring a consistent and professional look.

For this example we will configure an icon button that users can click to gain further information on the services provided.

**Create a new page that describes the services**  
   There are many dynamic ways to do this (e.i saving the services into a table) but for simplicy's sake we will just have a flex with text for each service.
![alt text](/src/assets/cookbook/buttons/image23.png)

**Add the icon button to your page**  
   this can be anywhere on your page
![alt text](/src/assets/cookbook/buttons/image24.png)

**Configure the icon button in page logic**  
The button will need to be configured to open the descriptions page on click.
![alt text](/src/assets/cookbook/buttons/image25.png)