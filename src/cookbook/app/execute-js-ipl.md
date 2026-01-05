# Execute Javascript in In Page Logic
In page logic allows you to execute a multide of action on page clicks and componenet loads,
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

### Important considerations

- JavaScript execution is client-side only
- Long-running or heavy logic should be handled in backend automations instead
- Keep scripts small and maintainable

### Best practices

- Use JavaScript only when no combinationation of native TOCA configuration exists that will achive what you desire 
- Comment your code for readability  
- Avoid direct DOM manipulation unless absolutely necessary  
- Prefer TOCA variables and events over hardcoded values  


> Tip: If you find yourself writing large or complex scripts, it may be a sign that the logic belongs in a backend automation rather than the UI.

### Scenario: Using JavaScript to Validate and Prepare Data Before Submission

Imagine you are building a **dashboard** that displays several **Key Performance Indicators (KPIs)**, such as:
- Total revenue
- Average order value
- Percentage growth compared to the previous period

While TOCA provides basic in-page addition and subtraction through page logic, this scenario requires **more complex calculations**, making it a good use case for executing **JavaScript**.

#### Create a Dashboard in a toca app page
In this example we will create a orders table to use for our app:


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
const totalRevenue = Number(context[total_revenue] || 0);
const totalOrders = Number(context[total_orders] || 0);
const previousRevenue = Number(context[previous_revenue] || 0);

// Calculate KPIs
let averageOrderValue = 0;
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
setaverageOrderValue;
inPage.revenue_growth_percentage = revenueGrowthPercentage;

```
