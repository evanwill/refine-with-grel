---
section: Controls
nav_order: 2
title: Conditionals (If Statements)
nav: Conditionals
---

## conditional

if(expression o, expression eTrue, expression eFalse)

nested if 

Evaluating conditions uses symbols such as <, >, *, /, etc. To check whether two objects are equal, use two equal signs (value=="true").

`if(row.starred, "yes", "no")`

Compare two columns - Create new "equal" column using expression:
`if(cells["column1"].value == cells["column2"].value, "True", "False")`

filter(e1, v, e test)


custom text facet of # of blank cells in a row
filter(row.columnNames,cn,isBlank(cells[cn].value)).length()


## boolean

add Boolean functions .and(), .or(), .not(), .xor()

## tests 

isBlank(e), isNonBlank(e), isNull(e), isNotNull(e), isNumeric(e), isError(e)
