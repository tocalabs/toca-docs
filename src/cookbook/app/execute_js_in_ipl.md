# Execute Javascript in In Page Logic (IPL)
In page logic allows you to execute a multitude of action on page clicks and componenet loads,
particularly important is the ExecuteJS in page logic that allows  custom JavaScript within your app when the inbuilt functionality doesnt quite do what you need it to.

Executing JavaScript is useful when you need:
- Custom calculations or data manipulation
- Conditional UI behaviour
- Interaction with browser APIs
- Formatting or transforming data before display
- Logic that is not currently supported through no-code configuration

### How it works

JavaScript can be executed using:
- Page Logic (e.g. button click events)
- Custom actions tied to components
- Event-driven logic (such as onClick, onLoad, or onChange events)

The script runs in the user’s browser, meaning it has access to:
- Page variables
- Session or in-page values
- Component state

### Example use cases

- Validate complex input before submitting a form  
- Dynamically enable or disable components  
- Generate or format values (e.g. dates, strings, IDs)  
- Show or hide components based on conditions  

#### Important considerations

- JavaScript execution is client-side only
- Long-running or heavy logic should be handled in backend automations instead
- Keep scripts small and maintainable

#### Best practices

- Use JavaScript only when no combinationation of native TOCA configuration exists that will achive what you desire 
- Comment your code for readability  
- Prefer TOCA variables and events over hardcoded values  


> Tip: If you find yourself writing large or complex scripts, it may be a sign that the logic belongs in a backend automation rather than the UI.

## Scenario: Using JavaScript to Calculate KPI's

Imagine you are building a dashboard that displays several Key Performance Indicators (KPIs), such as:
- Total Items Bought
- Total Orders
- Average Order Quantity

While TOCA provides basic in-page Logic Actions for addition and subtraction, this scenario requires more complex calculations, making it a good use case for executing JavaScript.

### Configure Table Data and a Dashboard

In this example, we will create an orders table in a datastore to serve as the data source for our app.
![SLUG](/src/assets/cookbook/execute-js-ipl/image0.png)

Next, create a new app and add a page called **Dashboard**.  
Add the datastore you previously created to the app’s **Resources**.

#### Display the Orders Data

Configure a Repeating Layout component to use the `orders` table you just created.

While this step is not required to calculate the KPIs, it is useful for displaying the underlying data that the KPIs are based on.

The Repeating Layout automatically renders one row per record, making it easy to present tabular data.

![alt text](/src/assets/cookbook/execute_js_in_ipl/image1_0.gif)

> **Tip:**  
> Repeating Layouts automatically stay in sync with the table, so any new records added to the datastore will appear without additional configuration.  
>
> You can disable this behaviour by unticking the Subscribe to changes checkbox.

![SLUG](/src/assets/cookbook/execute_js_in_ipl/image1_1.png)

#### Add KPI Cards

Next, add several Flex Layouts containing Card components.  
These cards will be used to display KPIs calculated from the orders data.

![SLUG](/src/assets/cookbook/execute_js_in_ipl/image2.png)

#### Styling the Dashboard

To improve the overall appearance of the dashboard, adjust component settings such as:
- Margins and padding  
- Borders and corner radius

This will help create a more professional-looking dashboard.

### Configure In Page Logic Using the JavaScript Action
Go to the page events and drag in the:
1. **Page Mounted**: Runs the logic on page load
2. **Get Table Data With Query**: Enables use of the table data configured in the datastore 
3. **Execute Javascript**: Runs Javascript code

Connect the 3 actions in the order mentioned.

Configure the `Get Table Data With Query` to get the orders table in your datastore.
![SLUG](/src/assets/cookbook/execute_js_in_ipl/image3_0.gif)

Configure the `Execute Javascript` drag the autput of `Get Table Data With Query` into the inputs and name the variable "orders_table". Here is an example code you can use to calculate the KPI's.

![SLUG](/src/assets/cookbook/execute_js_in_ipl/image3_1.gif)

```javascript
const table = Context.get('orders_table');

const totalOrders = table.rowCount;
let totalQuantity = 0;

// Track product popularity
let productCounts = {};

for (let i = 0; i < totalOrders; i++) {
  const row = table.values[i].recordValue;

  const orderQuantity = Number(row.quantity || 0);
  const productId = row.product_id;

  totalQuantity += orderQuantity;

  // Count quantity per product
  if (productId) {
    productCounts[productId] =
      (productCounts[productId] || 0) + orderQuantity;
  }
}

// Average Order Quantity
const averageOrderQuantity =
  totalOrders === 0 ? 0 : totalQuantity / totalOrders;

// Most & Least Popular Products
let mostPopularProduct = null;
let leastPopularProduct = null;
let maxQty = -Infinity;
let minQty = Infinity;

for (const product in productCounts) {
  const qty = productCounts[product];

  if (qty > maxQty) {
    maxQty = qty;
    mostPopularProduct = product;
  }

  if (qty < minQty) {
    minQty = qty;
    leastPopularProduct = product;
  }
}

// Set KPI's as in page values
set_in_page_value("Temporary","totalOrders", totalOrders, "Number");
set_in_page_value("Temporary","totalQuantity", totalQuantity, "Number");
set_in_page_value("Temporary","averageOrderQuantity", averageOrderQuantity, "Number");
set_in_page_value("Temporary","mostPopularProduct", mostPopularProduct, "Number");
set_in_page_value("Temporary","leastPopularProduct", leastPopularProduct, "Number");
```

When using the Execute JavaScript action, you can call TOCA-specific helper functions directly from your script.

**Rule of thumb**
>If there is a native TOCA action, there is usually an equivalent JavaScript function available.

For exaple as seen above the Set In-Page Value action maps to the function:
![SLUG](/src/assets/cookbook/execute_js_in_ipl/image4.png)

##### How JavaScript is used
When the dashboard loads, JavaScript is executed to:

1. Retrieve multiple numeric values from in-page or session variables  
2. Perform calculations such as:
   - Averages
   - Percentages
   - Conditional calculations (e.g. handling divide-by-zero scenarios)
3. Format the results (for example, rounding to two decimal places or adding percentage symbols)
4. Store the calculated KPI values back into in-page variables for display in the UI

#### Why JavaScript is needed

- Calculations go beyond simple arithmetic  
- Logic needs to account for edge cases (e.g. missing or zero values)  
- Formatting is required before displaying results to users

> If KPI calculations become data-heavy or rely on large datasets, consider moving the logic to a backend automation and using JavaScript only for presentation and formatting.


