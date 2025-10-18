# Custom Button

A **Custom Button** provides complete **flexibility and control**.
It has no predefined behavior — you decide exactly what it should do through **actions**, **workflows**, or **navigation rules**.

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

✅ **Best for:** Actions that go beyond saving data — such as *“Book Appointment”*, *“Generate Report”*, *“Send Email”*, or *“Open Modal”*

---

## Form Button Scenarios

Imagine you’re building a scheduling app where users can book services with available staff. On the **Create Appointment** page, users should be able to select a service, choose a date and time, pick a preferred staff member, and confirm their booking — all in one smooth flow.

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
At this stage, you’ll replace the standard submit button with a custom button and configure it to prevent users from booking a time when a staff member is unavailable. You can also add a small message to inform the user about availability.

Unlike a submit button, a custom button in Toca provides much greater visual and functional control, allowing you to tailor both its appearance and behavior to fit your app’s workflow.

As previously mentioned custom button allows you to:
- Add other components inside it (like icons, loaders, or status messages).
- Control exactly what happens on click — rather than immediately submitting the form.
- Connect it to specific logic flows or automation (e.g., “Check Availability” before “Book Appointment”).
- Customize its appearance — colors, animations, and layout — to better fit your app’s design.

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

Now that your form is configured we need to update the button to use the values set by the form and call the listener, you can do this by opening the events section on the button.
![alt text](/src/assets/cookbook/buttons/image15.png)

Add a click event and an execute listener event 
![alt text](/src/assets/cookbook/buttons/image16.png)