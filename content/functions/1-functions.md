---
section_id: Functions
nav_order: 3
title: GREL Functions
#nav: Introduction
---

GREL *Functions*{:.term} are written in [camelCase](https://en.wikipedia.org/wiki/Camel_case) followed by parentheses containing a list of the function's arguments (i.e. options or inputs).
They can be used in two forms:

- Parentheses: `functionName(argument0, argument1, argument2, etc)` -- this is as given in the documentation.
- Dot notation: `argument0.functionName(argument1, argument2, etc)` -- this is more commonly used in practice.

The *arguments*{:.term} in a function could be a variable, a string (wrapped in quotes `"example"` or `'example'`), a regex (wrapped in forward slash `/regex/`), another function, or nothing at all.

Multiple functions can be strung together or nested to carry out complex operations.

{% include alert.html text="**Readability:** Generally, dot notation can make reading a series of functions applied in sequence easier. White space is ignored in expressions, so use space to make your functions easier to read." color="warning" %}

## Examples

Starting with the cell's value, remove any white space on beginning or end, then count the number of characters:

- Parentheses: `length(trim(value))`
- Dot notation: `value.trim().length()`

Starting with the cell's value, replace "example" with "test", then remove all punctuation marks:

- Parentheses: `replace(replace(value,'example','test'),/\p{Punct}/,' ')`
- Dot notation: `value.replace('example','test').replace(/\p{Punct}/,' ')`
