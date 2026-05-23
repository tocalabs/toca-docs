# Dynamic Data Wrapper

The **Dynamic Data Wrapper** is a powerful component designed to provide a dynamic context for nested app components, allowing them to display specific information from a selected data source, such as a table or table view, or a list.

## Purpose

This **Dynamic Data Wrapper** component enables the creation of highly interactive and context-aware sections within your application. By placing other UI components inside a **Dynamic Data Wrapper**, those nested components can automatically access and display data relevant to a specific row or record from a designated data source. This eliminates the need for manual data binding for each individual nested component.

## How it Works

1.  **Data Source Selection:** You configure the **Dynamic Data Wrapper** to point to a specific data source (e.g., a "KPIs" table).
2.  **Context Provision:** When a specific row in the chosen data source is selected (e.g., by clicking on a row in a Data Table, or by an <a id="ipv"></a>In Page Value (IPV) setting a row ID), the **Dynamic Data Wrapper** provides that row's data as a "context" to all components placed within it.
3.  **Dynamic Display:** Nested components (e.g., Text/Label, Number Input, Image components) can then be configured to display fields directly from this contextual data row.

## Configuration Fields

To configure the **Dynamic Data Wrapper**, the following fields are available:

*   **Data Source:** This field requires you to select the data source. This can be a table, table view from a datastore, or a list. It also supports [IPV](#ipv) tables (from version 0.4.0 and above).

    > *Note: You must be using version `0.4.0` or newer of the **Dynamic Data Wrapper** component to use IPV tables as a `Data Source`.*

*   **Column or property (text):** Provide the exact name of the column (for tables, table views, and IPV tables) or property (for lists) within your selected Data Source that you wish to filter by.
*   **Data ID:** Enter the specific value that you want to find within the designated "Column or property." The component will filter the Data Source to return a record where the chosen column's value matches this Data ID. If multiple records match, the component will return the first one found.

![Dynamic Data Wrapper Configuration example](/src/assets/cookbook/dynamic_data_wrapper.png)

## Use Cases

### Displaying KPIs

Place a **Dynamic Data Wrapper** on a dashboard page, pointing it to a "KPIs" table. Inside, use Text/Label components to display individual KPI values (e.g., "Total Sales", "Average Customer Rating") for a selected KPI row.

### Detail View

When a user selects a record in a Data Table, a **Dynamic Data Wrapper** can show a detailed view of that record in a separate section of the page, with various components displaying different attributes of the selected item (e.g., product name, description, price, image).
