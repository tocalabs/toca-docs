# Database Data Types
Datatype customizations are available for `String` columns. A user is able to specify the database data type for a given `String` column.

The data types are found and selected in the `Update Column` modal in the Datastore edit screen.
![data_type](/src/assets/database_datatype.png)

If a database data type supports `(n)` length, a numeric field will appear allowing the set length to be set.

## Supported Database Data Types

### VARCHAR(n)
Variable-length string with a maximum length of n (1 to 65,535 characters, depending on row size and storage. Commonly set as 255).

Stores only the actual length of the string, plus 1-2 bytes for length metadata.

More efficient for short, frequently updated text fields such as names.

### CHAR(n)
Fixed-length string of n characters (1 to 255).

Always occupies n bytes, padded with spaces if the string is shorter.

Best for fixed-size values like codes or abbreviations.

### TEXT Types
`TEXT` types are used for large text storage and cannot have `UNIQUE` indexes.

Due to the large amount of storage being used it is not recommended querying/joining on these fields as the resulting query is likely to be slower.

| Type | Description |
| ---- | ---- |
| **TEXT** | Up to 65,535 characters (2-byte length indicator). |
| **LONGTEXT** | Up to 4,294,967,295 characters (4-byte length indicator).|
