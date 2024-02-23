# Default Values

Default values can be provided for most column types, which allows you to insert a value into a column even when an explicit value is not provided.
You can set a "hardcoded" default value which will always be used if a value is not provided.
Alternatively, some types (e.g. a `DateTime` or `UUID` type) give you the option to auto generate a value when:
- the row is created
- the row is updated

Below is a list of types and their default value options:

| Type | Default Value | Auto generate on Creation | Auto generate on Update |
| --- | ---- | --- | --- |
| String | A hardcoded static piece of text | N/A | N/A |
| Number | A constant number | N/A | N/A |
| Boolean | Either `true` or `false` | N/A | N/A |
| Time |  N/A | Will insert the time when the row was created | N/A |
| Date |  N/A | Will insert the date when the row was created | N/A |
| DateTime |  N/A | Will insert the date and time when the row was created | Will insert the date and time whenever the row is updated |
| File |  N/A | N/A | N/A |
| Image |  N/A | N/A | N/A |
| JSON | A harcoded piece of valid JSON e.g. `[ ]` or `{ }` | N/A | N/A |
| UUID | N/A | Generate a random and unique ID when the row is created | N/A |
| Table Relation | N/A | N/A | N/A |
