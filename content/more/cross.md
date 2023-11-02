---
section: More
nav_order: 2
title: Cross Function
nav: Cross
---

The cross function retrieves data from another Refine project on your computer based on a common column. 

The function looks like:

`cross(cell, projectName, columnName)`

The first argument is the value you want to match (in this function `cell` is short for `cell.value`, i.e. the current cell value).
The second argument is the exact name of another project on your computer and the third argument is the exact name of column in that project that you want to match against.

The cross will return an array that is the `row` objects for any matches between the current cell and the key column.
That is, the current value is checked against all the values in the other project column, and can return zero or more matches--and each match returns the full row of data, so you can access those values.

## Key columns

To use cross the two projects will have columns with shared values, the key column used to match. 
In cases where you are trying to join to tables, you will prepare a key column by modifying existing values so that they can successfully match up. 
If you are expecting a 1 to 1 match, ensure your key columns are unique identifiers. 

Keep in mind cross can't fuzzy match, and unlike reconciliation or clustering there isn't an interface to help manually select matches, so cross depends on clean key columns. 
One option is to use the string clustering functions `fingerprint(s)` (trim whitespace, to lowercase, remove punctuation, diacritics / accents, sort words alphabetically) or `ngramFingerprint(s, n)` (create ngrams of the size n given, remove duplicates, sort alphabetically) to create your key columns to find matches in text values that are *close* to the same.
However, since there isn't an interface (like facet clustering) it can be hard to evaluate the success of these methods.

## Internal Lookup 

You can use cross within a single project to check for matches between two columns--this can be very useful, allowing you to check for matches in other columns and/or pull data from other rows based on the matches.

To do a lookup with in the current project, give `""` for the second argument (rather than a project name).

For example, from the column you want to check, creating a new column using `cell.cross("","other_column").length()` will give you the number of matches.

## Use Examples

Check how many matches are available:

`cell.cross("other_project", "key_column").length()`

The most common use is to get data from another table based on a common key column. 
This cross will take the first match and bring in a value from a single column in the other table:

`cell.cross("other_project", "key_column")[0].cells["column_name"].value`

To access cell values from multiple columns in the other table: 

`with(cell.cross("other_project", "key_column")[0], a, a.cells["col1"].value + ";" + a.cells["col2"].value)`

Because cross returns an array of row objects, you could do more complicated look ups as well. 
For example, to access multiple matches, add a forEach:

`forEach(cell.cross("other_project", "key_column"), r, r.cells["column_name"].value).join(";")`

For multiple matches, with multiple columns: 

`forEach(cell.cross("other_project", "key_column"), r, forEach("colname1|colname2|colname3".split("|"), c, r.cells[c].value).join(";")).join("|")`

-------------

## Exercises 

{% include question.html header="pi_dogs pma_cataloguedeluxeo00unse cross"
text="Are any of the artists listed in pi_dogs represented in pma_cataloguedeluxeo00unse?"
solution='In pi_dogs, create a clean version of "Artist_Name" that contains just the name. 
Then in both projects create new column from the artists names using `value.fingerprint()`.
Then on pi_dogs, from the "artist_fingerprint" column, create a cross column using `cell.cross("pma_cataloguedeluxeo00unse", "artist_fingerprint").length()`.' %}
