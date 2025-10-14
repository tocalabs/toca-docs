# Custom Button

A **Custom Button** offers **full flexibility**.  
It doesn’t have predefined behavior — instead, you define exactly what it does using **actions**, **workflows**, or **page navigation rules**.

This makes it ideal for more **bespoke interactions**, such as:

- Running automations or API calls  
- Navigating to another page  
- Triggering conditional logic or showing popups  
- Performing actions outside of form submission

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
* choose a date and time,   
* staff member
![](/src/assets/cookbook/buttons/image3.png)



Create the backend automations to connect your form. For simplicity, we will use the automation wizard (🪄) placed on the top left:  
![](/src/assets/cookbook/buttons/image4.png)

Select **Create a Row** and ensure a listener is created as well:  
![](/src/assets/cookbook/buttons/image5.png)


In this example, we will call the listener `book_appointment`. This will link the button in the frontend to the backend “add row” automation.  

Create a list of options for users in the form:
![](/src/assets/cookbook/buttons/image6.png)


And a datastore variable list of staff:  
![](/src/assets/cookbook/buttons/image7.png)


### Create the App UI to Submit Using a Submit Button
![](/src/assets/cookbook/buttons/image8.png)


Example steps:  
- Add a repeating layout and a form component:
![](/src/assets/cookbook/buttons/image9.gif)  


- Add your listener to the app and update your form fields to use that listener:  
![](/src/assets/cookbook/buttons/image10.gif)

- Add form compoenent, fieldS and Map form fields the matching column in the table:  
![](/src/assets/cookbook/buttons/image11.gif)
![](/src/assets/cookbook/buttons/image12.gif)

- Add a submit button and test in preview:  
![](/src/assets/cookbook/buttons/image13.gif)

On submit, the form will indicate whether the booking was successful.

### Create the App UI to Submit Using a Custom Button

Let’s change the form functionality to check the availability of staff members.