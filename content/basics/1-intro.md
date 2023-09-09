---
section_id: Expressions
nav_order: 2
title: Expressions Basics
#nav: Introduction
---

To flexibly extend Refine's built in data exploration and transformation features, the system supports the use of *Expressions*{:.term} in a variety of contexts.
Unlike a spreadsheet' formulas that are stored in a cell and update dynamically, Refine's expressions are applied as an operation iterating over the rows of the data to generate a result.

The most common use is when transforming the cells in a column or creating a new column:

- *Edit cells > Transform...*{:.ui-item}
- *Edit column > Add column based on this column...*{:.ui-item}

Less common uses:

- *Facet > Custom text facet...*{:.ui-item} or *Custom numeric facet...*{:.ui-item} 
- Click *"change"*{:.ui-item} on a currently applied facet
- *Edit cells > Split*{:.ui-item} or *Join multi-valued cells...*{:.ui-item}
- *Edit column > Split*{:.ui-item} or *Join*{:.ui-item} or *Add column by fetching URLs*{:.ui-item}
- *Export > Templating...*{:.ui-item}

{% capture view %}
**Facet and filter vs. Transform:**
Remember that facets and filters do not change the data, *only your current view and the subset your are working with*.
If you close the window, your filters and facets will go away, they aren't saved.
To save the current state, you can click *"Permalink"*{:.ui-item} near the project name, then copy the URL from your browser.
Following this link later will re-open the project with the set of filters you had applied (restoring the view, but not state of the data!).
{% endcapture %}
{% include alert.html color="info" text=view %}

## Expression Editor

Refine's interface provides an "Expression Editor" with features to help write and apply transformations to your data.
This is a unique tool that makes Refine different than scripting languages or databases.

{% include figure.html img="expression-editor.png" alt="openrefine interface window showing expression editor for custom text transform" %}

- *Language*{:.ui-item}
    - **General Refine Expression Language (GREL)** -- a small set of functions specifically designed for data transformation puzzles in Refine. It is a good introduction to programming concepts because it is not large, you can learn it *all* and apply it in powerful ways!
    - **Python / Jython** -- Python implemented on the Java VM. You can use python code and standard library, and send the result to the cell with `return`. Limitations: out of date Python 2 which was sunsetted in 2020.
    - **Clojure** -- Lisp-family language implemented on Java VM. Limitations: not commonly used, little documentation. 
- *Expression*{:.ui-item} -- text box a message to the right will say if there is a syntax error.
- *Preview*{:.ui-item} -- see live preview of expression, help testing and debugging expression, keep in mind it is only first 10 rows (your issue could be later in data).
- *History*{:.ui-item} -- operations you have recently used.
- *Starred*{:.ui-item} -- bookmark your operations! Save commonly used expressions that you can edit to quickly re-use.
- *Help*{:.ui-item} -- internal docs for quick reference while you are writing.
- *On error*{:.ui-item} -- this is important to understand implications! For many expressions any cell blank value will result in an error, leaving the resulting cell unexpectedly blank. 

{% capture check %}**Coherence Checks:** Once you click "okay" the operation will run--watch for the little yellow notification at the top of the window for a count of the number of cells modified! Or check Undo/Redo for count of cells that are changed. Get suspicious if the number of cells modified isn't what you would expect.{% endcapture %}
{% include alert.html text=check color="warning" %}
