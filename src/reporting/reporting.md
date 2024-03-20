# Overview of Reporting

Reporting is a Toca user's hub for anything related to the jobs which are being run at any given time. A user can have multiple reports to accommodate for different queries and dashboards. The current report is denoted in the top left alongside dropdown options to switch reports or create a new one.

**Jobs page** - The jobs page is the default home screen for reporting. Here you will see every job which your user has the permissions to see, (at least 'read'), and which adheres to the current query. New jobs which have just been run will appear at the top of the feed.

**Columns**
- Name - The name of the job.
- Duration - How long the job took to run.
- Queued - When the user queued the job.
- Started - When the job began to run.
- Finished - The time when the job finished.
- Triggered by - the method via which the job was triggered e.g via schedule, listener, app user etc.
- Publish state - The version of the job which was run. This could be either: draft, published or previous.
- Bots - Hovering over either the monitor or cloud icons will show you which bot the job ran on and the corresponding bot version. This is useful for debugging.

Many of the columns in the jobs page can be sorted by clicking on the column header.

 **Further Options**
- Open workflow - Opens the workflow designer in a separate tab.
- Open project - Opens the project that the workflow belongs to in a separate tab.
- Rerun job - This will rerun the job with the exact same inputs etc as it was previously run.

**Queries** -  The jobs which appear in the jobs page are those which adhere to the current query. This query can be seen by pressing the query button in the top right hand corner. The query fields are as such:
- Field - A selection of categories to filter on, many of which are represented via the columns in the jobs page.
- Operator - This will depend on the field chosen as part of that query line. Many fields will give the operator 'equals' or 'doesn't equal', whereas those which relate to time may show 'before' or 'after'.
- Value - This field will often show a dropdown list of available options based on which field has been chosen as part of that query line. Other examples include a separate modal popup if the field relates to time.
 > N.B  It is also possible to query based on relative or static criteria. An example of a relative query would be 'show me all jobs in the last 7 days', which would be relative to today. A static date could be 'show me all jobs since 04/09/1998'
- And/or - Simply denotes whether this line of the query is relevant as well as the rest of it, or in contrast to it.

- Multi-line - A query may have multiple lines to specify a heightened set of criteria and display a more specific set of jobs.
- Group queries - Lines of a query can be grouped together so that their conditions are inextricably linked. Groups can exist within groups.

The jobs list will only be updated once the 'update query' button has been pressed. Changes to the query will only be permanently saved if the report is saved.

 **Dashboards** - Dashboards are a way of visualising your reporting data. Each report can have multiple dashboards which illustrate different things. Create a dashboard by pressing the '+' icon in the top left corner. More about dashboards - **Link to dashboard page**

 ![0a007eba3299d28b01eee59a363b0548.png](./0a007eba3299d28b01eee59a363b0548.png)

**Deleting Job Data** - Jobs can be deleted individually by selecting the checkboxes and pressing 'delete selected'. Jobs selected in this way will not be permanently deleted and may still appear as greyed out in your jobs list if 'show deleted jobs' is set to true.

Greyed out jobs will be shown as 'awaiting deletion' and will only be permanently deleted once the schedule you have set is executed.

**Downloading Job Report Data** - Pressing the 'Download report' button will download a CSV to the users machine which will contain the data of every job which adheres to the current query.
  
**Reporting levels** - There are circumstances where you may want to decrease your reporting level due to large amounts of data which can build up unnecessarily.

To change the reporting level of a job, enter the workflow designer and access the workflow settings by pressing the cog icon. There are 4 reporting levels which are presented in descending order:
- Debug - This option will provide all data which is available as part of the report including all action data.
- Actions - Will return every action which was run as part of the job but none of its outputs.
- Nodes - Will only show the nodes of the workflow e.g start, activity, exclusive, finish.
- Errors - This, the lowest level of report, will only show the errors which have caused a job to fail.
