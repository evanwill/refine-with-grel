---
section: More 
nav_order: 5
title: facetCount
---

Sometimes you have a column with many repeating values that you might explore using a text facet. 
In the text facet pane you can sort by facet count, but it would be difficult to subset based on the facet count. 

To select a group of rows based on the facet count of a value in a column: 

First, if you just need all the values with > 1 count, you can use the built in *Facet > Customized facets > Duplicates facet*{:.ui-item}. 
This returns true for rows with > 1 count, false if the value is unique.

Second, if you need a subset based on the count, create a new column or custom facet using the `facetCount` function.
On the column you want a count for use:

`value.facetCount("value","name_of_the_column")`

The first argument `"value"` is actually an expression (which oddly is given in quotes, unlike other functions).
The "name_of_column" could be a different column than the one the cell is in. 
If you are using the current column, you can use the builtin variable `columnName` instead, like `value.facetCount("value",columnName)`.

The result will be a number (same as the "count" given in facet pane), which you can then filter with a numeric facet.

If you want to add transformations to the value first, apply the same to the value feeding in as the first argument:

`value.fingerprint().facetCount("value.fingerprint()",columnName)`
