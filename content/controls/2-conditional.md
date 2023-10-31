---
section: Controls
nav_order: 2
title: Conditionals (If Statements)
nav: Conditionals
---

Conditionals allow you to test using a condition, then apply different expressions or outputs depending on the result.
A conditional expression looks like:

`if(expressionTest, expressionTrue, expressionFalse)`

The first argument is an expression that evaluates to true/false.
If the result for the cell is true, then the second argument will be used to output a value.
Otherwise, the third argument will be used. 

*Note: if your conditional expression doesn't actually return true/false, the window will not display an syntax error and GREL assumes it is false!*

The arguments can be string values or complete expressions providing flexibility to create complex outputs.

{% include alert.html text="Keep in mind that many of these outputs can be achieved by using faceting/filtering and applying different transformations to the subsets. 
Take a pragmatic approach to how difficult the expression is to write vs using facets. 
However, having the operation represented as a conditional expression may help make your processing more reuseable." color="info" %}

### Example Flowchart

Let's visualize this simple conditional, if the length of the cell's value is more than 10 characters, output "Big", otherwise output "Small": `if(value.length() > 10, 'Big', 'Small')`

{% include figure.html img="conditional-example.svg" alt="flow diagram showing parts of the expression if(value.length() > 10, 'Big', 'Small)" %}

## Common Tests

- To test numbers you can use operators such as `<` or `>`, e.g. `value.length() > 10`.
- To test if two values are equal use double equal signs `==`, e.g. `value == "Dogs"`.
- Test if the row is starred or flagged use built in variables, e.g. `row.starred` or `row.flagged`.
- Test the cell type with `isBlank(value)`, `isNonBlank(value)`, `isNull(value)`, `isNotNull(value)`, `isNumeric(value)`. This can be a useful check to avoid errors in a further expression.
- Test if the array contains a specific value using `inArray(a, s)`.
- Test string contents using:
    - `startsWith()` -- check using string only
    - `endsWith()` -- check using string only
    - `contains()` -- check using string or regex
    - `indexOf()` -- if it finds a match of your substring it returns the index number of the first instance, otherwise `-1`.
    - `lastIndexOf()`-- if it finds a match of your substring it returns the index number of the last instance, otherwise `-1`. 

## Boolean Operators

You can combine conditions with [Boolean functions](https://openrefine.org/docs/manual/grelfunctions#boolean-functions){:.docs-link} to build more complex tests, using `and()`, `or()`, `not()`, or `xor()`.
It is easiest to string boolean conditions together using dot notation. 
Each boolean function will contain an argument that is an expression that evaluates to true/false.

- example: `if(isNonBlank(value).and(value.startsWith("A")),"y","n")`

## Nested Conditions

Multiple conditional can be nested to create elsif or switch type flow. 
Use white space to help make the expression more readable!

```
if(cells["format"].value == 'image/jpeg', 'https://www.example.com/images/' + value,

    if(cells["format"].value == 'application/pdf', 'https://www.example.com/documents/' + value,

    if(cells["format"].value == 'video/mp4', 'https://youtu.be/' + value,

null)))
```

## Filter 

Filter is a control to subset an array based on conditions.
A filter expression looks like:

`filter(expressionArray, v, expressionTest)`

The first argument is an expression to create your array.
The second argument is a variable name to be used represent each array value in the next expression (this can be anything!).
The third argument is an expression, using the variable name, that evaluates to true/false.

Each item in the array will be tested using the condition.
If true, the item will be added to a new output array. 

For example, remove any term that contains "dogs" from list of subject terms in a multi-valued field: `filter(value.split(";"), v, v.indexOf("dogs") < 0).join(";")`.

## Examples

- Transform your stars into a column 
    - Create new "starred" column using expression: `if(row.starred, "Starred", "")`
    - Create new "issues" column using expression: `if(row.starred.and(row.flagged), "True", "False")` 
- Compare two columns 
    - Create new "equal" column using expression: `if(cells["column1"].value == cells["column2"].value, "true", "false")`
- Evaluate the number of blank cells in a row
    - Create new custom numeric facet using expression: `filter(row.columnNames,c,isBlank(cells[c].value)).length()`
- Remove blank items from an multi-valued field: `filter(value.split(";"), v, isNonBlank(v)).join(";")` (this can be handy to prep an array for another function)
- Find all columns containing a pattern: `filter(row.columnNames, v, cells[v].value.toLowercase().contains("example")).join(";")`

----------

## Exercises 

{% capture solution %}
Creating a new column from the current "Artist_Info" column, use multiple conditions to add "Description" values that start with `Born ` to the end of non-blank values:

```
if(cells.Description.value.contains(/^Born /), 

if(isNonBlank(value), value + ". " + cells.Description.value, cells.Description.value),

value )
```

{% endcapture %}
{% include question.html header="pma_cataloguedeluxeo00unse Description Field"
text='"Description" column seems to have two types: descriptions of the item or ones that start with "Born " describing the artist (explore by text filter on "born" and invert). Create a new column "artist_description" that combines the artist descriptions with the current "Artist_Info" values.'
solution=solution %}

{% include question.html header="pma_cataloguedeluxeo00unse Item Num"
text='Is "Item_Num" the same as "Desc_Num"? Create a custom text facet to compare.'
solution='On the "Item_Num" column, create a custom facet using expression: `if(value.toString() == cells["Desc_Num"].value.replace(".",""), "true", "false")`'
%}
