---
nav_order: 1
title: The Strategy (and Art) of Refine
nav: Strategies
---

OpenRefine is a unique data wrangling tool that presents a flexible interface unlike traditional spreadsheets or databases.
With Refine you typically don't know what the data issues are or the methods needed to fix them--instead, like solving a puzzle, the art of Refine is an iterative process of exploring, testing, and transforming.
Before diving into writing expressions to transform data, let's look at general strategies for using Refine that will apply no matter which functions we use.

## Know Your Data

- Explore your columns and values -- is there a data dictionary? Is there relationships between columns? Is there processing contexts that help explain current state? (e.g. data source from OCR, web harvest, or database exports)
- Identify data anomalies and challenges -- are there outliers that don't make sense? Outliers in specific contexts? Inconsistent formats, unnecessary white space, extra characters, typos, incomplete records, multi-valued cells, etc... (e.g. use text length facet to check string fields)
- Record a *Coherence Check*{:.term} -- what is your expected number of rows? Always keep this number in mind as you work through the project.

## Filter and Subset 

- Don't try to find *The One* solution to fix values in every row. Be pragmatic in applying a variety of transformations for the different issues represented in the column.
- Isolate groups of values in a column that need similar transformations using filters and facets on multiple columns.
- Use stars and flags to build up more complicated subsets with some manual intervention. Create a column to record the grouping (true/false or name it).

## Create New Data

- Add new columns when transforming. Check against the original values.
- Add temporary columns and values to hold useful information.
- Work through multiple step transformations--create what you need for the transformation, don't worry about the final output shape until your data is clean.

*(just remember, you generally can't create new rows, unless you are breaking apart values in existing rows)*

## Organize 

- Export your data or project regularly, and name the files following a convention.
- Save your operation history in a text file for reference (not in a Word doc).
- If necessary subset and export, then recombine later.
