---
section: Functions
nav_order: 2
title: String Functions
nav: Strings
---

what are string values?

trim()

slice()
substring()

toLowercase()
toTitlecase()
toUppercase()

replace()

replaceChars()
- "Téxt thát was optícálly recógnízéd".replaceChars("áéíóú", "aeiou")
replaceEach()

tests

startsWith()
endsWith()
contains()

indexOf()
lastIndexOf()



`"row_id_" + "0000"[0,4-length(row.index +1)] + (row.index +1)`

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

titlecase on hyphenated names?
`replace(toTitlecase(replace(value,"-",".")),".","-")`


## replace

replace()

Regex in replace, use any regex notation, wrap the pattern in forward slashes. 

Ex + strings, replace string together multiple, cells. Pull in from other

Custom facet just beginning of word, or multiple columns 
