# Data Types

## What are Types?

Every value that you come across in Toca has three properties:
- The key - This is the identifier that is used to "name" the value
- The type - This is the classifier that tells Toca how this value is intended to be used
- The value - This is the actual value

If you think of every value as a box, a box needs a label (the **key**) so that you can easily identify what is in the box, we also have a classifier that tells us what sort of thing to expect in the box (the **type**) and lastly you have the thing in the box (the **value**).

Whilst the key is useful for identifying the value, the type is of equal importance as it tells us how we can use the value.
For example, if the value is a `Number` we know we can use that for mathematical operations. If the value is a `File` we know that we can perform file system operations on the value.

Types also help us to make our software safer and more robust as it allows us to make guarantees about our programme such as "I can only add a `Number` to a `Number`" or "I can only iterate over values in a `List`".
This is a good way of preventing errors which could occur whilst our Application is running such as what might happen if you attempted to make a `Table` uppercase instead of some text!

Within Toca there are two categories of types:
1. Base Types - Types that hold a single value
2. Collection Types - Types that store multiple values

## Base Types

### String

A `String` type represents text content and is probably the most common type that you'll deal with in Toca. It may seem odd to refer to text as a `String` but this is a term that is used very commonly in computing, it is supposedly due to text being referred to as a "string of characters" where a character represents a letter.

A value of type `String` in Toca is a variable-length piece of text that can range from a single letter all the way to thousands of words and it can contain any valid [UTF-8](https://en.wikipedia.org/wiki/UTF-8) characters. They also support escape characters to enable formatting such as:
- `\n` - newline character
- `\t` - tab character
- `\r` - carriage return character

There is no real upper limit on how many letters can be stored within a single `String` type but once you start getting to the 100,000's of characters, you might notice some performance issues when trying to view the value.

> #### Warning ⚠️
>
> `String` type values cannot contain 2 or more instances of `$$` as these are reserved characters used behind the scenes to denote variables and datachips.

#### Casting

`Strings` are fairly unique in that almost all other types can be converted to a `String` as you may want to view a number as text or convert a `List` to a comma delimited list of text.

#### Operators

When you need to compare `Strings` then they are only able to be compared in two ways, they are either equal to each other or not.

| Operator | Description |
| :--- | :--- |
| `LHS == RHS` | True when Left Hand Side (LHS) is the same as the Right Hand Side (RHS) |
| `LHS != RHS` | True when LHS is **NOT** the same as RHS |


### Number

The `Number` type can represent any sort of number, whether it is an integer, a negative number or decimal number. Behind the scenes, the value is always stored as a decimal number, even if that means specifying an additional `.0` on the value. By storing all number values consistently behind the scenes it means they can all be treated in the exact same way and you don't have to worry about conversion between different number types like you might have to do when coding.

A `Number` type allows for the following range:
- Max: 1.79x10³⁰⁸
- Min: -1.79x10³⁰⁸

It has a precision of approximately 15-17 digits.

A `Number` type can contain only digits, it does not support constants such as `π`, `e` or `τ`. In some places, it does support scientific E notation so for example you can set a `Number` variable of 2E10 and this will result in 20,000,000,000.

![E Notation Example](/src/assets/book/e_notation.png)

#### Casting

It is worth noting that if you convert a value of type `Number` to a `String`, the behaviour will change slightly depending on if the underlying value is a whole number (integer) or a decimal. If the underlying value is a valid integer then it will not include any decimal points, if the value is a valid decimal then it will keep all relevant significant figures.

For example:
`4.5` will be converted to `"4.5"`
`4.0` will be converted to `"4"`

This is because when treating a whole number as text, it is seldom desired to include `".0"`.

#### Operators

When using `Number` values, you are typically using them to obtain the result of a mathematical equation or using them in some sort of comparison such as "Filter data where `{number}` is greater than 100". When you are performing these comparisons, it is good to know what operators are available to you.

| Operator | Description |
| :--- | :--- |
| `LHS == RHS` | True when Left Hand Side (LHS) is the same as the Right Hand Side (RHS) |
| `LHS != RHS` | True when LHS is **NOT** the same as RHS |
| `LHS > RHS` | True when LHS is greater than RHS |
| `LHS >= RHS` | True when LHS is greater than or equal to RHS |
| `LHS < RHS` | True when LHS is less than RHS |
| `LHS <= RHS` | True when LHS is less than or equal to RHS |

### Boolean

A `Boolean` type represents only two possible values: `true` and `false`. This type is most useful for representing states which can only be either true or false, on or off, enabled or disabled.

`Boolean` values are usually used as a way to configure a conditional flow of logic. For example: "If `{boolean}` is true, then perform actions."

#### Operators

| Operator | Description |
| :--- | :--- |
| `LHS == RHS` | True when Left Hand Side (LHS) is the same as the Right Hand Side (RHS) |
| `LHS != RHS` | True when LHS is **NOT** the same as RHS |
| `!LHS` | **NOT** LHS, this returns the opposite value to LHS, so if LHS is `true` this would return `false` |

### Date Time

A `DateTime` type represents an instant in time, typically expressed as a date and a time of day. Dates and time are difficult as there are many factors to take into account in how a date and time is measured and formatted, such as what calendar is the date represented by and what format should it be displayed in? Month first? Day first? Year first? The `Datetime` type aims at being an agnostic way of storing a static point in time which can then be formatted down to the users preference in the future.

In general, dates and time are stored throughout the system in the format of `yyyy-MM-ddTHH:mm:ssZ`, this adheres to [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) formatting.
So this means that 9AM on the 5th September 2018 would be stored as:

`2018-09-05T09:00:00Z`

When you wish to format a date into a particular format there are automation actions and app components which will allow you to do this so you can represent your date in the exact way you want. You can take a look at:
- :docs-link[Format / Convert Date]{id="FormatDate" type="Action"}
- :docs-link[ISO Date Parser]{id="6a6c986-ce3d-4d22-b18a-16d3d704db10" type="AppComponent"}


#### Casting

`DateTime` values can only be cast to text via explicit actions such as Format / Convert Date as otherwise Toca doesn't know what format to store the date and time in.

### Password

### File

### Image

### Identity


## Collections
- List
- Coordinates
- Bounding Box
- Grid
- JSON
- Table

### List


### Coordinates


### Bounding Box


### Grid


### JSON


### Table

## Null



## Casting and Converting

- Rules
- Matrix of Types vs Types
