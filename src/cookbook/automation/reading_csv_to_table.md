# Reading a CSV/Excel file into a Table

There are several reasons you might want to import an **.xlsx** or **.csv** file into Toca. For example, a third-party system may only generate output data in CSV format, or you may have a large dataset stored in an Excel spreadsheet that you’d like to load into Toca for analysis and exploration. Toca makes ingesting this data easy with the **XLSX/CSV to Table** action.

![Action location](/src/assets/cookbook/table_to_csv_action_location.png)

First, lets ingest the sample .csv file below. This file contains records for 5 users of a system.

[Sample CSV File](https://support.staffbase.com/hc/en-us/article_attachments/360009197031/username.csv)

The input data looks like this.
~~~
| Username | Identifier | First name | Last name |
| :-- | :-- | :-- | :-- |
| booker12 | 9012 |Rachel | Booker |
| grey07 | 2070 | Laura | Grey |
| johnson81 | 4081 | Craig | Johnson |
| jenkins46 | 9346 | Mary | Jenkins |
| smith79 | 5079 | Jamie | Smith |

~~~

To ingest this data, we need the file to be available on the bot to which the activity is assigned. Once this file has been uploaded to the bot, drag a **XLSX/CSV to Table** action onto the action canvas and, within the action configuration, specify a name for your table, the type of file to be ingested and use the file navigator in the "File" input to select the .csv file from the bot. 

When ingesting this file, we have the option to specify the index of the header row. In this example, this will be "0".

Running this action should produce the output shown in the image below.

![CSV Ingestion](/src/assets/cookbook/csv_ingestion.png)

The resultant table can now be used as any other table in Toca. For example, it could be saved permanently to a datastore or it could be fed directly into a data processor action to perform further analysis or transformations on the data.


Next we will look at ingesting the .xlsx file available below.

[Sample XLSX File](https://file-examples.com/wp-content/storage/2017/02/file_example_XLS_1000.xls)

The .xlsx file we will use for this example contains 1000 rows of details about people. The process of ingesting these 1000 rows is much the same as for the .csv file earlier but this time we will select "XLSX (Excel)" as the file type and specify both a sheet name and a header row index as shown in the image below.

![XLSX Ingestion](/src/assets/cookbook/xlsx_ingestion.png)

After running this action, we can see the output within the console; a Toca table with 1000 rows as per the input file. Again, the resultant table can now be used in a multitude of ways within Toca.
