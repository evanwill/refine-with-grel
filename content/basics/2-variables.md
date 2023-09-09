---
section: Expressions
nav_order: 2
title: GREL Variables
nav: Variables
---

Refine provides a set of *variables*{:.term} to access your data inside of expressions.

The most commonly used [variables](https://openrefine.org/docs/manual/expressions#variables) include: 

- `value` -- the value of the current cell, generally your starting point!
- `cells` -- an array of all the cells of the current row. 
    - Use bracket or dot notation to access values from other columns.
    - e.g. `cells["example_col"].value` or `cells.example_col.value`.
- `rowIndex` -- index number of the current row, starting from 0.

Less commonly used: 

- `row` -- access details associated with the row. 
    - e.g. `row.flagged` (true/false), `row.starred` (true/false), `row.columnNames` (array of all columns).
- `row.record` -- access [fields for record](https://openrefine.org/docs/manual/expressions#record) containing the current row.
- `cell.recon` -- access [reconciliation fields](https://openrefine.org/docs/manual/expressions#reconciliation) for the current cell.

{% include figure.html img="refine-variables.png" alt="row of spreadsheet table showing cell labelled with 'value' and 'cells[two].value' in the next cell to demonstrate variables" %}

## Example

GREL uses `+` to concatenate values. 
Use quotes around string values you want to add, e.g. `+ "-example"`.

Let's combine the values from different columns to create a unique id.

- *Edit column > Add column based on this column...*{:.ui-item}
- Name the column "newid"
- `rowIndex + "_" + value + "_" + cells["example"].value`
