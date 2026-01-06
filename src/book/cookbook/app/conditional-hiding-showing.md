## Conditional Hiding and Showing Components on a Page

There are several ways to hide or display components in the Toca application:

### 1st - "Visible on" Toggle

The simplest and most straightforward way is to use the **"Visible on"** toggle located in the component’s **Properties** panel.

By default, this toggle is turned ON, but you can switch it OFF if you want to hide the component on a specific viewport: Desktop, Laptop, Tablet, Mobile, or Widescreen. Simply navigate to the desired viewport and turn the toggle OFF for the component you want to hide on a page.

This allows for tailored visibility depending on your design needs.

![alt text](/src/assets/cookbook/conditional-hiding-showing/Gif1-1.gif)

---

### 2nd - Transition component

  
The second option allows you to show or hide a component on the screen based on specific conditions such as **when a button is clicked**.

To achieve this, you’ll need to set up **In-Page Logic** and use a **Transition component**. Let’s walk through an example where content visibility depends on a button click.

**1. Add and Configure an Icon Button**

Start by adding a **Flex layout** to the app designer. This will serve as the container for all the components involved in the interaction.

Next, add the button the user will interact with. In this example, we’ll use an **Icon Button**. Customize it through the **Icon properties** tab. There’s a wide variety of icons to choose from in the Icon field. For this walkthrough, we’ll use the **Lock** **icon** and set:
 - Color: Primary 
- Size: Large

![alt text](<Image 1-1.png>)

**2. Add a Transition component**

Add a **Transition** component within the same Flex layout. The component you want to show or hide will go inside this Transition.

Configure the Transition component with the desired effect (e.g. collapse, grow or fade). Since we want to toggle between showing and collapsing the content, set:

- Transition Effect: Collapse
- Height: 0

Also, ensure the ‘**Component displayed on page load**’ toggle is disabled.

![alt text](<Image 2-2.png>)

**3. Add the Target Components**

Place the components to be shown/hidden inside the Transition. In our example, this includes:
- A **Text** component
- A **Flex** layout
- An **Image** (placed inside the Flex layout)

![alt text](<Image 3-1.png>)

**4. Set Up In-Page Logic**

Now it’s time to set up the In-Page Logic. For this, click on the **Icon Button**, then go to **Events**. 

![alt text](<Image 4-1.png>)

In the opened event editor, create the following logic: **Click > Trigger Event listener**. Save the changes.

You might be wondering which listener to use. For that, navigate back to the app designer and open the Properties panel of the Transition component. 

Click on **Advanced**, and you will see the **Event Listener Toggle**. This is what you'll reference in the event logic. Be sure to copy the listener name.

![alt text](<Image 5-1.png>)

**5. Set up the Event Listener**

Return to the **Events** panel of the Icon Button and set up the **Trigger Event listener** by entering the copied listener into the **Listener Name** field. Save the changes.

![alt text](<Image 6-1.png>)

**6. Now, it’s time to check that it all works as expected in preview mode.**

![alt text](<Gif 2-1.gif>)

---

### 3rd - Conditional content component

The third way is by using the **Conditional content** component. The components placed inside it will be shown only if the condition set for the Conditional component is **True**. 

For example, you can type in the Condition field **112>=100**. As this is true, the components put inside the Conditional component will be shown. In contrast, if you type in **112<=100**, the components will not be shown as **112<=100** is **not True**. 

![alt text](<Gif 3-1.gif>)

To make conditions dynamic, you can also insert **dataships**, which the app automatically converts into their real values. 

Let’s explore how this works on the **People Details** page of the **Onboarding app**, by looking at specific parts of the configuration:

![alt text](<Image 7-1.png>)

If we look at the background of how these parts of the app are configured, we could see that the Conditional component was used:

![alt text](<Image 8-1.png>)

The **Conditional content component** was used in the following scenarios:

**1. Initial state (no people added):**
A notification is shown: *"You must add at least one person in order to continue to the next stage"*
**Condition**: people_added == 0

**2. At least one person added:**
The *Save & Continue* button becomes visible.
**Condition**: people_added > 0

![alt text](<Image 9-1.png>)

**3. Less than four people added:**
The *Add Person* button is displayed along with the instruction:
"*Please provide the information requested for up to 4 individuals to be added to your account.*"
**Condition**: people_added < 4

**4. Exactly four people added:**
 The *Add Person* button is no longer shown.

![alt text](<Image 10-1.png>)

In all these examples, the **people_added** datachip was used. This variable is automatically updated in the background to reflect how many people have been added, and based on that value, the app dynamically shows or hides relevant buttons and messages. It all is implemented with the help of the Conditional content component.

**Note**: If you're comparing strings, remember to wrap datachips in **quotes**.
 