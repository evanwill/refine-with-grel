---
section: Expression Basics
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
