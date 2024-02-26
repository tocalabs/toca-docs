# Default Values

Default values can be provided for most column types, this allows you to insert a value into a column even when an explicit value is not provided.

You can set a "hardcoded" default value which will always be used if a value is not provided.
Alternatively, some types (e.g. a `DateTime` or `UUID` type) give you the option to auto generate a value when:
- the row is created
- the row is updated

Below is a list of types and their default value options:

| Type | Default Value | Auto generate on Creation | Auto generate on Update |
| --- | ---- | --- | --- |
| String | A hardcoded static piece of text | - | - |
| Number | A constant number | - | - |
| Boolean | Either `true` or `false` | - | - |
| Time |  - | Will insert the time when the row was created | - |
| Date |  - | Will insert the date when the row was created | - |
| DateTime |  - | Will insert the date and time when the row was created | Will insert the date and time whenever the row is updated |
| File |  - | - | - |
| Image |  - | - | - |
| JSON | A harcoded piece of valid JSON e.g. `[ ]` or `{ }` | - | - |
| UUID | - | Generate a random and unique ID when the row is created | - |
| Table Relation | - | - | - |

To read more about the data types mentioned above, read :docs-link[here]{id="projects/automation/datastores/tables/data_types"}. To find out more about table relationships read the :docs-link[next page]{id="projects/automation/datastores/tables/table_relationships"}.
