# Building in the Toca Development Kit (TDK): A Complete Guide

## Overview

The Toca Development Kit (TDK) is a powerful in-platform development environment that enables you to extend Toca's capabilities without leaving the platform. This guide will teach you how to build custom functionality that integrates seamlessly with Toca's automation and app ecosystem.

## What You Can Build

The TDK supports four main types of extensions:

| Extension Type | Purpose | Technology | Use Cases |
|---|---|---|---|
| **Automation Actions** | Custom workflow steps | C# | Data processing, calculations, integrations |
| **Connectors** | API endpoints for workflows | C# | External system integration, webhook handling |
| **App Components** | User interface elements | React | Custom UI controls, data visualization |
| **App Actions** | Interactive page logic | TypeScript | User interactions, data manipulation |

### Real-World Examples

- **Custom Connectors**: Transform XML data to JSON for legacy system integration
- **Automation Actions**: Calculate text differences for document comparison workflows
- **App Components**: Build hierarchical menu structures with React
- **App Actions**: Create date difference calculators with custom formatting

## Key Benefits

✅ **No External Dependencies**: Everything runs within the Toca platform  
✅ **Immediate Deployment**: Test and deploy without leaving the TDK  
✅ **Shareable**: Package extensions into reusable packs  
✅ **Integrated**: Full access to Toca's platform capabilities

---

## Building Automation Actions

### Understanding Action Architecture

Every automation action follows a three-part structure:

```
┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│   INPUTS    │ -> │    LOGIC    │ -> │   OUTPUTS   │
│             │    │             │    │             │
│ User-defined│    │ C# code     │    │ Returned    │
│ parameters  │    │ execution   │    │ results     │
└─────────────┘    └─────────────┘    └─────────────┘
```

### Step-by-Step: Building a DateTime Modifier Action

Let's create a comprehensive example by building a `Modify DateTime` action that demonstrates all core concepts.

#### Step 1: Planning Your Action

**Objective**: Create an action that modifies a datetime by adding or subtracting time units.

**Requirements Analysis**:
- Input: Base datetime value
- Input: Time unit (days, hours, minutes, seconds)
- Input: Quantity to add/subtract (positive or negative)
- Input: Error handling preference
- Output: Modified datetime
- Output: Human-readable description of the change

#### Step 2: Designing the Inputs

Configure your input controls by dragging them from the left panel:

| Control Type | Parameter Name | Description | Validation |
|---|---|---|---|
| DateTime Picker | `dateToModify` | The starting datetime | Required |
| Dropdown | `unit` | Time unit to modify | Options: days, hours, minutes, seconds |
| Number Input | `valueToAdd` | Amount to add/subtract | Allow negative values |
| Checkbox | `failOnError` | Error handling behavior | Default: true |

**Pro Tip**: Use descriptive parameter names that clearly indicate their purpose in your code.

#### Step 3: Implementing the Logic

Here's the complete C# implementation with comprehensive error handling:

```csharp
// Input validation
if (string.IsNullOrWhiteSpace(dateToModify))
{
    throw new ArgumentException("Date to modify cannot be empty");
}

if (string.IsNullOrWhiteSpace(unit))
{
    throw new ArgumentException("Time unit must be specified");
}

try
{
    // Parse the input datetime
    var date = DateTime.Parse(dateToModify);
    DateTime modifiedDate;
    string operationDescription;

    // Determine the operation description
    string operation = valueToAdd >= 0 ? "added" : "subtracted";
    string absoluteValue = Math.Abs(valueToAdd).ToString();

    // Perform the datetime modification
    switch (unit.ToLower())
    {
        case "days":
            modifiedDate = date.AddDays(valueToAdd);
            operationDescription = $"{operation} {absoluteValue} {unit}";
            break;
        case "hours":
            modifiedDate = date.AddHours(valueToAdd);
            operationDescription = $"{operation} {absoluteValue} {unit}";
            break;
        case "minutes":
            modifiedDate = date.AddMinutes(valueToAdd);
            operationDescription = $"{operation} {absoluteValue} {unit}";
            break;
        case "seconds":
            modifiedDate = date.AddSeconds(valueToAdd);
            operationDescription = $"{operation} {absoluteValue} {unit}";
            break;
        default:
            throw new ArgumentException($"Invalid time unit: {unit}. Valid options are: days, hours, minutes, seconds");
    }

    // Return the results
    AddResult("modifiedDate", modifiedDate, ActionTypes.DateTime);
    AddResult("operationDescription", operationDescription, ActionTypes.Text);
    AddResult("originalDate", date, ActionTypes.DateTime);
    
    Action.Status = ActionStatus.Success;
}
catch (Exception ex)
{
    if (failOnError)
    {
        Action.Status = ActionStatus.Failed;
        throw new Exception($"DateTime modification failed: {ex.Message}");
    }
    else
    {
        // Log the error but continue
        AddResult("error", ex.Message, ActionTypes.Text);
        Action.Status = ActionStatus.Warning;
    }
}
```

#### Step 4: Configuring Outputs

Add these outputs to make your action results accessible:

| Output Name | Type | Description |
|---|---|---|
| `modifiedDate` | DateTime | The calculated result |
| `operationDescription` | Text | Human-readable description |
| `originalDate` | DateTime | The original input for reference |
| `error` | Text | Error message (if any) |

#### Step 5: Testing Your Action

**Testing Strategy**:
1. **Select a Test Bot**: Choose a bot from the bot panel for testing
2. **Configure Test Inputs**: Switch to preview mode and enter test values
3. **Run Test Cases**: Execute multiple scenarios to validate behavior

**Recommended Test Cases**:
```
Test Case 1: Add days
- dateToModify: "2025-01-01T00:00:00Z"
- unit: "days"
- valueToAdd: 30
- Expected: "2025-01-31T00:00:00Z"

Test Case 2: Subtract hours
- dateToModify: "2025-01-01T12:00:00Z"
- unit: "hours"
- valueToAdd: -6
- Expected: "2025-01-01T06:00:00Z"

Test Case 3: Invalid unit (error testing)
- dateToModify: "2025-01-01T00:00:00Z"
- unit: "invalid"
- valueToAdd: 1
- Expected: Error message
```

### Advanced Concepts: Building Action Libraries

As you develop more actions, you'll discover common functionality that can be shared. This is where **Action Helpers** become essential.

#### Creating a Helper Library

Action Helpers are C# classes that function as shared libraries:

```csharp
public class DateTimeHelper
{
    public static string FormatDateTimeForDisplay(DateTime dateTime, string format = "yyyy-MM-dd HH:mm:ss")
    {
        return dateTime.ToString(format);
    }
    
    public static bool IsBusinessDay(DateTime dateTime)
    {
        return dateTime.DayOfWeek != DayOfWeek.Saturday && 
               dateTime.DayOfWeek != DayOfWeek.Sunday;
    }
    
    public static DateTime GetNextBusinessDay(DateTime startDate)
    {
        var nextDay = startDate.AddDays(1);
        while (!IsBusinessDay(nextDay))
        {
            nextDay = nextDay.AddDays(1);
        }
        return nextDay;
    }
}
```

#### Using Helpers in Actions

```csharp
// Import and use the helper
var helper = new DateTimeHelper();
var formattedDate = DateTimeHelper.FormatDateTimeForDisplay(modifiedDate);
var isBusinessDay = DateTimeHelper.IsBusinessDay(modifiedDate);

AddResult("formattedDate", formattedDate, ActionTypes.Text);
AddResult("isBusinessDay", isBusinessDay, ActionTypes.Boolean);
```

---

## Building Connectors

### Understanding Connector Architecture

Connectors transform your workflows into consumable APIs, acting as the bridge between external systems and your Toca workflows.

```
External Request -> Connector Handler -> Workflow -> Connector Response -> External System
```

### Connector Components

#### 1. Handler
The Handler is the entry point that processes incoming requests:
- Validates authentication
- Parses request data
- Prepares data for the workflow
- Handles errors and edge cases

#### 2. Responses
Response definitions control how your API responds:
- Success responses with data
- Error responses with appropriate status codes
- Custom headers and formatting

### Building a Webhook Connector Example

Let's create a connector that receives product updates via webhook:

```csharp
// Handler Code
public class ProductUpdateHandler
{
    public void ProcessRequest()
    {
        try
        {
            // Validate API key
            var apiKey = Request.Headers["X-API-Key"];
            if (string.IsNullOrEmpty(apiKey) || !IsValidApiKey(apiKey))
            {
                SetResponse("unauthorized", 401);
                return;
            }

            // Parse JSON body
            var requestBody = Request.Body;
            var productData = JsonConvert.DeserializeObject<ProductUpdate>(requestBody);

            // Validate required fields
            if (string.IsNullOrEmpty(productData.ProductId))
            {
                SetResponse("badRequest", 400, "Product ID is required");
                return;
            }

            // Pass data to workflow
            SetWorkflowVariable("productId", productData.ProductId);
            SetWorkflowVariable("productName", productData.Name);
            SetWorkflowVariable("price", productData.Price);
            SetWorkflowVariable("lastUpdated", DateTime.UtcNow);

            // Execute the workflow
            ExecuteWorkflow();
        }
        catch (Exception ex)
        {
            SetResponse("error", 500, $"Internal server error: {ex.Message}");
        }
    }

    private bool IsValidApiKey(string apiKey)
    {
        // Implement your API key validation logic
        return !string.IsNullOrEmpty(apiKey) && apiKey.Length >= 32;
    }
}

// Response Definitions
// Success Response (200)
{
    "status": "success",
    "message": "Product updated successfully",
    "productId": "{{productId}}",
    "timestamp": "{{lastUpdated}}"
}

// Error Response (400)
{
    "status": "error",
    "message": "{{errorMessage}}",
    "timestamp": "{{DateTime.UtcNow}}"
}
```

---

## Building App Components

### Component Development with React

App Components extend Toca's user interface capabilities using React. They integrate seamlessly with the platform's design system and data flow.

#### Basic Component Structure

```jsx
import React, { useState, useEffect } from 'react';
import { TocaComponent } from '@toca/component-library';

const CustomTreeMenu = ({ data, onItemSelect, theme }) => {
    const [expandedNodes, setExpandedNodes] = useState(new Set());
    const [selectedItem, setSelectedItem] = useState(null);

    const toggleNode = (nodeId) => {
        const newExpanded = new Set(expandedNodes);
        if (newExpanded.has(nodeId)) {
            newExpanded.delete(nodeId);
        } else {
            newExpanded.add(nodeId);
        }
        setExpandedNodes(newExpanded);
    };

    const handleItemClick = (item) => {
        setSelectedItem(item);
        onItemSelect(item);
    };

    const renderTreeNode = (node) => (
        <div key={node.id} className="tree-node">
            <div 
                className={`tree-item ${selectedItem?.id === node.id ? 'selected' : ''}`}
                onClick={() => handleItemClick(node)}
            >
                {node.children && (
                    <button 
                        className="expand-button"
                        onClick={(e) => {
                            e.stopPropagation();
                            toggleNode(node.id);
                        }}
                    >
                        {expandedNodes.has(node.id) ? '▼' : '▶'}
                    </button>
                )}
                <span className="tree-label">{node.label}</span>
            </div>
            {node.children && expandedNodes.has(node.id) && (
                <div className="tree-children">
                    {node.children.map(renderTreeNode)}
                </div>
            )}
        </div>
    );

    return (
        <TocaComponent className={`tree-menu ${theme}`}>
            <div className="tree-container">
                {data.map(renderTreeNode)}
            </div>
        </TocaComponent>
    );
};

export default CustomTreeMenu;
```

---

## Building App Actions

### TypeScript for Interactive Logic

App Actions handle user interactions and data manipulation within Toca apps using TypeScript.

#### Date Difference Calculator Example

```typescript
interface DateDifference {
    years: number;
    months: number;
    days: number;
    hours: number;
    minutes: number;
    seconds: number;
}

class DateDifferenceCalculator {
    calculateDifference(startDate: Date, endDate: Date): DateDifference {
        const start = new Date(startDate);
        const end = new Date(endDate);
        
        // Ensure start is before end
        if (start > end) {
            [start, end] = [end, start];
        }
        
        const years = end.getFullYear() - start.getFullYear();
        const months = end.getMonth() - start.getMonth();
        const days = end.getDate() - start.getDate();
        
        // Calculate total difference in milliseconds
        const totalMs = end.getTime() - start.getTime();
        const totalSeconds = Math.floor(totalMs / 1000);
        const totalMinutes = Math.floor(totalSeconds / 60);
        const totalHours = Math.floor(totalMinutes / 60);
        const totalDays = Math.floor(totalHours / 24);
        
        return {
            years: years,
            months: months,
            days: days,
            hours: totalHours % 24,
            minutes: totalMinutes % 60,
            seconds: totalSeconds % 60
        };
    }
    
    formatDifference(difference: DateDifference, format: 'short' | 'long' = 'long'): string {
        const parts = [];
        
        if (difference.years > 0) {
            parts.push(`${difference.years} ${format === 'long' ? 'years' : 'y'}`);
        }
        if (difference.months > 0) {
            parts.push(`${difference.months} ${format === 'long' ? 'months' : 'm'}`);
        }
        if (difference.days > 0) {
            parts.push(`${difference.days} ${format === 'long' ? 'days' : 'd'}`);
        }
        
        return parts.join(', ') || '0 days';
    }
}

// Usage in an App Action
const calculator = new DateDifferenceCalculator();
const startDate = new Date('2025-01-01');
const endDate = new Date('2025-12-31');

const difference = calculator.calculateDifference(startDate, endDate);
const formattedDifference = calculator.formatDifference(difference);

// Update the UI
updateComponent('dateResult', {
    difference: formattedDifference,
    details: difference
});
```

---

## Best Practices and Tips

### Development Workflow

1. **Plan Before Coding**: Define inputs, outputs, and logic flow
2. **Start Simple**: Build a basic version first, then add complexity
3. **Test Incrementally**: Validate each component before integration
4. **Document Everything**: Add comments and maintain clear naming conventions

### Performance Considerations

- **Minimize API Calls**: Cache data when possible
- **Handle Large Datasets**: Implement pagination and lazy loading
- **Error Handling**: Always include comprehensive error handling
- **Resource Management**: Dispose of resources properly

### Security Best Practices

- **Validate All Inputs**: Never trust user input
- **Sanitize Data**: Clean data before processing
- **Secure API Keys**: Use environment variables, not hardcoded values
- **Authentication**: Implement proper authentication mechanisms

---

## Next Steps

Once you've built your extensions:

1. **Test Thoroughly**: Use the TDK testing environment
2. **Deploy**: Push your extensions to the main platform
3. **Share**: Package functionality into reusable packs
4. **Document**: Create clear documentation for other users

Ready to deploy your creations? Continue to the next section: **Deploying from the TDK**.

---

## Additional Resources

- **TDK API Reference**: Complete documentation of available functions
- **Component Library**: Pre-built components for faster development
- **Community Examples**: Real-world implementations from other developers
- **Troubleshooting Guide**: Common issues and solutions