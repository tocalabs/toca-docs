# Execute Javascript in In Page Logic
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

Next, create a new app and add a page called Dashboard. Configure this page with a Repeating Layout component bound to the orders table you just created. The Repeating Layout automatically renders one row per record from the table, making it easy to display tabular data.
![SLUG](/src/assets/cookbook/execute-js-ipl/image1.gif)

>Tip: Repeating Layouts automatically stay in sync with the table, so any new records added to the datastore will appear without additional configuration.

We will also add several Flex Layouts containing Card components. These cards will be used to display key performance indicators (KPIs) calculated from the orders data.
![SLUG](/src/assets/cookbook/execute-js-ipl/image2.png)

To improve the overall appearance of the dashboard, adjust component settings such as margins and borders.

### Configure In Page Logic Using the JavaScript Action
Go to the page events and drag in the:
1. `Page Mounted`: Runs the logic on page load
2. `Get Table Data With Query`: Enables use of the table data configured in the datastore 
3. `Execute Javascript`: Runs Javascript code
Connect the 3 actions in the order mentioned.


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
- The same logic can be reused across multiple KPI widgets 

> 💡 Tip: If KPI calculations become data-heavy or rely on large datasets, consider moving the logic to a backend automation and using JavaScript only for presentation and formatting.

```javascript
// Retrieve values from in-page variables
const totalItemsBought = Number(context['quantity'] || 0);
const totalOrders = Number(context['total_orders'] || 0);
const mostPopularProduct = Number(context['previous_revenue'] || 0);

// Calculate KPIs
let averageOrderQuantity = 0;
if (totalOrders > 0) {
  averageOrderValue = totalRevenue / totalOrders;
}

let revenueGrowthPercentage = 0;
if (previousRevenue > 0) {
  revenueGrowthPercentage =
    ((totalRevenue - previousRevenue) / previousRevenue) * 100;
}

// Format results
averageOrderValue = averageOrderValue.toFixed(2);
revenueGrowthPercentage = revenueGrowthPercentage.toFixed(2);

// Store results back into in-page variables

const table = Context.get("table")

let rows = table.values.map(e => e.recordValue)

total = rows.reduce((acc, e) => acc + parseInt(e.number), 0)

console.log(total)



```
