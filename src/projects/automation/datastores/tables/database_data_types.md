### Database Data Types
Datatype customizations have been added for `String` columns. You are now able to specify the database data type you wish to use per column.
You can find these data types in the `Update Column` modal in the Datastore edit screen.
![data_type](/src/assets/releases/8_0/datatype.png)

#### VARCHAR(n)
Variable-length string with a maximum length of n (1 to 65,535 characters, depending on row size and storage).
Stores only the actual length of the string, plus 1-2 bytes for length metadata.
More efficient for short, frequently updated text fields.

#### CHAR(n)
Fixed-length string of n characters (1 to 255).
Always occupies n bytes, padded with spaces if the string is shorter.
Best for fixed-size values like codes or abbreviations.

#### TEXT Types (Used for large text storage, cannot have default values)
**TEXT** – Up to 65,535 characters (2-byte length indicator).
**LONGTEXT** – Up to 4,294,967,295 characters (4-byte length indicator).