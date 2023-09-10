---
section: Examples 
nav_order: 3
title: Regular Expressions
---

Regular expressions (regex) are a syntax to write match patterns to search in strings.
You can use regex patterns in many areas of Refine.
Wrap the regex pattern in forward slashes `/`.

[Regexr](https://regexr.com/) is a good site for learning about regex and testing your patterns. 
Refine's regex is based in Java, so you can check the [Java regular expression tutorial](https://docs.oracle.com/javase/tutorial/essential/regex/) details.

## Find and Match 

The functions `find(s, p)` (creates array of substrings that match the pattern) and `match(s, p)` (creates array of all capturing groups found by the pattern) are designed specifically for handling regex pattern matching.
Here are some examples to compare different uses of the regex:

| `value` | "The dogs" | "Theology" | "Cat food" |
| `value.replace(/^The /,"")` | "dogs" | "Theology" | "Cat food" |
| `value.match("^(The )?(.*)")` | [ "The ", "dogs" ] | [ null, "Theology" ] | [ null, "Cat food" ] |
| `value.find(/^T\w*/)` | [ "The" ] | [ "Theology" ] | [ ] |
{:.table .table-bordered}

Note that match takes the regex pattern in quotes, unlike other uses where it is wrapped in forward slashes.

## Examples 

- In regex `^` is start of string and `$` means end of string.
    - Remove "The " from front of string: `value.replace(/^The /,"")`
    - Remove trailing period, "." at end of string: `value.replace(/\.$/,"")` (note the "." needs to be escaped with `\` since it has a meaning in regex)
- Classes of characters
    - Remove all punctuation marks: `value.replace(/\p{Punct}/,' ')`
    - Remove all letters: `value.replace(/\p{IsAlphabetic}/,"")`
