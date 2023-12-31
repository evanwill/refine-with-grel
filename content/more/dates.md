---
section: More 
nav_order: 4
title: Dates
---

Dates in metadata are generally stored as string values following a descriptive standard. 
Refine has the ability to parse a variety of conventional date formats into the "date" data type (represented internally as "UTC: YYYY-MM-DDTHH:MM:SSZ"). 

This allows you to manipulate the dates or easily change to a new format.

For example, if you had a column with reasonably well formatted dates in multiple formats such as "10/15/1918", "Oct 15, 1918", and "1918-10-15", you can normalize the format using:

`value.toDate().toString('yyyy-MM-dd')`

If your dates are in unconventional formats or other languages, you can specify parsing options to avoid errors.
Check the [Refine Date functions](https://openrefine.org/docs/manual/grelfunctions#date-functions){:.docs-link} for details on the function or the [Java data syntax](https://docs.oracle.com/javase/8/docs/api/java/text/SimpleDateFormat.html).

------------

## Exercises 

{% include question.html header="pi_dogs dates"
text='Clean up the "Date or Range" column and convert to ISO date yyyy-mm-dd'
solution='Check for values like "aft." that will break parsing. Then create new column using  
`forEach(value.split("-"), d, if(d.trim().length() > 4, d.trim().toDate().toString("yyyy-MM-dd"), d.trim())).join(" - ")`' %}
