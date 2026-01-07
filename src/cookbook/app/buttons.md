# Buttons

Buttons are one of the most common and essential components in any app interface. They allow users to interact with your app, perform actions, and navigate through content. There are a few main types of buttons:

- Basic buttons
- Submit buttons
- Custom buttons
- Icon buttons
- Floating Action buttons
- Link buttons

---

## Basic Buttons

Basic buttons are standard clickable elements that usually contain text labels. They are ideal for actions where you want the user to clearly understand what will happen when they click, such as:

- Submit a form (e.g., “Book Appointment”)  
- Navigate to another page (e.g., “View Details”)  
- Trigger an action (e.g., “Generate Report”)  

Key features of normal buttons:

- Display descriptive text for clarity  
- Can include emojis alongside text for added visual cues  
- Supports basic level of styling  
- Can trigger in-page logic flows, automations, or navigation events  
- Automatically adopt the app’s theme for colors and sizing  

---

## Styles

Buttons support multiple visual styles, allowing you to match the button’s appearance to its purpose and importance:

- Text: Minimal styling with no background. Ideal for low-emphasis actions. Commonly used for inline actions or secondary navigation  
- Outlined: Transparent background with a visible border. Suitable for secondary or alternative actions  
- Filled: Solid background using the primary theme colour. Best for primary actions such as Save, or Confirm  

---

## Submit Buttons

Submit Buttons have all the features and functionality you can find in a generic button, but are exclusively used for forms.  

This is because it has the extra functionality of submitting any form the button is placed in without having to configure it to do so.  

> ⚠ Warning  
> A submit button submits all forms it is contained within.  
> If forms are nested, all nested forms will be submitted.  

---

# Custom Buttons

A Custom Button provides complete flexibility and control over its design and content. Unlike normal or submit buttons, which are mostly predefined, a custom button allows you to decide exactly how it should look.  

## Variants

Custom buttons include a variant property that enables a wider range of styling options:

- Button (Default) – Configurable size, click, hover effects, and corner rounding  
- Div – Supports mouse click and hover events; behaves like a clickable container  
- Paper – Includes mouse click and hover events, as well as elevation  

Best for: Actions that go beyond saving data, such as *“Book Appointment”*, *“Generate Report”*, *“Send Email”*, or *“Open Modal”*  

A custom button lets you embed other components within it, such as icons, loading indicators, or dynamic status messages, giving you more functional and visual freedom in your app design.  

---

## Icon Buttons

Icon buttons contain only an icon instead of text. They are perfect for actions that are widely understood by their visual representation, such as:

- Opening a modal or popup  
- Navigating to a section of the app  
- Performing quick actions (e.g., edit, delete, or favourite)  

Key features of icon buttons:

- Use pre-defined icons  
- Automatically adopt the app’s theme for colors and sizing  
- Maintain a clean and minimal interface  
- Ideal for toolbar actions or secondary actions  

---

## Floating Action Buttons

Floating Action Buttons (FABs) are a type of button used to highlight a primary action on a page. They are designed to stand out and remain easily accessible, floating above other content rather than being embedded in the page.  

Common Use Cases:

- Adding a new item (e.g., Add Contact, Create Task)  
- Starting a new message or email  

---

## Button Scenarios

Imagine you’re building a scheduling app where users can book services with available staff. On the Create Appointment page, users should be able to:

1. Select a service  
2. Choose a date and time  
3. Pick a preferred staff member  
4. Confirm their booking  

All in one smooth flow.

### Background Configuration

Let's first create the automation project for confirming and submitting an appointment booking form.  

1. Create a workspace
   ![](/src/assets/cookbook/buttons/image0.png)  

2. Create an automation project → datastore → table:  

   ![](/src/assets/cookbook/buttons/image1.gif)  

3. Add the columns desired to the table, for example:  

   - service  
   - appointment date  
   - staff member  

   ![](/src/assets/cookbook/buttons/image3.png)  

4. Create the backend automations to connect your form using the automation wizard (🪄) placed on the top left:  

   ![](/src/assets/cookbook/buttons/image4.png)  

5. Select Create a Row and ensure a listener is created as well:  

   ![](/src/assets/cookbook/buttons/image5.png)  

   In this example, the listener is renamed to `book_appointment` to link the frontend button to the backend automation.  

6. Create a list of options for users in the form:  

   ![](/src/assets/cookbook/buttons/image6.png)  

7. Create a datastore variable list of staff:  

   ![](/src/assets/cookbook/buttons/image7.png)  

---

### Create the App UI to Submit Using a Submit Button

1. Add a flex layout and a form component:  

   ![](/src/assets/cookbook/buttons/image9.gif)  

2. Add your listener to the app using the app settings:  

   ![](/src/assets/cookbook/buttons/image10-1.gif)  
   ![](/src/assets/cookbook/buttons/image10-2.gif)  

3. Update your form to use that listener:  

   ![](/src/assets/cookbook/buttons/image10-3.gif)  

4. Add form fields matching the type of data you are passing through:  

   ![](/src/assets/cookbook/buttons/image11.gif)  

5. Add a submit button and test in preview:  

   ![](/src/assets/cookbook/buttons/image12.png)  

On submit, the form will indicate whether the booking was successful.  

---

### Basic Button

Basic Buttons are essentially a simple version of custom buttons. Unlike a submit button, Basic buttons are not directly linked to the form component. If you try to preview the button and click on it, nothing will happen by default.  

We demonstrate how to do this in the Custom Buttons section.

---

### Create the App UI to Submit Using a Custom Button

At this stage, replace the standard submit button with a custom button and configure a confirmation box before submitting the information.  

Custom buttons allow you to:

- Add other components inside it (like icons, loaders, or status messages)  
- Control exactly what happens on click, rather than immediately submitting the form  
- Connect it to specific logic flows or automation before submitting a form  
- Customize its appearance, colors, animations, and layout  

Try to play around with components and change the look of your button.

Tip: When using Text components, it is recommended to **encase them within a Flex layout**. Flex components enable:

- Horizontal or vertical alignment of multiple elements  
- Consistent spacing between text and other components  
- Better control over positioning and grouping within the UI  

Here's an example custom button configuration:  

![Custom button with Flex component and icon, the flex contains text](/src/assets/cookbook/buttons/image13.png)  

Unlike a submit button, custom buttons are not directly linked to the form component.  

---

### Configure Form to Use In-Page Values

Change the form type from `Listener` to `In Page Value`:  

![alt text](/src/assets/cookbook/buttons/image14.png)  

This saves values in a temporary in-page variable, which can be configured to session or temporary storage.  

The form component also has a prefix setting to prevent variable name collisions.  

Map the created variables to the form fields:  

![alt text](/src/assets/cookbook/buttons/image15-1.png)  

Preview the form and select some values, then exit preview so chip values are selectable when configuring your button event.  

Update the button to use the values set by the form and call the listener via the events section:

![alt text](/src/assets/cookbook/buttons/image15.png)  

Add a `click event` and an `execute listener event`:  

![alt text](/src/assets/cookbook/buttons/image16.png)  

Insert the in-page values created by the form component. Include the configured prefix if necessary:

![alt text](/src/assets/cookbook/buttons/image17.gif)  

Test the form in preview and check Reports to confirm submission:  

![alt text](/src/assets/cookbook/buttons/image18.png)  

---

### Add a Confirmation Box to Prompt the User

Steps:

1. Open the button event settings and add a "confirmation dialog"  
2. Create a custom message using dynamic values if needed![alt text](/src/assets/cookbook/buttons/image19.png)  
3. Customize dialog buttons text (OK/Cancel). You can change these labels to match your desired wording. Regardless of the wording, the logic will return true for a positive response (e.g., OK) and false for a negative response (e.g., Cancel) 
4. Add an exclusive node to control logic based on the confirmation result 
![alt text](/src/assets/cookbook/buttons/image20.gif)  

Tip: Add a snackbar notification to inform users if their action was cancelled or succeeded:  

![alt text](/src/assets/cookbook/buttons/image21.png)

Preview:

![alt text](/src/assets/cookbook/buttons/image22.gif)  

---

### Add App Functionality Using an Icon Button

Icon buttons allow you to:

- Select from pre-defined icons  
- Apply the site’s theme automatically  
- Keep icon sizes and appearance uniform  

Create a new page describing the services:  
![alt text](/src/assets/cookbook/buttons/image23.png)
There are many dynamic ways to do this (e.i saving the services into a table) but for simplicy's sake we will just have a flex with text for each service.  

Add the icon button to your page:  

![alt text](/src/assets/cookbook/buttons/image24.png)  

Configure the icon button in page logic to open the description page on click:  

![alt text](/src/assets/cookbook/buttons/image25.png)  

Test in preview:  

![alt text](/src/assets/cookbook/buttons/image26.gif)  

---

### Add App Functionality Using a Floating Action Button
In your app you may want for customers to easely contact support in the case of questions or issues with booking their appointment.

Use a floating button to make a contact form easily accessible:

1. Create a new page (contact form) and configure fields  
2. Get the app URL
![url](/src/assets/cookbook/buttons/image27.png)
3. Get the page SLUG:
![SLUG](/src/assets/cookbook/buttons/image28.gif)  
4. Configure the floating button to redirect to URL/SLUG on click:  

   ![SLUG](/src/assets/cookbook/buttons/image29.png)  

Preview page and click on the floating button
