---
section: More
nav_order: 2
title: Cross Function
nav: Cross
---

The cross function retrieves data from another Refine project on your computer based on a common column. 

The function looks like:

`cross(cell, projectName, columnName)`

The second argument is the exact name of another project on your computer and the third argument is the exact name of column in that project. 
To do a lookup with in the current project, you can give `""` for the second argument--this allows you to pull data from the current rows based on matches.

The cross will return an array that is the `row` objects for any matches between the current cell and the key column.
That is, the current value is checked against all the values in the other project column, and can return zero or more matches.

Keep in mind cross can't fuzzy match, and unlike reconciliation or clustering there isn't an interface to help manually select matches, so cross depends on clean key columns. 
One option is to use the string clustering functions `fingerprint(s)` (trim whitespace, to lowercase, remove punctuation, diacritics / accents, sort words alphabetically) or `ngramFingerprint(s, n)` (create ngrams of the size n given, remove duplicates, sort alphabetically) to create your key columns to find matches in text values that are *close* to the same.
However, since there isn't an interface (like facet clustering) it can be hard to evaluate the success of these methods.

## Use Examples

Check how many matches are available:

`cell.cross("other_project", "key_column").length()`

Common use would be to take the first match and bring in a value from a column in the other table, which looks like:

`cell.cross("other_project", "key_column")[0].cells["column_name"].value`

To access cell values from multiple columns in the other table: 

`with(cell.cross("other_project", "key_column")[0], a, a.cells["col1"].value + ";" + a.cells["col2"].value)`

Because cross returns an array of row objects, you could do more complicated look ups as well. 
For example, to access multiple matches, add a forEach:

`forEach(cell.cross("other_project", "key_column"), r, r.cells["column_name"].value).join(";")`

For multiple matches, with multiple columns: 

`forEach(cell.cross("other_project", "key_column"), r, forEach("colname1|colname2|colname3".split("|"), c, r.cells[c].value).join(";")).join("|")`
