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

## Examples 

- In regex `^` is start of string and `$` means end of string.
    - Remove "T" from front of string: `value.replace(/^T/,"")`
    - Remove trailing period, "." at end of string: `value.replace(/\.$/,"")` (note the "." needs to be escaped with `\` since it has a meaning in regex)
- Classes of characters
    - Remove all punctuation marks: `value.replace(/\p{Punct}/,' ')`
    - Remove all letters: `value.replace(/\p{IsAlphabetic}/,"")`
