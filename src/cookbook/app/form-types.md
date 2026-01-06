# Forms


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