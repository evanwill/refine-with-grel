---
section_id: Functions
nav_order: 3
title: GREL Functions
nav: Introduction
---

GREL *Functions*{:.term} are written in [camelCase](https://en.wikipedia.org/wiki/Camel_case) followed by parentheses containing a list of the function's arguments (i.e. options or inputs).
They can be used in two forms:

- parentheses: `functionName(argument0, argument1, argument2, etc)` (this is as given in the documentation)
- dot notation: `argument0.functionName(argument1, argument2, etc)` (this is more commonly used in practice)

The arguments in a function could be a variable, a string (wrapped in quotes `"example"` or `'example'`), a regex (wrapped in forward slash `/regex/`), or another function.
Multiple functions can be strung together (or nested) to carry out complex operations.

For example, in this case we start with the cell's value (`value`), remove any white space on beginning or end (`trim()`), and count the number of characters (`length()`):

- parentheses: `length(trim(value))`
- dot notation: `value.trim().length()`

Generally, dot notation can make reading a series of functions applied in sequence easier.

{% include alert.html text="*Note:* white space is ignored in expressions! Use space to make your functions easier to read." color="warning" %}
