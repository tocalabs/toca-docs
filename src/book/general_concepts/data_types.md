# A Guide to Data Types in Toca

Ever wonder what goes on behind the scenes of your Toca applications? It all comes down to **Data Types**. Think of them as the building blocks of everything you create. This guide will help you understand what types are, why they're important, and how you can use them effectively.

## What are Types?

A type is like a label for a piece of data. It tells Toca what the data is and how it should behave.

Imagine a big bowl of fruit. Before you eat a piece, you need to know what kind of fruit it is. You'd peel an orange, but you wouldn't peel a grape. Knowing the fruit's "type" tells you how to handle it. In Toca, it's the same\! The data's type tells the platform how to use and interact with it.

Every piece of data in Toca has three key parts:

1.  **The Key:** This is the name you give your data (like `customerName` or `orderTotal`). It's how you identify it.
2.  **The Type:** This is the label that tells Toca what kind of data it is (like a `String` or a `Number`).
3.  **The Value:** This is the actual data itself (like `"John Smith"` or `123.45`).

Think of it like a neatly labeled box. The **key** is the label on the outside, telling you what's in there. The **type** is a quick description of what to expect, like "documents" or "toys." And the **value** is the actual stuff inside the box.

The type is super important because it ensures your application runs smoothly and safely. For example, Toca knows that you can only do math with a `Number` and that you can't try to change the font of a `Table`. This prevents common errors and makes your applications more reliable.

Toca's types fall into two main categories:

1.  **Scalar Types:** These hold a single value (like a single piece of text or a number).
2.  **Collection Types:** These hold multiple values (like a list of names or a table of data).

Let's dive into the specifics\!

## Scalar Types

These are your fundamental building blocks, each holding a single piece of information.

### String

A `String` is simply a piece of text. It's one of the most common types you'll use. The name "string" comes from the idea of a "string of characters."

In Toca, a `String` can be anything from a single letter to a long article. It can contain any valid characters and supports special formatting like:

  * `\n` for a new line
  * `\t` for a tab
  * `\r` for a carriage return

While there's no strict limit on length, very long strings (tens of thousands of characters) might cause minor performance slowdowns.

> **Warning ⚠️**
>
> Don't use `$$` inside a `String`. Toca uses these characters behind the scenes to identify variables.

#### Converting to a String (Casting)

`Strings` are very flexible. You can convert almost any other type into a `String`, which is useful for displaying numbers as text or turning a `List` into a comma-separated sentence.

#### Operators

You can only compare `Strings` to see if they are identical.

  * `LHS == RHS`: Is the text on the left exactly the same as the text on the right?
  * `LHS != RHS`: Is the text on the left **not** the same as the text on the right?

### Number

The `Number` type is for, you guessed it, numbers\! It can handle whole numbers (`100`), negative numbers (`-50`), and decimals (`3.14`).

Toca stores all numbers in a consistent decimal format, so you don't have to worry about converting between different number types—it just works\!

`Numbers` have a huge range, from approximately `-1.79 x 10^308` to `1.79 x 10^308`, with a precision of about 15-17 digits.

You can use scientific notation in some places. For example, `2E10` will be understood as `20,000,000,000`.

#### Converting to a Number (Casting)

When you convert a `Number` to a `String`, Toca is smart about it:

  * `4.5` becomes `"4.5"`
  * `4.0` becomes `"4"` (Toca removes the unnecessary `.0`)

#### Operators

`Number` values are perfect for mathematical equations and comparisons.

  * `LHS == RHS`: Is the left number equal to the right number?
  * `LHS != RHS`: Is the left number **not** equal to the right number?
  * `LHS > RHS`: Is the left number greater than the right number?
  * `LHS >= RHS`: Is the left number greater than or equal to the right number?
  * `LHS < RHS`: Is the left number less than the right number?
  * `LHS <= RHS`: Is the left number less than or equal to the right number?

### Boolean

A `Boolean` can only hold one of two values: `true` or `false`. This type is ideal for switches and conditions, like "Is the light on?" or "Is the user logged in?"

`Boolean` values are often used to control the flow of your application. For example: "If `{boolean}` is `true`, then run these actions."

#### Operators

  * `LHS == RHS`: Are both values the same (`true` and `true`, or `false` and `false`)?
  * `LHS != RHS`: Are the values different?
  * `!LHS`: This gives you the opposite value. If `LHS` is `true`, `!LHS` is `false`.

### Date Time

A `DateTime` type represents a specific moment in time. Managing dates and times can be tricky due to different calendars and formats, but Toca's `DateTime` type handles all of this for you by storing a consistent, universal format.

Dates and times are stored using the international standard **ISO 8601**. This means 9 AM on September 5th, 2018 is stored as: `2018-09-05T09:00:00Z`

When you need to display a `DateTime`, you can use special automation actions or app components to format it exactly how you want. Check out the :docs-link[Format / Convert Date]{id="FormatDate" type="Action"} action for more details.

#### Converting to a Date Time (Casting)

You can only convert a `DateTime` to a `String` using specific actions. This is because Toca needs to know how you want the date and time to be formatted.

### JSON

The `JSON` type is for storing data in the JSON (JavaScript Object Notation) format. This is a great way to handle structured data, like settings or configuration.

A `JSON` type is similar to a `String` but it enforces a valid format. One of its best features is that you can use a powerful tool called **JSONPath** to easily pull out specific pieces of information.

For example, from the following data:

```json
{
  "name": "Toca",
  "industry": "Technology",
  "available_jobs": [
    {
      "title": "Application Builder"
    }
  ]
}
```

  * `$.industry` would get you `"Technology"`.
  * `$.available_jobs[0].title` would get you `"Application Builder"`.

> **Note 📝**
>
> Like Toca's `List` type, the first item in a JSON list is always at position `0`.

#### Converting to a JSON (Casting)

You can easily convert between a `JSON` and a `String`. You can also extract individual JSON properties and convert them into a `String`, `Number`, or `Boolean` if the values are valid.

### Password

The `Password` type is for keeping sensitive information like passwords, API keys, and security tokens safe. It's a text value that's automatically encrypted and is only decrypted at the exact moment it's used.

`Password` values will never be logged or displayed, making them perfect for secure automation tasks. You'll typically use this type with the :docs-link[Paste Password]{id="PastePassword" type="Action"} action in desktop automation.

### File

The `File` type represents any kind of file within the Toca platform, from a PDF to a spreadsheet. It's useful for handling file uploads, downloads, and transfers between different parts of your application and bots.

The `File` type stores important information about the file, such as its name, size, and type.

> **Note 📝**
>
> A `File` type is **not** the same as a file path on a bot's computer. It's a special type for moving files around the Toca platform.

### Image

The `Image` type is for storing images (like PNGs, JPEGs, etc.) in a universal format. You can use `Image` values in automation actions like "Image Search" or display them in an app.

Behind the scenes, images are stored as a **Data URI**, which is a special text representation of the image data.

#### Converting to an Image (Casting)

For advanced uses, you can cast an `Image` to a `String` to get its raw Data URI. Be careful with this, as it's no longer a usable `Image` type afterward.

### Identity

An `Identity` represents a link to an external account, like a Microsoft, Google, or GitHub account. This is a special type used to securely authorize automation actions.

For example, an `Identity` allows you to send an email via Outlook or upload a file to Google Drive on behalf of a user without needing them to log in every time. Because of its specific purpose, the `Identity` type can only be used with these kinds of actions.

## Collection Types

These types are designed to store multiple values in a structured way.

### List

A `List` is an ordered collection of values. It's like a shopping list—the items stay in the order you put them in. A `List` can contain any number of items (even duplicates\!) and can even hold values of different types.

For example:

```python
my_list = ["james", 28, False, "Toca.io"]
```

You can get an item from a `List` by its position, called its "index." You can also go through each item one by one.

> **Note 📝**
>
> Toca lists start counting at `0`. So, the first item is at position `0`, and the last item is at position `list length - 1`.

#### Converting to a List (Casting)

You can't convert a whole `List` to another type directly, but you can use actions to combine its items into a single `String`. You can also convert a table row or column into a `List`.

### Coordinates

A `Coordinates` type holds two `Number` values: an `X` position and a `Y` position. This is commonly used in desktop automation to specify a single point on a screen.

The `(0, 0)` coordinate is the top-left corner of the screen.

Behind the scenes, a coordinate might look like this:

```javascript
{
  X: 50,
  Y: 125
}
```

You can access the individual `X` and `Y` values to get their `Number` components.

### Bounding Box

A `Bounding Box` defines a rectangle on the screen. It's made up of four `Number` values: `X` and `Y` for the top-left corner, and a `Width` and `Height`.

This type is often used in desktop automation to specify an area of the screen, like a window or a button.

A bounding box is represented like this:

```javascript
{
  X: 50,
  Y: 125,
  Width: 100,
  Height: 200
}
```

You can access the individual `X`, `Y`, `Width`, and `Height` values if you need them.

> **Note 📝**
>
> A `Bounding Box` can only represent a perfect rectangle. It can't be used for more complex shapes.

### Grid

A `Grid` is a collection of `Bounding Box` types, arranged in a grid pattern. It's used in specific automation actions to define a series of areas on the screen that a bot needs to interact with.

When a bot processes a `Grid`, it moves from the top-left box to the top-right, and then down to the next row, and so on.

Because of its complexity, you can't access the individual boxes within a `Grid` directly.

### Table

A `Table` is a powerful, two-dimensional type that stores data in columns and rows, much like a spreadsheet. Each column can have its own type, making tables perfect for storing any kind of structured data.

Tables are so important they have their own dedicated documentation :docs-link[here]{id="projects/automation/datastores/tables"}.

Some key features of tables include:

  * Searching and filtering data.
  * Default and auto-generated values.
  * Creating relationships with other tables.
  * Setting permissions for specific rows.

Here’s an example:

| *id* | Name | Age | Fellowship Member |
|:-- | :---: | :---: | :---: |
| 1 | Legolas | 2931 | ✅ |
| 2 | Aragorn | 87 | ✅ |
| 3 | Frodo | 33 | ✅ |

> **Note 📝**
>
> Every table row must have a unique ID, typically in a special format called a `UUID`. This ensures every row can be uniquely identified.

Tables are stored in a database, so they can handle thousands of rows with excellent performance.

> **Warning ⚠️**
>
> While tables can be huge, moving very large amounts of data can slow things down. To keep your apps fast, only retrieve the data you absolutely need, and use pagination in apps to load data in smaller chunks.

#### Converting to a Table (Casting)

You can't convert an entire table to another type, but you can convert a single row or column into a `List`. You can also access individual cells and cast them to their specific type (like `String` or `Number`). For special types like `UUID` or `Time`, you can always convert them to a `String`.

## Conversion Chart (Casting Matrix)

This chart shows which types can be easily converted into others. Some types, like `Identity`, are left out because they can't be converted.

| Type | String | Number | Boolean | DateTime | JSON | Image | List | Coordinates | Bounding Box | Table |
|:---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| **String** | - | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | | | ✅\*|
| **Number** | ✅ | - | | | ✅\* | | | ✅\* | ✅\* | ✅\*|
| **Boolean** | | | - | | ✅\*| | | | | ✅\*|
| **DateTime** | ✅ | | | - | ✅\* | | | | | ✅\*|
| **JSON** | ✅ | | | | - | | | | | ✅\*|
| **Image** | | | | | | - | | | | ✅\*|
| **List** | ✅ | | | | ✅ | | - | | | ✅\*|
| **Coordinates** | | | | | | | | - | | |
| **Bounding Box** | | | | | | | | | - | |
| **Table** | | | | | | | ✅| | | - |

\* An asterisk means you can convert the type, but you'll need to use special "subchips" to do it. You can learn more about subchips {here}.
