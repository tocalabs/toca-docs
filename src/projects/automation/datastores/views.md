# Views

A View is a virtual read-only table which is created by a query, which can include columns from one or more tables in a datastore. This is very useful for scenarios where you are using a common query to display a subset of data on a page of your App or you need to create a single table which encapsulates data from multiple tables so you can query it.

![View Diagram](/src/assets/view.png)

### Features of a View

#### Queries

#### Joins

#### Aliases

### Where you can use a View

Since a View is a read-only Table, you can use a View anywhere that you read Table data and it will behave exactly the same as a Table. This includes but is not limited to:
- Automation Actions
  - Get Table Data
  - For Each Row
  - Get Table Information
  - Table to XLSX/CSV
  - Table to List
- App Pages
  - Dynamic Page Datasource
- App Components
  - Repeating Layout
  - Dynamic Data Wrapper
  - Select Field
  - Table Component
  - Chart and Apex Chart components
- IPL Actions
  - Get Table Data with Query
  - Get Table Information
  - Get Datastore Value

### Limitations of a View

Whilst a View is very similar to a Table, the main difference is that a View is read only. This means that you cannot add a row to a view or update a row in a view. If you want to update the contents of a View, you either have to update the contents from the tables that the view is made up of, or you need to update the query that was used to build the View.

Additionally, as a View is quite involved to create, you cannot currently create or update a View from an action as you might a regular Table. You can only create or update a View from the Datastore.

Thirdly, a View can only access Tables within the same Datastore it is created in, so bear that in mind when it comes to structuring your Datastores.

Lastly, you cannot create a local View in an Activity, a View can only exist as a Datstore variable. This is because behind the scenes it is actually stored as an [SQL View](https://en.wikipedia.org/wiki/View_(SQL)) and there is no way to store a View locally to an Activity.
