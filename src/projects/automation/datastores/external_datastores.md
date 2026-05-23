# External Datastores

External datastores are a variant of Datastore where the source of the data is outside of the main Toca platform.

By connecting your Toca platform to an existing external database, you can leverage all of the power of automation on it, as well as query and use the data in your apps as well.

### Benefits compared to a standard Datastore

- Faster prototyping - Plug straight into your existing database without having to migrate your data.
- Single source of truth - Useful if you have other platforms accessing the same data, as you will not have to synchronise or duplicate your data
- More robust ability when it comes to auditing data

### Limitations compared to a standard Datastore

- Higher latency - as API requests go through Toca and then land on your external database server, the latency can be higher than using standard datastores
- No table modification or creation - while you can connect to your external database through Toca, we currently do not support creation of new tables, or modification of the columns or indexes on existing tables

## Configuration and setup

You can set up an external datastore from the workspace homepage, clicking on the plus icon while having datastores selected in the lower pane. Select 'External' when prompted, then enter in your external connection details.
Most important of these is the connection string, which takes precedence over the other fields, in most scenarios you will also be required to select a database schema - once you have finished setting up the rest of your connection details, click the 'fetch schemas' button to poll the server for available schemas, then select the one you want from the dropdown.

If your external server is firewalled or has other connection security, you will likely have to set up SSH Tunnelling as well to allow the Toca server to establish a connection, consult your local IT team or database provider for these credentials and options.

After adding the connection info, SSH info (if required), and selected a schema, you can click 'Test Connection', if successful you should see your tables appear at the bottom of the screen, if you see results but not the tables you are expecting, you may have selected the wrong schema.

> The connection string can handle options which do not have associated fields in the connection setup UI, and is recommended for advanced users.

## Other notes and quirks

- While 'Subscribe to changes' is supported on external datastore tables in apps, this will only work if the data is updated via Toca. If the table data is updated externally the user will only see it on the next table refresh.
