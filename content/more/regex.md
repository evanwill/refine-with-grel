---
section: Examples 
nav_order: 3
title: Regular Expressions
---


Regex in replace, use any regex notation, wrap the pattern in forward slashes. 

https://regexr.com/

Remove leading or trailing character

In regex `^` is start of string and `$` means end of string, which can be used in a `replace` statement.

Remove "T" from front of string:

`value.replace(/^T/,"")`

Remove trailing period, "." at end of string:
 
`value.replace(/\.$/,"")`

(note the "." needs to be escaped with `\` since it has a meaning in regex)

classes of characters
`value.replace(/\p{Punct}/,' ')`
`\p{IsAlphabetic}`
