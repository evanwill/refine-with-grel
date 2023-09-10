---
section: Controls
nav_order: 3
title: Iteration (Loops)
nav: Iteration
---

GREL provides several controls for iterating through an array to apply an expression to each individual member. 
This allows you to break up a string into an array, loop through the parts to transform, then rejoin to create your desired output.

## forEach

The most commonly used option is forEach, which looks like:

`forEach(expressionArray, v, expression)`

The first argument is an expression that creates an array. 
The second argument is a variable name to be used represent each array value in the next expression (this can be anything!).
The third is an expression to apply to each individual array value in sequence.
The output will be another array.

`forEachIndex(expressionArray, i, v, expression)` works in the same way, but adds the `i` which will be the index number for the individual item in the array as you loop through. 

## forRange

Rather than iterating over an array, forRange steps through a series of numbers set by you, binding each step to a variable which is used in an expression.
The results are output in a new array.

`forRange(numberFrom, numberTo, numberStep, v, expression)` 

For example, `forRange(1, 10, 2, v, v)` would create the array [  1, 3, 5, 7, 9 ]. 

## With

The control `with(expressionArray, a, expression)` 
is a method to create an array, then bind it to a variable which can then be used in another expression. 

In some cases this may be a cleaner way of setting up a complex expression. 
The basic pattern would look like 
`with(value.split(";"), a, forEach(a, v, v.trim())).join(";")`.

## Examples

- Iterate through multi-valued cell to clean up: `forEach(value.split(";"), v, v.trim()).join(";")`
- Iterate through data using index
    - Merge all columns in a row into a single cell: `forEach(row.columnNames, c, cells[c].value).join("|")`
    - Merge the first three columns: `forEach(row.columnNames[0,3], c, cells[c].value).join("|")`
    - Merge a set of columns: `forEach("colname1|colname2|colname3".split("|"), c, if(isBlank(cells[c]), "none", cells[c].value)).join("|")`
- Iterate in a Json array to retrieve multiple keys: `forEach(value.parseJson().items,v,v.city[0] + v.county[0]).join("|")`
