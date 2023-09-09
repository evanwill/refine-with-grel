---
section: Functions
nav_order: 2
title: String Functions
nav: Strings
---

Most values in the columns of GLAM data will be *Strings*{:.term}, a series of text characters (vs. other Refine data types: numbers, booleans, dates, or null).
GREL provides a variety of functions to manipulate and clean up string values.

## Common String Functions

- `value.replace("old","new")` -- Perhaps the most common function is replace which takes as arguments a string you want to find and what you want to replace it with.
- `value.replaceChars("áéíóú", "aeiou")` -- Rather than a string, this replaces all the individual characters listed in the argument. For example, this is often used to clean up junk characters resulting from OCR.
- Change case: 
    - `value.toLowercase()`
    - `value.toTitlecase()`
    - `value.toUppercase()`
- `value.trim()` -- removes white space from beginning and end of string.
- `value.slice(1,5)` -- returns characters starting from the first argument (including it) to the second number (no including it). Alternatively, you can use bracket notation for a short cut, e.g. `value[1,5]`.

## Examples

- Create a *Custom text facet*{:.ui-item}: 
    - just beginning of the values: `value.slice(0,5)`
    - combining multiple columns: `value.trim().toLowercase() + " " + cells["example"].value.trim().toLowercase()`
- Create a new column as a unique id with leading zeros: `"row_id_" + "0000"[0,4-length(row.index +1)] + (row.index +1)`
- Apply title case with hyphenated names: `value.replace("-"," || ").toTitlecase().replace(" || ","-")` (notice the strategic replace, use a temporary string that will be unique in the data to avoid unintended consequences!)
