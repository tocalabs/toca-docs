### **Custom Button**

A **Custom Button**, on the other hand, offers **full flexibility**.  
 It doesn’t have a predefined behavior — instead, you define exactly what it does using **actions**, **workflows**, or **page navigation** rules.

This makes it ideal for more **bespoke interactions**, for example:

* Running automations or API calls  
* Navigating to another page  
* Triggering conditional logic or showing popups  
* Performing actions outside of form submission

Furthermore custom buttons have a variant property which enable a wider range of styling options:

* Button ( default \-  Has configurable button size click and on hover event and corner rounding )   
* Div (Has configurable mouse click and on hover events, behaves like a clickable div )   
* Paper ( Has configurable mouse click and on hover event as well as elevation ) 

✅ **Best for:** actions that go beyond saving data — such as *“Book Appointment”*, *“Generate Report”*, *“Send Email”*, or *“Open Modal”*

## Form Button Scenarios: 

Imagine you’re building a scheduling app where users can easily book services with available staff. On the **Create Appointment** page, users should be able to select a service, choose a date and time, pick a preferred staff member, and confirm their booking — all in one smooth flow.

### **📝 Background Configuration**

Used to confirm and submit an appointment booking form.  
Create the back end automation:   
Create an automation project → datastore → table: 

![test](src/assets/cookbook/buttons/image1.png)

![](/src/assets/cookbook/buttons/image2.png)

![](/src/assets/cookbook/buttons/image3.png)

Add the columns desired to the table, in this case 

* select a service,   
* choose a date and time,   
* staff member

![](/src/assets/cookbook/buttons/image4.png)

Create the back end automations to connect your form to. For simplicity we will use the automation wizard: 

![](/src/assets/cookbook/buttons/image5.png)

Select create a row and ensure that a listener is created as well 

![](/src/assets/cookbook/buttons/image6.png)

In this example we will call the listener book\_appointment. We will use this to link the button in the front end to the back end “add row automation”. 

Create a list of the options you would like to make available for the user to select in yoru form: 

![](/src/assets/cookbook/buttons/image7.png)

And a datastore variable  list of staff:

![](/src/assets/cookbook/buttons/image8.png)

Create the App UI to submit using a SUBMIT BUTTON: 

![](/src/assets/cookbook/buttons/image9.png)

Here is an example steps: 

Add a repeating layout and a form component:

![](/src/assets/cookbook/buttons/image10.png)

*Add your listener to the app and update your form field component to use that listener:* 

*![](/src/assets/cookbook/buttons/image11.png)*

*Add your form fields ( try to use form components that match the column type you configured in the table ) :* 

*![( In this example the select list fields use the datastore lists for staff and services)][image12]*

*( In this example the select list fields use the datastore lists for staff and services)* 

*link the listener outputs*

*![][image13]*

*Add a submit button and test in preview*

*![][image14]*

*On submit your form will return whether your booking was successful or not\!*

Create the App UI to submit using a CUSTOM BUTTON: 

Let’s change up the functionality for the form to check the availability of staff members: 
