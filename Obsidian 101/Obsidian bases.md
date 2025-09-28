Bases is a [core plugin](https://help.obsidian.md/plugins) that lets you create database-like views of your notes. Using a base you can view, edit, sort, and filter files and their [properties](https://help.obsidian.md/properties). Bases can help you organize everything from projects to travel plans, reading lists, and more.

Each base can have several [views](https://help.obsidian.md/bases/views) with different layouts such as tables and cards. Below is an example of table view where each row is a file, and each column is a property of that file.

![Example of a base showing a table view with a list of books](https://publish-01.obsidian.md/access/f786db9fac45774fa4f0d8112e232d67/Attachments/bases-noshadow.png)

All the data in Obsidian Bases is stored in your local [Markdown](https://help.obsidian.md/syntax) files and their [properties](https://help.obsidian.md/properties). The views are described by the [Bases syntax](https://help.obsidian.md/bases/syntax), which can be saved as a `.base` file or [embedded](https://help.obsidian.md/bases/create-base#Embed%20a%20base) in code blocks within your Markdown files.

# Create a base
### Embed a base file

You can embed base files in [any other file](https://help.obsidian.md/embeds) using the `![[File.base]]` syntax. To specify the default view use `![[File.base#View]]`.

### Embed a base as a code block

Bases can also embedded directly into a note using a `base` code block and the [bases syntax](https://help.obsidian.md/bases/syntax).

```
\`\`\`base
filters:
  and:
    - file.hasTag("example")
views:
  - type: table
    name: Table
\`\`\`
```

# Views
Views allow you to organize the information in a [Base](https://help.obsidian.md/bases) in multiple different ways. A base can contain several views, and each view can have a unique configuration to display, sort, and filter files.

For example, you may want to create a base called "Books" that has separate views for "Reading list" and "Recently finished". The first view in your list of views will load by default. You can drag views by their icon to change their order.

## Layout

Currently, bases can be displayed as a **table** or **cards**. In the future more layout types will be added. See [roadmap](https://obsidian.md/roadmap/).

**Cards layout** displays each file as a card in a grid. The view settings allow you to optionally configure an image property, which can be an image URL or [attachment](https://help.obsidian.md/attachments) link.

Each layout type provides its own configuration options and actions. To see a view's configuration options:

Click the view name in the top left of the bases toolbar.

Click the right arrow next to the current view.

Choose **Configure view**.

Table

Row height

If you want to display more information per row, you can change the row height in the view settings. Choose between short, medium, tall, and extra tall.

Cards

Image property

Cards support an optional cover image, which is [property](https://help.obsidian.md/properties) that's displayed as an image at the top of the card. The property can be any of the following:

A link to a local attachment `"[[link/to/attachment.jpg]]"`

An external link (URL)

A hex color code (`#000000`)

Image fit

If you have an image property configured, this option will determine how the image should be displayed in the card.

**Cover:** The image fills the card's content box. If it does not fit, the image will be cropped.

**Contain:** The image is scaled until it fits within the card's content box. The image will not be cropped.

Image aspect ratio

The size of the cover image is determined based on its aspect ratio. The default aspect ratio is 1:1 meaning all your images will be square. Adjust this option to make the image wider or taller.

Filters

A base without filters shows all the files in your vault. Filters allow you to narrow down results to only show files that meet specific criteria. For example, you can use filters to only display files with a specific [tag](https://help.obsidian.md/tags) or within a specific folder. Many filter types are available.

Click the **Filters** button at the top of a base to add filters.

Filters can be applied to all views in a base, or just a single view by choosing from the two sections in the **Filters** menu.

**All views** applies filters to all views in the base.

**This view** applies filters to the active view.

Properties, operators, values

Filters have three components:

**Property** — lets you choose a [property](https://help.obsidian.md/properties) in your vault, including [file properties](https://help.obsidian.md/bases/syntax#File%20properties).

**Operator** — lets you choose how to compare the conditions. The list of available operators depends on the property type (text, date, number, etc)

**Value** — lets you choose the value you are comparing to. Values can include math and [functions](https://help.obsidian.md/bases/functions).

Conjunctions

**All the following are true** is an `and` statement — results will only be shown if *all* conditions in the filter group are met.

**Any of the following are true** is an `or` statement — results will be shown if *any* of the conditions in the filter group are met.

**None of the following are true** is a `not` statement — results will not be shown if *any* of the conditions in the filter group are met.

Filter groups

Filter groups allow you to create more complex logic by creating combinations on conjunctions.

Advanced filter editor

Click the code button ![lucide-code-xml.svg > icon](https://publish-01.obsidian.md/access/f786db9fac45774fa4f0d8112e232d67/Attachments/icons/lucide-code-xml.svg) to use the **advanced filter** editor. This displays the raw [syntax](https://help.obsidian.md/bases/syntax) for the filter, and can be used with more complex [functions](https://help.obsidian.md/bases/functions) that cannot be displayed using the point-and-click interface.

Limit, copy, and export results

The *results* menu shows the number of results in view. Click the results button to limit the number of results, and access additional actions.

Copy to clipboard

This action copies the view to your clipboard. Once in your clipboard you can paste it into a Markdown file, or into other document apps including spreadsheets like Google Sheets, Excel, and Numbers.

Export CSV

This action saves a CSV of your current view.

# Functions
Functions

Functions are used in [Bases](https://help.obsidian.md/bases) to manipulate data from [Properties](https://help.obsidian.md/properties) in filters and formulas. See the [bases syntax](https://help.obsidian.md/bases/syntax) reference to learn more about how you can use functions.

Aside from [Global](https://help.obsidian.md/bases/functions#Global) functions, most functions depend on the type of value you want to modify:

Any

Date

String

Number

List

Link

File

Object

Regular expression

Global

Global functions are used without a type.

`date()`

date(date: string): date

`date(string): date` parses the provided string and returns a date object.

The `date` string should be in the format `YYYY-MM-DD HH:mm:ss`.

`file()`

file(path: string | file | url): file

Returns a file object for the given file or path.

Example: `file(link("[[filename]]"))` or `file("path to file")`.

`if()`

if(condition: any, trueResult: any, falseResult?: any): any

`condition` is the condition to be evaluated.

`trueResult` is the output if condition is true.

`falseResult` is the optional output if the condition is false. If it is not given, then it is assumed to be `null`.

Returns the `trueResult` if `condition` is true, or is a truthy value, or `falseResult` otherwise.

Example: `if(isModified, "Modified", "Unmodified")`

`image()`

image(path: string | file | url): image

Returns an image object which will render the image in the view.

Example: `image(image-property)` or `image("https://obsidian.md/images/obsidian-logo-gradient.svg")`

`icon()`

icon(name: string): icon

Returns a value that will render as an icon in a view. The icon name must match a supported Lucide icon.

Example: `icon("arrow-right")`.

`max()`

max(value1: number, value2: number...): number

Returns the largest of all the provided numbers.

`min()`

min(value1: number, value2: number...): number

Returns the smallest of all the provided numbers.

`link()`

link(path: string | file, display?: value): Link

Parses a string `path` and returns a Link object that renders as a link to the path given.

Optionally provide the `display` parameter to change what text the link says.

`list()`

list(element: any): List

If the provided element is a list, return it unmodified.

Otherwise, wraps the provided `element` in a list, creating a list with a single element.

This function can be helpful when a property contains a mixture of strings or lists across the vault.

Example: `list("value")` returns `["value"]`.

`now()`

now(): date

`now()` returns a date object representing the current moment.

`number()`

number(input: any): number

Attempt to return the provided value as a number.

Date objects will be returned as milliseconds since the unix epoch.

Booleans will return a 1 or 0.

Strings will be parsed into a number and return an error if the result is invalid.

Example, `number("3.4")` returns `3.4`.

`duration()`

duration(value: string): duration

Parse a string as a duration. See the [date arithmetic section](https://help.obsidian.md/bases/syntax#Date%20arithmetic) for the `value` string format.

Durations do not need to be explicitly parsed when performing date arithmetic (for example, `now() + '1d'`), but the do when performing arithmetic on durations (for example, `now() + (duration('1d') * 2)`).

When performing arithmetic on durations with scalars, the duration must be on the left. For example `duration('5h') * 2`, instead of `2 * duration('5h')`.

`today()`

today(): date

`today()` returns a date object representing the current date. The time portion is set to zero.

`date()`

date(input: string | date): date

Returns a date object representing the parsed input timestamp or date object.

Any

Functions you can use with any value. This includes strings (e.g. `"hello"`), numbers (e.g. `42`), lists (e.g. `[1,2,3]`), objects, and more.

`toString()`

any.toString(): string

Returns the string representation of any value.

Example: `123.toString()` returns `"123"`.

`isTruthy()`

any.isTruthy(): boolean

Return the value coerced into a boolean.

Example: `1.isTruthy()` returns `true`.

Date

Functions you can use with a date and time such as `date("2025-05-27")`. Date comparisons can be done using [date arithmetic](https://help.obsidian.md/bases/syntax#Date%20arithmetic).

Fields

The following fields are available for dates:

Field Type Description `date.year` `number` The year of the date `date.month` `number` The month of the date (1–12) `date.day` `number` The day of the month `date.hour` `number` The hour (0–23) `date.minute` `number` The minute (0–59) `date.second` `number` The second (0–59) `date.millisecond` `number` The millisecond (0–999)

`date()`

date.date(): date

Returns a date object with the time removed.

Example: `now().date().format("YYYY-MM-DD HH:mm:ss"` returns a string such as "2025-12-31 00:00:00"

`format()`

date.format(format: string): string

`format` is the format string (e.g., `"YYYY-MM-DD"`).

Returns the date formatted as specified by a Moment.js format string.

Example: `date.format("YYYY-MM-DD")` returns `"2025-05-27"`.

`time()`

date.time(): string

Returns the time.

Example: `now().time()` returns a string such as "23:59:59"

`relative()`

date.relative(): string

Returns a readable comparison of the date to the current datetime.

Example: `file.mtime.relative()` returns a value such as `3 days ago`.

`isEmpty()`

date.isEmpty(): boolean

Returns false.

String

Functions you can use with a sequence of characters such as `"hello".`

Fields

Field Type Description `string.length` `number` The number of characters in the string

`contains()`

string.contains(value: string): boolean

`value` is the substring to search for.

Returns true if the string contains `value`.

Example: `"hello".contains("ell")` returns `true`.

`containsAll()`

string.containsAll(...values: string): boolean

`values` are one or more substrings to search for.

Returns true if the string contains all of the `values`.

Example: `"hello".containsAll("h", "e")` returns `true`.

`containsAny()`

string.containsAny(...values: string): boolean

`values` are one or more substrings to search for.

Returns true if the string contains at least one of the `values`.

Example: `"hello".containsAny("x", "y", "e")` returns `true`.

`endsWith()`

string.endsWith(query: string): boolean

`query` is the string to check at the end.

Returns true if this string ends with `query`.

Example: `"hello".endsWith("lo")` returns `true`.

`isEmpty()`

string.isEmpty(): boolean

Returns true if the string has no characters, or is not present.

Example: `"Hello world".isEmpty()` returns `false`.

Example: `"".isEmpty()` returns `true`.

`replace()`

string.replace(pattern: string | Regexp, replacement: string): string

`pattern` is the value to search for in the target string.

`replacement` is the value to replace found patterns with.

If `pattern` is a string, all occurrences of the pattern will be replaced.

If `pattern` is a Regexp, the `g` flag determines if only the first or if all occurrences are replaced.

Example: `"a,b,c,d".replace(/,/, "-")` returns `"a-b,c,d"`, where as `"a,b,c,d".replace(/,/g, "-")` returns `"a-b-c-d"`.

`lower()`

string.lower(): string

Returns the string converted to lower case.

`reverse()`

string.reverse(): string

Reverses the string.

Example: `"hello".reverse()` returns `"olleh"`.

`slice()`

string.slice(start: number, end?: number): string

`start` is the inclusive start index.

`end` is the optional exclusive end index.

Returns a substring from `start` (inclusive) to `end` (exclusive).

Example: `"hello".slice(1, 4)` returns `"ell"`.

If `end` is omitted, slices to the end of the string.

`split()`

string.split(separator: string | Regexp, n?: number): list

`separator` is the delimiter for splitting the string.

`n` is an optional number. If provided, the result will have the first `n` elements.

Returns an list of substrings.

Example: `"a,b,c,d".split(",", 3)` or `"a,b,c,d".split(/,/, 3)` returns `["a", "b", "c"]`.

`startsWith()`

string.startsWith(query: string): boolean

`query` is the string to check at the beginning.

Returns true if this string starts with `query`.

Example: `"hello".startsWith("he")` returns `true`.

`title()`

string.title(): string

Converts the string to title case (first letter of each word capitalized).

Example: `"hello world".title()` returns `"Hello World"`.

`trim()`

string.trim(): string

Removes whitespace from both ends of the string.

Example: `"  hi  ".trim()` returns `"hi"`.

Number

Functions you can use with numeric values such as `42`, `3.14`.

`abs()`

number.abs(): number

Returns the absolute value of the number.

Example: `(-5).abs()` returns `5`.

`ceil()`

number.ceil(): number

Rounds the number up to the nearest integer.

Example: `(2.1).ceil()` returns `3`.

`floor()`

number.floor(): number

Rounds the number down to the nearest integer.

Example: `(2.9).floor()` returns `2`.

`round()`

number.round(digits: number): number

Rounds the number to the nearest integer.

Optionally, provided a `digits` parameter to round to that number of decimal digits.

Example: `(2.5).round()` returns `3`, and `(2.3333).round(2)` returns `2.33`.

`toFixed()`

number.toFixed(precision: number): string

`precision` is the number of decimal places.

Returns a string with the number in fixed-point notation.

Example: `(3.14159).toFixed(2)` returns `"3.14"`.

`isEmpty()`

number.isEmpty(): boolean

Returns true if the number is not present.

Example: `5.isEmpty()` returns `false`.

List

Functions you can use with an ordered list of elements such as `[1, 2, 3]`.

Fields

Field Type Description `list.length` `number` The number of elements in the list

`contains()`

list.contains(value: any): boolean

`value` is the element to search for.

Returns true if the list contains `value`.

Example: `[1,2,3].contains(2)` returns `true`.

`containsAll()`

list.containsAll(...values: any): boolean

`values` are one or more elements to search for.

Returns true if the list contains all of the `values`.

Example: `[1,2,3].containsAll(2,3)` returns `true`.

`containsAny()`

list.containsAny(...values: any): boolean

`values` are one or more elements to search for.

Returns true if the list contains at least one of the `values`.

Example: `[1,2,3].containsAny(3,4)` returns `true`.

`isEmpty()`

list.isEmpty(): boolean

Returns true if the list has no elements.

Example: `[1,2,3].isEmpty()` returns `false`.

`join()`

list.join(separator: string): string

`separator` is the string to insert between elements.

Joins all list elements into a single string.

Example: `[1,2,3].join(",")` returns `"1,2,3"`.

`reverse()`

list.reverse(): list

Reverses the list in place.

Example: `[1,2,3].reverse()` returns `[3,2,1]`.

`sort()`

list.sort(): list

Sorts list elements from smallest to largest.

Example: `[3, 1, 2].sort()` returns `[1, 2, 3]`.

Example: `["c", "a", "b"].sort()` returns `["a", "b", "c"]`.

`flat()`

list.flat(): list

Flattens nested list into a single list.

Example: `[1,[2,3]].flat()` returns `[1,2,3]`.

`unique()`

list.unique(): list

Removes duplicate elements.

Example: `[1,2,2,3].unique()` returns `[1,2,3]`.

`slice()`

list.slice(start: number, end?: number): list

`start` is the inclusive start index.

`end` is the optional exclusive end index.

Returns a shallow copy of a portion of the list from `start` (inclusive) to `end` (exclusive).

Example: `[1,2,3,4].slice(1,3)` returns `[2,3]`.

If `end` is omitted, slices to the end of the list.

`map()`

list.map(value: Any): list

Transform each element of this list by calling a conversion function, which uses the variables `index` and `value`, and returns the new value to be placed in the list.

`value` is the value of an item in the list.

`index` is the index of the current value.

Example: `[1,2,3,4].map(value + 1)` returns `[2,3,4,5]`.

`filter()`

list.filter(value: Boolean): list

Filter the elements of this list by calling a filter function, which uses the variables `index` and `value`, and returns a boolean value for whether the element should be kept.

`value` is the value of an item in the list.

`index` is the index of the current value.

Example: `[1,2,3,4].filter(value > 2)` returns `[3,4]`.

permalink: bases/functions

Link

`linksTo()`

link.linksTo(file): boolean

Returns whether the file represented by the `link` has a link to `file`.

`asFile()`

link.asFile(): file

Returns a file object if the link refers to a valid local file.

Example: `link("[[filename]]").asFile()`

File

Functions you can use with file in the vault.

`asLink()`

file.asLink(display?: string): Link

`display` optional display text for the link.

Returns a Link object that renders as a functioning link.

Example: `file.asLink()`

`hasLink()`

file.hasLink(otherFile: file | string): boolean

`otherFile` is another file object or string path to check.

Returns true if `file` links to `otherFile`.

Example: `file.hasLink(otherFile)` returns `true` if there’s a link from `file` to `otherFile`.

`hasProperty()`

file.hasProperty(name: string): boolean

Returns true if the note has the given file property.

`hasTag()`

file.hasTag(...values: string): boolean

`values` are one or more tag names.

Returns true if the file has any of the tags in `values`.

Example: `file.hasTag("tag1", "tag2")` returns `true` if the file has either tag.

`inFolder()`

file.inFolder(folder: string): boolean

`folder` is the folder name to check.

Returns true if the file is in the specified folder.

Example: `file.inFolder("notes")` returns `true`.

Object

Functions you can use with a collection of key-value pairs such as `{"a": 1, "b": 2}`.

`isEmpty()`

object.isEmpty(): boolean

Returns true if the object has no own properties.

Example: `{}.isEmpty()` returns `true`.

`keys()`

object.keys(): list

Returns a list containing the keys of the object.

`values()`

object.values(): list

Returns a list containing the values of the object.

Regular expression

Functions you can use with a regular expression pattern. Example: `/abc/`.

`matches()`

regexp.matches(value: string): boolean

`value` is the string to test.

Returns true if the regular expression matches `value`.

# Bases syntax
Bases syntax

When you [create a base](https://help.obsidian.md/bases/create-base) in Obsidian, it is saved as a `.base` file. Bases are typically edited using the app interface, but the syntax can also be edited manually, and embedded in a code block.

The [Bases](https://help.obsidian.md/bases) syntax defines [views](https://help.obsidian.md/bases/views), filters, and formulas. Bases must be valid YAML conforming to the schema defined below.

Example

Here's an example of a base file. We'll walk through each section in detail.

filters: or: \- file.hasTag("tag") \- and: \- file.hasTag("book") \- file.hasLink("Textbook") \- not: \- file.hasTag("book") \- file.inFolder("Required Reading") formulas: formatted\_price: 'if(price, price.toFixed(2) + " dollars")' ppu: "(price / age).toFixed(2)" properties: status: displayName: Status formula.formatted\_price: displayName: "Price" file.ext: displayName: Extension views: \- type: table name: "My table" limit: 10 filters: and: \- 'status != "done"' \- or: \- "formula.ppu > 5" \- "price > 2.1" order: \- file.name \- file.ext \- note.age \- formula.ppu \- formula.formatted\_price

Filters

By default a base includes every file in the vault. There is no `from` or `source` like in SQL or Dataview. The `filters` section lets you define conditions to narrow down the dataset.

filters: or: \- file.hasTag("tag") \- and: \- file.hasTag("book") \- file.hasLink("Textbook") \- not: \- file.hasTag("book") \- file.inFolder("Required Reading")

There are two opportunities to apply filters:

At the global `filters` level (shown above) where they apply to all views in the base.

At the `view` level where apply only to a specific view.

These two sections are functionally equivalent and when evaluating for a view they will be concatenated with an `AND`.

The `filters` section contains either a single filter statement as a string, or a recursively defined filter object. Filter objects may contain one of `and`, `or`, or `not`. These keys are a heterogeneous list of other filter objects or filter statements in strings. A filter statement is a line which evaluates to truthy or falsey when applied to a note. It can be one of the following:

A basic comparison using standard arithmetic operators.

A function. A variety of [functions](https://help.obsidian.md/bases/functions) are built-in, and plugins can add additional functions.

The syntax and available functions for filters and formulas are the same.

Formulas

The `formulas` section defines formula properties that can be displayed across all views in the base file.

formulas: formatted\_price: 'if(price, price.toFixed(2) + " dollars")' ppu: "(price / age).toFixed(2)"

Formula properties support basic arithmetic operators and a variety of built-in [functions](https://help.obsidian.md/bases/functions). In the future, plugins will be able to add functions for use in formulas.

You can reference properties in different ways depending on their type:

**Note properties** are properties defined in the note’s frontmatter. For example `note.price` or `note["price"]`.  
If no prefix is specified, the property is assumed to be a `note` property.  

**File properties** describe the file itself.  
For example `file.size` or `file.ext`. You can also reference the file object directly, e.g., `file.hasLink()`.  

**Formula properties** are other formulas in the base.  
Example `formula.formatted_price`.  

A formula can use values from other formula properties, as long as there’s no circular reference.

Formula properties are always stored as strings in YAML, but their actual **output data type** is determined by the type of the underlying data and the return value of any functions used.

Note the use of nested quotes is necessary to include text literals in the YAML field. Text literals must be enclosed in single or double quotes.

Properties

The `properties` section allows storing configuration information about each property. It is up to the individual view how to use these configuration values. For example, in tables the display name is used for the column headers.

properties: status: displayName: Status formula.formatted\_price: displayName: "Price" file.ext: displayName: Extension

Display names are not used in filters or formulas.

Views

The `views` section defines how the data can be rendered. Each entry in the `views` list defines a separate view of the same data, and there can be as many different views as needed.

views: \- type: table name: "My table" limit: 10 filters: and: \- 'status != "done"' \- or: \- "formula.ppu > 5" \- "price > 2.1" order: \- file.name \- file.ext \- note.age \- formula.ppu \- formula.formatted\_price

`type` selects from the built-in and plugin-added view types.

`name` is the display name, and can be used to define the default view.

`filters` are exactly the same as described above, but apply only to the view.

[Views](https://help.obsidian.md/bases/views) can add additional data to store any information needed to maintain state or properly render, however plugin authors should take care to not use keys already in use by the core Bases plugin. As an example, a table view may use this to limit the number of rows or to select which column is used to sort rows and in which direction. A different view type such as a map could use this for mapping which property in the note corresponds to the latitude and longitude and which property should be displayed as the pin title.

In the future, API will allow views to read and write these values, allowing the view to build its own interface for configuration.

Properties

There are three kinds of properties used in bases:

**Note properties**, stored in frontmatter of Markdown files.

**File properties**, accessible for all file types.

**Formula properties**, defined in the `.base` file itself (see above).

Note properties

[Note properties](https://help.obsidian.md/properties) are only available for Markdown files, and are stored in the YAML frontmatter of each note. These properties can be accessed using the format `note.author` or simply `author` as a shorthand.

File properties

File properties refer to the file currently being tested or evaluated. File properties are available for all [file types](https://help.obsidian.md/file-formats), including attachments.

For example, a filter `file.ext == "md"` will be true for all Markdown files and false otherwise.

Property Type Description `file.backlinks` List List of backlink files. Note: This property is performance heavy. When possible, reverse the lookup and use `file.links`. Does not automatically refresh results when the vault is changed. `file.ctime` Date Created time `file.embeds` List List of all embeds in the note `file.ext` String File extension `file.file` File File object, only usable in specific functions `file.folder` String Path of the file folder `file.links` List List of all internal links in the note, including frontmatter `file.mtime` Date Modified time `file.name` String File name `file.path` String Path of the file `file.properties` Object All properties on the file. Note: Does not automatically refresh results when the vault is changed. `file.size` Number File size `file.tags` List List of all tags in the file content and frontmatter

Access properties of the current file

Embedded bases can use `this` to access properties of the current file. For example, `this.file.name` will resolve to the name of the file which has embedded the base, instead of the file being evaluated.

In a sidebar, `this` takes on the special meaning of "the currently active file". This allows you to create contextual queries based on the active file in the main content area. For example, this can be used to replicate the backlinks pane with this filter: `file.hasLink(this.file)`.

Operators

Arithmetic operators

Arithmetic operators perform arithmetic on numbers. For example, `radius * (2 * 3.14)`.

Operator Description `+` plus `-` minus `*` multiply `/` divide `%` modulo `( )` parenthesis

Date arithmetic

Dates can be modified by adding and subtracting durations. Duration units accept multiple formats:

Unit Duration `y`, `year`, `years` year `M`, `month`, `months` month `d`, `day`, `days` day `w`, `week`, `weeks` week `h`, `hour`, `hours` hour `m`, `minute`, `minutes` minute `s`, `second`, `seconds` second

To modify or offset Date objects, use the `+` or `-` operator with a duration string. For example, `date + "1M"` adds 1 month to the date, while `date - "2h"` subtracts 2 hours from the date.

The global [function](https://help.obsidian.md/bases/functions) `today()` can be used to get the current date, and `now()` can be used to get the current date with time.

`now() + "1 day"` returns a datetime exactly 24 hours from the time of execution.

`file.mtime > now() - "1 week"` returns `true` if the file was modified within the last week.

`date("2024-12-01") + "1M" + "4h" + "3m"` returns a Date object representing `2025-01-01 04:03:00`.

Subtract two dates to get the millisecond difference between the two, for example, `now() - file.ctime`.

To get the date portion of a Date with time, use `datetime.date()`.

To format a Date object, use the `format()` function, for example `datetime.format("YYYY-MM-DD")`.

Comparison operators

Comparison operators can be used to compare numbers, or Date objects. Equal and not equal can be used with any kind of value, not just numbers and dates.

Operator Description `==` equals `!=` not equal `>` greater than `<` less than `>=` greater than or equal to `<=` less than or equal to

Boolean operators

Boolean operators can be used to combine or invert logical values, resulting in a true or false value.

Operator Description `!` logical not `&&` logical and || logical or

Functions

See the [list of functions](https://help.obsidian.md/bases/functions) that can be used in formulas and [filters](https://help.obsidian.md/bases/views).

Types

Bases have a type system which is used by formulas and filters to apply functions to properties.

Strings, numbers, and booleans

Strings, numbers, and booleans are "primitive" values which do not require a function to create.

Strings are enclosed in single or double quotes, for example `"message"`.

Numbers are written as digits, and may optionally be enclosed in parenthesis for clarity. For example, `1` or `(2.5)`.

Booleans are written as `true` or `false` without quotes.

Dates and durations

Dates represent a specific date, or a date and time depending on the function used to create them, or that type that has been assigned to the [property](https://help.obsidian.md/properties).

To construct a date, use the `date` function, for example `date("2025-01-01 12:00:00")`

To modify a date, add or remove a duration, for example `now() + "1 hour"` or `today() + "7d"`

Compare dates using comparison operators (e.g. `>` or `<`) and arithmetic operators (for example, `(now() + "1d") - now()` returns `86400000` milliseconds.)

To extract portions of a date, use the available fields (`now().hour`), or a convenience function (`now.time()`).

Many other [fields and functions](https://help.obsidian.md/bases/functions) are available on date objects.

Objects and lists

Turn a single element into a list using the `list()` function. This is especially helpful for properties which may contain a mixture of lists or single values.

Access list elements using square brackets, and a 0-based index. For example, `property[0]` returns the first element from the list.

Access object elements using square brackets and the element name or dot notation. For example, `property.subprop` or `property["subprop"]`.

permalink: bases/syntax aliases: \- Bases file format

Files and links

[Wikilinks](https://help.obsidian.md/link-notes) in [frontmatter properties](https://help.obsidian.md/properties) are automatically recognized as Link objects. Links will render as a clickable link in the [view](https://help.obsidian.md/bases/views).

To construct a link, use the global `link` [function](https://help.obsidian.md/bases/functions), for example `link("filename")` or `link("https://obsidian.md")`.

You can create a link from any string, for example, `link(file.ctime.date().toString())`.

To set the display text, pass in an optional string or icon as a second parameter, for example `link("filename", "display")` or `link("filename", icon("plus"))`.

A File object can be turned into a link using `file.asLink()` with an optional display text.

Links can be compared with `==` and `!=`. They are equivalent as long as they point to the same file, or if the file does not exist when looked up, their link text must be identical.

Links can be compared to files such as `file` or `this`. They will equate if the link resolves to the file. For example, `author == this`.

Links can also be checked in list contains, for example, `authors.contains(this)`.