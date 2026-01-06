# Forms
# Intro to Toca.io Forms

## What is a Form in Toca.io?

A **form** in Toca.io is a screen or component used to collect user input and store it in a table. Forms are commonly used to capture business data and trigger workflows.

A form typically combines:

* **UI inputs** (text, number, date, dropdowns)
* **Data storage** (tables)
* **Logic** (actions, scripts, workflows)

---

## Core Components of a Toca Form

### 1. Form Fields (Inputs)

Common input types include:

* Text
* Number
* Date
* Dropdown / Select
* Checkbox
* Hidden fields (IDs, metadata)

Each input is usually mapped to a column in a table.

---

### 2. Data Table

Forms save data into tables. Example table:

**orders_table**

* order_id
* product_name
* quantity
* price
* created_at

Each form submission creates a new row in the table.

---

### 3. Submit Action

A submit button typically performs one or more actions:

* Insert a row into a table
* Validate input data
* Trigger workflows or scripts
* Navigate to another screen
* Send notifications or emails

---

## Creating a Simple Form (Step-by-Step)

### Step 1: Create a Table

Create a table with the required fields, for example:

* `product_name` (Text)
* `quantity` (Number)

---

### Step 2: Create a Screen

Add a new screen and include:

* Text input for product name
* Number input for quantity
* Submit button

---

### Step 3: Bind Inputs to Table Columns

For each input field:

* Set the value binding to the corresponding table column

Example:

* Product Name → `product_name`
* Quantity → `quantity`

---

### Step 4: Configure the Submit Button

On submit:

* Action: Insert Row
* Target table: `orders_table`
* Map input fields to table columns

---

## Accessing Form Data in Scripts

Submitted form data can be accessed in scripts using the Context object:

```js
const table = Context.get('orders_table');
```

Each row is accessible as:

```js
table.values[i].recordValue.quantity
```

---

## Example: Basic KPI Calculation

Calculate total orders and total quantity:

```js
const table = Context.get('orders_table');
const totalOrders = table.rowCount;

let totalQuantity = 0;
for (let i = 0; i < totalOrders; i++) {
  totalQuantity += Number(table.values[i].recordValue.quantity || 0);
}

console.log("Total Orders:", totalOrders);
console.log("Total Quantity:", totalQuantity);
```

---

## Best Practices

* Use correct data types (Number for quantities)
* Set default values to avoid `NaN`
* Validate required fields before submission
* Keep one form per table when possible
* Use scripts for calculations and KPIs

---

## Example: Building an Orders Dashboard

In this example, we will create an **orders table** in a datastore and use it to power a simple dashboard app.

### Step 1: Create the Orders Table

Create a new table in your datastore to store order data. This table will be used throughout the app.

![Orders table](/src/assets/cookbook/execute-js-ipl/image0.png)

Typical columns might include:

* `order_id`
* `product_name`
* `quantity`
* `price`
* `created_at`

---

### Step 2: Create a New App and Dashboard Page

Create a new app and add a page called **Dashboard**.

On this page, add a **Repeating Layout** component and bind it to the orders table you just created.

The Repeating Layout automatically renders **one row per record** from the table.

![Repeating layout bound to table](/src/assets/cookbook/execute-js-ipl/image1.gif)

---

### Step 3: Display KPI Cards

Next, add several **Flex Layouts** to the page. Inside each flex layout, place a **Card** component.

These cards will be used to display KPI values such as:

* Total Orders
* Total Quantity
* Average Order Quantity
* Other calculated metrics

![KPI cards layout](/src/assets/cookbook/execute-js-ipl/image2.png)

---

### Styling Notes

To improve the visual appearance of the dashboard, adjust component settings such as:

* Margins
* Padding
* Alignment
* Card spacing

These small layout tweaks can significantly improve readability and overall UX.

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