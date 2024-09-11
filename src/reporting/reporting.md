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
- Job Input Names - This allows you to search for particular variables being used as an input to a Job
- Job Input Values - Allows you to search for particular values being used as an input for a Job
- Job Output Names - Filter jobs based on the name of the output variables returned
- Job Output Values - Filter jobs based on the values of the output variables returned
- Failed Activities - Return jobs which contain failed activities, useful for identifying jobs which may have failed but continued

Many of the columns in the jobs page can be sorted by clicking on the column header.

 **Further Options**
- Open workflow - Opens the workflow designer in a separate tab.
- Open project - Opens the project that the workflow belongs to in a separate tab.
- Rerun job - This will rerun the job with the exact same inputs etc as it was previously run.
- Open rerun - This will open the report of a job's rerun. (Hidden by default - Show by using the 'Show rerun info' found in the ⋮ menu at the top right of the page)

**Queries** -  The jobs which appear in the jobs page are those which adhere to the current query. This query can be seen by pressing the query button in the top right hand corner. The query fields are as such:
- Field - A selection of categories to filter on, many of which are represented via the columns in the jobs page.
- Operator - This will depend on the field chosen as part of that query line. Many fields will give the operator 'equals' or 'doesn't equal', whereas those which relate to time will show 'before' or 'after'.
- Value - The input will be appropriate for the selected field - values will be suggest where possible and date/time fields will use a custom selector.
 > N.B  It is also possible to query dates based on relative or static criteria. An example of a relative query would be 'show me all jobs in the last 7 days', which would be relative to today. A static date could be 'show me all jobs since 04/09/1998'
- And/or - Denotes whether this line of the query is relevant as well as the rest of it, or in contrast to it.

- Multi-line - A query may have multiple lines to specify a heightened set of criteria and display a more specific set of jobs.
- Group queries - Lines of a query can be grouped together so that their conditions are inextricably linked. Groups can exist within groups.

The jobs list will only be updated once the 'update query' button has been pressed. Changes to the query will only be permanently saved if the report is saved.

 **Dashboards** - Dashboards are a way of visualising your reporting data. Each report can have multiple dashboards which illustrate different things. Create a dashboard by pressing the '+' icon in the top left corner. More about :docs-link[Dashboards]{id="reporting/dashboards"}.

 ![Reporting Diagram](/src/assets/reporting.png)

**Deleting Job Data** - Jobs can be deleted individually by selecting the checkboxes and pressing 'delete selected'. Jobs selected in this way will not be permanently deleted and may still appear as greyed out in your jobs list if 'show deleted jobs' is set to true.

Greyed out jobs will be shown as 'awaiting deletion' and will only be permanently deleted once the schedule you have set is executed.

**Notes On Multiple Selection** - Deleting, re-running and cancelling jobs via the checkboxes are enabled/disabled based on the jobs selected, however for ease of use we allow mixed selection and only execute the request on selected jobs if it makes sense. As an example, Only a Running or Queued job may be cancelled, so if you select a running job and a completed job, pressing 'Cancel jobs' will only submit the running job to be cancelled.

Re-running multiple jobs will queue with a slight delay between each job, and in the order they were selected.
If the 'all items' checkbox was used to select all jobs on the page, the jobs will be queued from order of top to bottom.

**Downloading Job Report Data** - Pressing the 'Download report' button will download a CSV to the users machine which will contain the data of every job which adheres to the current query.

**Reporting levels** - There are circumstances where you may want to decrease your reporting level due to large amounts of data which can build up unnecessarily.

To change the reporting level of a job, enter the workflow designer and access the workflow settings by pressing the cog icon. There are 4 reporting levels which are presented in descending order:
- Debug - This option will provide all data which is available as part of the report including all action data.
- Actions - Will return every action which was run as part of the job but none of its outputs.
- Nodes - Will only show the nodes of the workflow e.g start, activity, exclusive, finish.
- Errors - This, the lowest level of report, will only show the errors which have caused a job to fail.
