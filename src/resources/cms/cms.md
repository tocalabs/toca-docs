# Content Management System (CMS)

CMS, or content management system, is a different way of storing data which is specifically tailored to being displayed in Toca apps.

CMS' can be found primarily via the resources tab of your Toca platform but can also be accessed via your app once they have been linked.

**Files** - Within your CMS you will find a dedicated file storage area. This is where you will select files from when you add content to your CMS later. Once uploaded, files can be previewed by clicking on them.

**Type**: A type is an overarching category of data within a CMS. Each CMS can have many types. For example, a restaurant may have a type 'lunch menu' and a type 'dinner menu'.

**Model**: A model is how you define what types of data you want to add to your CMS and their names. A model is comprised of different fields. A simple restaurant menu may include the fields: 'name', 'price' and 'picture' in the format: 'String', 'number' and 'file'.

**Field**: A field is akin to the column of a table and can accept a variety of data formats. These include:
- String
- Number
- Boolean
- JSON
- Markdown
- File

**Hidden Fields** - A CMS model will also contain a number of hidden fields which will always be populated automatically. The viewing of hidden fields can be toggled on or off. These include:
- ID - The unique ID of the item.
- Status - whether the item is in draft or published.
- Created - The time when the item was created.
- Updated - The last time anything within that item was updated.
- Author - The user which created that item.

**Add content**: When adding content you will see a modal which contains every field which you have defined as part of your model. This content will be added as a row within that CMS type.

**Publish**: Within the content modal you will have the ability to publish certain items of content. Published items will have a cloud icon which is highlighted in pink.

**CMS configuration (Apps)** - In the miscellaneous section of your apps settings you will see 'CMS configuration' with some options.
- Default statuses - This sets whether you want draft or published content to be shown by default.
- Show all in preview - Whether you want all CMS data to be shown when you enter preview mode.

**Examples**

**Dynamic page** - A CMS can be used to drive the content of a dynamic page. 
**Repeating layout** - A CMS can also be used as the data source for a repeating layout wherein each item of content will render in the layout. At the point where you are choosing the CMS as the data source you will also notice the 'status override' option which gives you the option of overriding which data is set to be displayed at an app level.
