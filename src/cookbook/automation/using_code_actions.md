# Using Code in Automation

This document provides practical examples of how to use Toca's code actions (`Python` or `C#`) in combination with other low-code actions to build powerful and flexible solutions. By bridging the gap between low-code and high-code, you can handle complex logic, data manipulation, and integrations that might be difficult to achieve with low-code blocks alone.

## Combining Low-Code and High-Code

The core idea is to use Toca's standard low-code actions for what they do best — connecting to services, handling user interactions, and orchestrating workflows—while delegating complex data processing, complex bulk calculations, or intricate logic to a snippet of Python or C# code.

**Common Workflow Pattern:**
1.  **Ingest Data:** Use a low-code actions like the `API Caller` for a HTTP Request, `Get Table Data` to retrieve your user data, and `For Each Row` to over a table.
2.  **Process with Code:** Pass the data into a `Python` or `C#` action to parse, transform, or analyse it.
3.  **Use the Result:** Take the output from the code action and feed it into subsequent low-code actions like `JSON Navigator`, `Update Table Row`, or `Data Processor` to perform your automated task.

---

## Example 1: Advanced Date & Time Operations with Python

This example demonstrates how to perform common date and time manipulations, such as calculating future dates based on an offset and converting between different timestamp formats. This is useful when dealing with license expiry dates, scheduling tasks, or preparing data for systems that require a specific time format (like UNIX).

### Goal
- Take an ISO 8601 formatted date string and a number of days as input.
- Calculate the future date by adding the specified number of days.
- Get the current date and time.
- Convert the original ISO date into a UNIX timestamp.
- Output the calculated future date, the current timestamp, and the UNIX timestamp.

### Actions Required
1.  **Datetime:** To provide the current datetime.
2.  **Set Variable:** To provide the day offset.
3.  **Python:** To perform all date and time calculations.
4.  **Set Variable:** To store and view the multiple outputs from the Python script.

### Step-by-Step Implementation

**Step 1: Define Inputs**
In a real workflow, this data might come from an API or a database. For this example, we'll use `Datetime` and `Set Variable` actions to define them.

- **Variable `number_of_days`:** `90`

**Step 2: Python Action**

In your Toca activity, add the **Python** action and click the "Edit" button to configure it.

-   **Python Inputs:** Above the code box, click the "Add Data Chip" button to add your inputs. Select the `number_of_days` datachip from your activity. For clarity, you can rename the input key for this input to `days_offset`. Next, add your datetime action result from the `Datetime` action. You can rename this input key to `iso_date`. These keys are what you will use to access the data inside your Python script.

>*Note:* We strongly recommend ticking the "Fresh namespace" option. This ensures that each time the action runs, it starts with a completely clean environment, preventing variables or imports from a previous run from accidentally affecting the current execution. This makes your code predictable, reliable, and easier to debug.

-   **Code:** Paste the following script into the code box.
  ```python
  import json
  from datetime import datetime, timedelta

  # 1. GET INPUTS
  iso_date_str = context['iso_date']
  days_offset_str = context['days_offset']

  # 2. VALIDATE INPUTS
  if not iso_date_str or not days_offset_str:
      raise ValueError(f"Missing inputs. Toca sent: {list(context.keys())}")

  # 3. CONVERT OFFSET (Handle '5.0', '5', etc.)
  try:
      # Convert string to float first, then to int to handle "5.0"
      offset_days = int(float(days_offset_str))
  except ValueError:
      raise ValueError(f"Invalid number format for days_offset: '{days_offset_str}'")

  # 4. DATE CALCULATIONS
  # Handle 'Z' for UTC
  start_date = datetime.fromisoformat(iso_date_str.replace('Z', '+00:00'))

  # Calculate future date
  future_date = start_date + timedelta(days=offset_days)

  # 5. OUTPUT
  context['calculated_expiry_date'] = future_date.isoformat()
  context['unix_timestamp'] = int(start_date.timestamp())

  print(f"Expiry: {future_date.isoformat()}")
  ```

![Configured Python Action](/src/assets/cookbook/python_action.png)

- This single script produces two new context variables back to the activity: `calculated_expiry_date`, `unix_timestamp`.

**Step 3: Use the Outputs**
You can now use these variables in subsequent actions. For example, you could save the `calculated_expiry_date` to a datastore, or use the `unix_timestamp` in a call to an external API that may require it.
