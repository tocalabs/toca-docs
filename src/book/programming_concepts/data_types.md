# Data Types

- Behind Toca there sits a Type System
- What is a Type system?
- Why is useful?

Every value that you come across in Toca has three properties:
- The key - This is the identifier that is used to "name" the value
- The type - This is the classifier that tells Toca how this value is intended to be used
- The value - This is the actual value

If you think of every value as a box, a box needs a label (the **key**) so that you can easily identify what is in the box, we also have a classifier that tells us what sort of thing to expect in the box (the **type**) and lastly you have the thing in the box (the **value**).

Whilst the key is useful for identifying the value, the type is of equal importance as it tells us how we can use the value.
For example, if the value is a `Number` we know we can use that for mathematical operations. If the value is a `File` we know that we can perform file system operations on the value.

Types also help us to make our software safer and more robust as it allows us to make guarantees about our programme such as "I can only add a `Number` to a `Number`" or "I can only iterate over values in a `List`".
This is a good way of preventing errors which could occur whilst our Application is running such as what might happen if you attempted to make a `Table` uppercase instead of some text!

Within Toca there are two main Types:
1. Base Types - Simple types that hold a single value
2. Collections - More complex types that can store many values

## Base Types

- String
- Number
- Boolean
- Date Time
- Image
- File

### String

Probably the most common type that you'll deal with in Toca, a `String` type represents text content. It may seem odd to refer to text as a `String` but this is a term that is used very commonly in computing, it is supposedly due to text being referred to as a "string of characters" where a character represents a letter.

A value of type `String` in Toca is a variable-length piece of text that can range from a single letter all the way to thousands of words and it can contain any valid ![UTF-8](https://en.wikipedia.org/wiki/UTF-8) characters.

#### Casting

`Strings` are fairly unique in that almost all other types can be converted to a `String` as you may want to view a number as text or convert a `List` to a comma delimited list of text.

`Strings` are _truthy_. Empty `Strings` are _falsey_.

`Strings` can be multiline, they also support escape characters such as `\n` or `\t`.

`String` interpolation and concatenation. (Examples with explanation)

#### Operators and Expressions

When you need to compare `Strings` then they are only able to be compared in two ways, they are either equal to each other or not.

| Operator | Description |
| :--- | :--- |
| `LHS == RHS` | True when Left Hand Side (LHS) is the same as the Right Hand Side (RHS) |
| `LHS != RHS` | True when LHS is **NOT** the same as RHS |


> #### Warning ⚠️
>
> `String` type values cannot contain 2 or more instances of `$$` as these are reserved characters used behind the scenes to denote variables and datachips.


### Number

The `Number` type can represent any sort of number, whether it is an integer, a negative number or decimal number. Behind the scenes, the value is always stored as a decimal number, even if that means specifying an additional `.0` on the value. By storing all number values consistently behind the scenes it means they can all be treated in the exact same way and you don't have to worry about conversion between different number types like you might have to do when coding.

A `Number` type allows for the following range:
- Max: 1.7976931348623157E+308
- Min: -1.7976931348623157E+308

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



## Collections
- List
- Coordinates
- Bounding Box
- Grid
- JSON
- Table

## Casting and Converting

- Rules
- Matrix of Types vs Types
