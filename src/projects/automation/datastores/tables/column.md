# Columns

## General

### Label
The text users will see as the header of the column.

### Name
Autopopulated by default by the sanitized string in `Label`. The name cannot have spaces or special characters (replaced with underscores) and must start with a lowercase letter.

Names are the values used in queries, not the lables, so it's essential these names make sense.

### Type
The :docs-link[Data Type]{id="book/programming_concepts/data_types"} to be used in the system.

### Multiline
> `String` only.

Whether the text field is allowed to display newlines and dictates whether the `Enter` key will produce a new line.

### Default Value
> Excluding `Table` types.

The `Set Default Value` flag can be set to allow a default value if one is not provided.

It is not recommended both enabling default values and specifying `Cannot be NULL` at the same time as this may cause data entry issues due to validation.

## Constraints

Constraints are custom alterations to a column to tailor the data to your needs.

### Database Data Type
> `String` only.

The underlying :docs-link[Database Data Type]{id="projects/automation/datastores/tables/database_data_types"} to be used in the database storage.

Getting the Database Data Type correct for querable/joining columns is essential for an efficient automation.

### Unique
> Excluding `TEXT` and `LONGTEXT`.

Enabling this flag will ensure that data in any row for this column can only be present once. Attempting to enter the same value into another row for this column will result in an error being thrown.

### Cannot be NULL
Enabling this flag will ensure there must be a value present upon insertion/updating.

It is not recommended both enabling default values and specifying a `Default Value` at the same time as this may cause data entry issues due to validation.

> Note that an empty string is not the same as `NULL` and will still be valid in this condition.

### Auto Increment
> `Number` only.

Enabling this flag will increment the number for each new row inserted. The incremental number is taken from the highest value inserted so far.

Example:

Three records are added. The values of this column for each row would be 1,2,3 respectively.

If a user adds another row, manually setting the value to 20, subsequent additions would start from the increment of 21.
