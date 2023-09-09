---
section: Functions
nav_order: 3
title: Array Functions
nav: Arrays
---

basics 

Create an array from any string by using the `split(value, expression)` function. 
The expression is the character or pattern you want to split the string up on, often a new line or a deliminator in a list. 

For example, split on semi-colon `value.split(";")` (a classic multi-valued cell list), split on spaces `value.split(" ")` (basic word array), or split on a new line `value.split(/\n/)` (lines of a text).

Once the cell is an array, it can be rearranged and sliced in many ways with [array functions](https://openrefine.org/docs/manual/grelfunctions#array-functions).
Finally, reconstitute the string by using `join()` on the array (usually using the same deliminator that you used to split!). 


split()
splitByLengths(s, n1, n2, ...) (if there isn't a character separator, but you can break it based on some pattern in number of characters)

join()

bracket notation
Remember that array objects are indexed starting at 0. 

length()

manipulate 

reverse()

sort()

slice()

uniques()

tests

inArray(a, s)
