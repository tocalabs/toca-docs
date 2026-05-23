# Custom Tab Buttons

In Toca, you can achieve a specific look and feel for your app's navigation by creating **Custom Tab Buttons**. This technique is for when you want to go beyond the default styling of the built-in **Tabs** component.

This guide shows you how to use a combination of other Toca components and <a id="ipl"></a>**In-Page Logic (IPL)** to achieve a custom design while keeping the functionality of the **Tabs** component. We will be discussing two possible approaches within this article.

---

## Why Use Custom Tab Buttons?

While Toca's native **Tabs** component is great for many use cases, you might need more control over the design. For example, you may want to:

- Create a unique visual style for your tab navigation.
- Implement advanced interactive behaviours.
- Have greater control over the layout and responsiveness of your tabs.

Default Tabs
![Default Tabs](/src/assets/cookbook/default_tabs.png)

Custom Tabs
![Custom Tabs](/src/assets/cookbook/custom_tabs.png)

---

## What You'll Need

To build your custom tab buttons, you will combine several key Toca components and app actions:

### Components:
-   **Flex**: Used for arranging your custom tab buttons horizontally or vertically.
-   **Button**: Styled to act as your individual tabs.
-   **Conditional Content**: Used to show or hide other components based on a condition, which in this guide will be used to indicate which tab the user has selected.
-   **Tabs**: Used to manage the content for each tab. The component's built-in buttons will be hidden, and your **Custom Tab Buttons** will be used for navigation instead.
-   **Run In Page Logic**: Used to execute [**IPL**](#ipl), often triggered by a **Component Event**.

### App Actions:
-   **Set Component Style**: Used to dynamically change the visual appearance of on-screen components.
-   **Set In Page Value**: Used to store and update the active tab within a **Page Variable**.
-   **Set Component Property**: Used to dynamically alter the properties of on-screen components.
-   **Trigger Event Listener**: Used to trigger other component listeners, such as those on the **Run In Page Logic** component.

---

## Building Your Custom Tab Buttons

This section will walk you through the steps to create your own custom tab button system.

### Step 1: Set Up the Tabs Component

Begin by adding the **Tabs** component to your page. This component will manage the actual content switching for your custom tabs.

1.  Drag and drop a **Tabs** component onto your page where you want the tabbed content to appear.
2.  Add the tabs that you wish to have on your page within the **Tabs** component's properties.
3.  In the component's properties, locate and **disable** the `Tabs Visible` option. This will hide the default tab buttons.
    > *Note: You must be using version `1.0.1` or newer of the **Tabs** component to see the `Tabs Visible` option.*
4.  Rename the `Update Tab Listener` field to a more user-friendly and descriptive name (e.g., `homePageTabs_updateTab`). This will make it easier to reference later.

![Configuring the Tabs component](/src/assets/cookbook/tab_component_configuration.png)

### Step 2: Create Your Custom Tab Buttons Layout

Now, you will build the visual navigation bar. All components for your custom tabs should be placed within a "Container" component.

1.  Add a **Flex** component to your page, typically above your **Tabs** component. While any container component can work, **Flex** is the most versatile for this purpose.
2.  Inside this **Flex** component, add the **Button** components that will represent your tabs.

![Flex container with custom buttons](/src/assets/cookbook/flex_container_with_buttons.png)

### Step 3: Choose Your Implementation Approach

You can create your custom tab buttons using one of two approaches.

#### Approach 1: Using Conditional Content and <a id="ipv"></a>In-Page Values (IPVs)

This approach uses **Conditional Content** components to render the selected state of your buttons and [**IPVs**](#ipv) to control which tab is active.

1.  **Create an [**IPV**](#ipv)**: Create a new [**IPV**](#ipv) to store the currently selected tab (e.g., `selected_tab`).
2.  **Configure the Click Event**: For each **Button** component, following the `Click` **Component Event**, add the following **App Actions**:
    *   **Set the [**IPV**](#ipv)**: Use the **Set In Page Value** **App Action** to update your `selected_tab` [**IPV**](#ipv) to a unique value for that button (e.g., "Tab 1", "Tab 2").
    *   **Update the Tabs Component**: Add a **Set Component Property** **App Action**. Configure it to point to your main **Tabs** component by referencing the listener you configured in Step 1 (e.g., `homePageTabs_updateTab`).
3.  **Manage Selected State**: Place your styled "selected" and "unselected" buttons inside 2 separate **Conditional Content** components. Use the `selected_tab` [**IPV**](#ipv) to control which version is visible. For example, the condition `{{selected_tab}} == 'Tab 1'` will render the "selected" version of Tab 1 when the [**IPV**](#ipv) matches.

![Approach 1 in canvas](/src/assets/cookbook/approach_1_in_canvas.png)

![Approach 1 IPL](/src/assets/cookbook/approach_1_in_ipl.png)

#### Approach 2: Using Run In Page Logic and Set Component Style

This approach is more scalable and uses a single, centralised **Run In Page Logic** component to manage tab state. A **Button** click passes data (like a tab index) to the component's `Listener Trigger` event, which then executes a series of actions.

1.  **Create a Reusable Logic Flow**: Create a **Run In Page Logic** component on your page. In its properties, rename the `Event Listener Name` field to something descriptive (e.g., `selectTab_runIPL`). The logic you define inside this component will be kicked off by its `Listener Trigger` **Component Event**. It should be configured to accept an input parameter (e.g., `tabIndex`), which will be the 0-based index of the tab to display.
2.  **Define Actions for the `Listener Trigger` Event**: Inside the **Run In Page Logic** component, for the `Listener Trigger` event, you can use the `tabIndex` that was passed in from the button click. Add the following sequence of **App Actions**:
    *   **Reset All Button Styling**: Add a **Set Component Style** **App Action** for *each* of your custom tab buttons. Set its `Component Name` to the target **Button**, `Property` to the style property you want to reset (e.g., `Background Colour`), `Action` to `Set Property`, and `New Value` to the "inactive" style value (e.g., `#e0e0e0`).    
    *   **Highlight the Active Button**: Add a final **Set Component Style** **App Action**. Use the `Component Name` to target the specific button (e.g., you can use conditional logic within the `Component Name` field to select the button corresponding to the `tabIndex`), `Property` to the style property you want to change (e.g., `Background Colour`), `Action` to `Set Property`, and `New Value` to the "active" style value (e.g., `#007bff`).
    *   **Update the Tabs Component**: Use a **Set Component Property** **App Action** to update the main **Tabs** component. Set its `Selected Tab` property to the `tabIndex` value that was passed in.
3.  **Trigger the Logic Flow from Buttons**: For each of your custom **Button** components, following the `Click` **Component Event**, add a single **Trigger Event Listener** **App Action**.
    *   Point this **App Action** to the listener for your **Run In Page Logic** component (e.g., `selectTab_runIPL`).
    *   In the `data` field for the listener, pass in the 0-based index for that specific tab (e.g., `0`, `1`, `2`). This is the `tabIndex` that the `Listener Trigger` event will receive.

![Approach 2 in canvas](/src/assets/cookbook/approach_2_in_canvas.png)

![alt text](/src/assets/cookbook/approach_2_ipl_setup.png)

![alt text](/src/assets/cookbook/approach_2_ipl_more_setup.png)

![alt text](/src/assets/cookbook/approach_2_in_ipl.png)

---

## Summary

With **Custom Tab Buttons**, you can:
-   Achieve complete design freedom for your tab navigation using **Flex** and **Button** components.
-   Leverage the **Tabs** component for content management while using custom buttons for interaction.
-   Dynamically switch content views using **Component Events** and **App Actions** like **Set In Page Value** and **Set Component Property**.
-   Create an enhanced user experience with custom visual feedback using **Set Component Style** or **Conditional Content**.
