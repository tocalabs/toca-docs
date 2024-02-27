# Dynamic Page

A dynamic page is a page that is driven by data from a datasource such as a table in a datastore. It allows for a design to be implemented and then repeated for every row of data in the datasource.

Dynamic Pages support both **:docs-link[Tables]{id="projects/datastores/tables"}** and **:docs-link[CMS Types]{id="resources/cms/types"}** as data sources.

The data from the data source is available to each component and app action on the dynamic page through the `Context` object.

![Dynamic Page Diagram](/src/assets/dynamic_page.png)

## Data Sources

There are two types of data source which are supported in a dynamic page:

1. Table - Each page produced by the dynamic page represents a single row of data
2. CMS Type - Each page produced by the dynamic page represents a single content entry

![Dynamic Page Example](/src/assets/dynamic_page_example.png)
