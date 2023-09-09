---
section: Examples
nav_order: 2
title: Cross Function
nav: Cross
---

cross

https://github.com/OpenRefine/openrefine.org/issues/214

No fuzzy match (this isn't reconciliation or clustering) https://okfnlabs.org/reconcile-csv/
Work on a clean key column first 

## Cross function

Use `cross` to retrieve columns from other OpenRefine projects based on a common column. 

1. Open the two projects you want to join
2. Identify the common column to be used as a key. Ensure that it is a unique identifier, or cross won't work how you expect. You can create a new unique column on both projects by adding an index number an existing common column (on common column > Add column based on this column... > `value + "-" + row.index` ).
3. On the project where you want to import values, go to the key column you identified, and Add column based on this column...
4. In the expression window, put: `cell.cross("name_of_other_project", "name_of_key_column").cells["name_of_column_you_want_to_import"].value[0]`

You should have a new column that has the correct values from the other project.

https://github.com/OpenRefine/OpenRefine/wiki/Recipes#combining-datasets
