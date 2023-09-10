---
section: Examples
nav_order: 2
title: Cross Function
nav: Cross
---

The cross function retrieves data from another Refine project on your computer based on a common column. 
Keep in mind cross can't fuzzy match, and unlike reconciliation or clustering there isn't an interface to help manually select matches, so cross depends on clean key columns. 

The function looks like:

`cross(cell, projectName, columnName)`

The second argument is the exact name of another project on your computer and the third argument is the exact name of column in that project. 
To do a lookup with in the current project, you can give `""` for the second argument. 

The cross will return an array that is the `row` objects for any matches between the current cell and the key column.

## Use Examples

Common use would be to take the first match and bring in a value from a column in the other table, which looks like:

`cell.cross("other_project", "key_column")[0].cells["column_name"].value`

To access values from multiple columns: 

`with(cell.cross("other_project", "key_column")[0], a, a.cells["col1"].value + ";" + a.cells["col2"].value)`

Because cross returns an array of row objects, you could do more complicated look ups as well. 
For example, to access multiple matches, add a forEach:

`forEach(cell.cross("other_project", "key_column"), r, r.cells["column_name"].value).join(";")`

For multiple matches, with multiple columns: 

`forEach(cell.cross("other_project", "key_column"), r, forEach("colname1|colname2|colname3".split("|"), c, r.cells[c].value).join(";")).join("|")`
