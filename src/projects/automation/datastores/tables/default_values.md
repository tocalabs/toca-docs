# Default Values

Default values can be provided for most column types, which allows you to insert a value into a column even when an explicit value is not provided.
You can set a "hardcoded" default value which will always be used if a value is not provided.
Alternatively, some types (e.g. a `DateTime` or `UUID` type) give you the option to auto generate a value when:
- the row is created
- the row is updated

