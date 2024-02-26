# Dynamic Page

A dynamic page is a page that is driven by a data from a datasource such as a table in a datastore. It allows for a design to be implemented and then repeated for every row of data in the datasource.

Dynamic Pages support both **:docs-link[Tables]{id="projects/datastores/tables"}** and **:docs-link[CMS Types]{id="resources/cms/types"}** as data sources.

The data from the data source is available to each component and app action on the dynamic page through the `Context` object.

>> Insert Excalidraw of Table row to Dynamic Page

## Data Sources

There are two types of data source which are supported in a dynamic page:

1. Table - Each page produced by the dynamic page represents a single row of data

If our table of films contained the following data then we could use this to design a page for each page.
- Film title
- Film Poster
- Film Description
- Film rating

>> Insert Excalidraw of this

2. CMS Type - Each page produced by the dynamic page represents a single content entry

Imagine you are building a travel blog and you have created a CMS type that defines a:
- Location
- Stay duration
- Picture album
- Summary
- Food & Drink
- Accomodation
- Culture

You can now design a page that displays all of this information in a consisten format and then see it brought to life for every entry in the CMS type.
