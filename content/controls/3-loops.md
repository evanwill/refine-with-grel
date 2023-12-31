---
section: Controls
nav_order: 3
title: Iteration (Loops)
nav: Iteration
---

GREL provides several controls for iterating through an array applying an expression to each individual member. 
This allows you to break up a string into an array, loop through the parts to transform, then rejoin to create your desired output--even more powerful processing options with arrays!

## forEach

The most commonly used option is forEach, which looks like:

`forEach(expressionArray, v, expression)`

The first argument is an expression that creates an array. 
The second argument is a variable name to be used represent each array value in the next expression (this can be anything!).
The third is an expression to apply to each individual array value in sequence.
The output will be another array.

`forEachIndex(expressionArray, i, v, expression)` works in the same way, but adds the `i` which will be the index number for the individual item in the array as you loop through. 

### Example Flowchart 

Let's visualize using this simple forEach: starting from an multi-valued cell like "one;two;three", create an array, assign each item to the variable, apply the expression, then rejoin,
`forEach(value.split(';'), v, v + ' potato').join(';')`.

{% include figure.html img="foreach.svg" alt="flowchart breaking down the parts of the express forEach(value.split(';'), v, v + ' potato').join(';')" %}

## forRange

Rather than iterating over an array, forRange steps through a series of numbers set by you, binding each step to a variable which is used in an expression.
The results are output in a new array.
The expression looks like:

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
    - Merge a set of repeating columns with numbers in the name: `forRange(1, 5, 1, r, cells["Column " + r].value).join("|")`
    - Note: most of this can be done visually using *Edit column > Join columns...*{:.ui-item}, however it may be easier to do programmatically or to use the results in further expression.
- Iterate in a Json array to retrieve multiple keys: `forEach(value.parseJson().items, v, v.city[0] + v.county[0]).join("|")`

--------

## Exercises 

{% include question.html header="pi_dogs combine artists"
text='Combine the multiple "Artist Name" columns into a single multi-valued column.'
solution='Use forRange to generate the numbers: `forRange(1, 5, 1, r, cells["Artist Name " + r].value).join("|")`' %}
