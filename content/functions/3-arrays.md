---
section: Functions
nav_order: 3
title: Array Functions
nav: Arrays
---

In Refine an *Array*{:.term} is data structure representing an ordered set of values, displayed as a comma separated list enclosed by square brackets, e.g. `["example", "two", "three"]`.

However, **cells can not directly store an array**.
Instead, you will have to split a value to create an array, use [array functions](https://openrefine.org/docs/manual/grelfunctions#array-functions){:.docs-link} to manipulate the data, and then join the array back into a string. 

If you think of the patterns in your strings as potential chunks in an array, this becomes a surprisingly powerful approach for wrangling data!
Puzzles like getting the last word from a the sentence, the stuff after the coma, the unique words, or the filename from a URL become much easier.

## Split

Since cells do not contain arrays, we start by strategically splitting the value into parts.
For example, create an array by splitting:

- a multi-valued cell on a separator or deliminator character, e.g. semicolon `value.split(";")` or pipe `value.split("|")`
- a string based on a meaningful feature or pattern, e.g. space for basic word `value.split(" ")`, white space `value.split(/\s/)`, or new line `value.split(/\n/)`
- a string based on pattern of the numbers of characters, e.g. `value.splitByLengths(3,3,4)` (note: this will throw out characters beyond the total)

## Bracket Notation

The individual values in the array can be accessed using an index number in bracket notation. 
The index starts at 0, e.g. first item `value.split(";")[0]` or third item `value.split(";").sort()[2]`.
Alternatively, you can use negative numbers to count backward in the array, e.g. last item `value.split(";")[-1]` or third to last item `value.split(";").sort()[-3]`.

Bracket notation can also be used to select a range of items (a short cut for `slice()`), e.g. `value.split(";").sort()[2,4]`.

## Join 

Some expressions, such as using an index number or length, will result in a regular string value ready to go into the cell. 
However, if the result of your expression is an array, you will need to reconstitute it into a string using `join()`. 
This could be the same pattern that you used to split, a new character to create a string, or unique deliminator useful for future splits, e.g. `.join("|||")` or `.join(";")`. 

If you forget to add the join, the result of the transformation will be an error. Depending on what "On error" option you chose, it may not be clear that your expression didn't work!

## Examples of Common Array Functions

For example, if we had a column with multi-valued cells representing lists of items like "dogs;cats;muffins;cats": 

| Description | Expression | Output |
| --- | --- | --- |
| `split()` creates an array | `value.split(";")` | [ "dogs", "cats", "muffins", "cats" ] |
| `length()` count the number of items in the array | `value.split(";").length()` | 4 |
| `sort()` returns the array sorted, ascending order, case-sensitive with uppercase first and lowercase second | `value.split(";").sort().join(";")` | "cats;cats;dogs;muffins" |
| `reverse()` returns the array in reversed order | `value.split(";").reverse().join(";")` | "cats;muffins;cats;dogs" |
| `uniques()` returns only the unique values, removing duplicates | `value.split(";").uniques().join(";")` | "dogs;cats;muffins" |
| `slice()` returns an array of items starting from the first argument (including it) to the second number (no including it). | `value.split(";").slice(n, n)` <br>or bracket `value.split(";")[n, n]` | |
| Remove first item | `value.split(";").slice(1).join(";")` | "cats;muffins;cats" |
| Remove last item | `value.split(";").slice(0,-1).join(";")` | "dogs;cats;muffins" |
| Remove first and last | `value.split(";")[1,-1].join(";")` | "cats;muffins" |
| Get the second and third items | `value.split(";").slice(1,3).join(";")` | "cats;muffins" |
{:.table .table-bordered}

-------------

{% include question.html header="pi_dogs identifier"
text='Extract the identifier from the "Document" column.'
solution='One method `value.split(",")[0].split(" ")[-1]`' %}
