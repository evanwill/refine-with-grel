---
section: More 
nav_order: 4
title: Parsing JSON
---

It is common to get JSON data when fetching from APIs using Refine. 
Using the `parseJson()` function allows you to retrieve data out of the JSON structure with bracket notation using the keys or index numbers. 

For example, if the cell contained

`{ "type" : "dog", "color" : "brown", "size" : "large" }`

and your transform was `value.parseJson()["color"]`, 
you would get the value "brown" in your new column. 

For nested values you can add additional brackets to navigate deeper into the structure, e.g. `value.parseJson()["items"][0]["title"]`.

To get multiple values from the same key, combine with a forEach.
For example, to extract all the keywords from a cell with the JSON

`{"language": "en", "keywords": [{"text": "dogs", "relevance": 0.979292}, {"text": "muffins", "relevance": 0.977987}, {"text": "cats", "relevance": 0.969001}, {"text": "idaho", "relevance": 0.967973}] }`

transform with `forEach(value.parseJson()["keywords"], v, v["text"]).join("; ")`, resulting in the new cell value of `dogs; muffins; cats; idaho`.

## Example 

If you had cells with Getty vocab identifiers like `tgn/9225352`:

- From the id column, create a new column "url" using `"https://vocab.getty.edu/" + value + ".json"`
- From "url" column fetch URLs into new column "results".
- On the "results" column, use `parseJson()` to explore the contents of the response.
- For example, extract type label: `value.parseJson()["classified_as"][0]["_label"]`

## Demo Project

A quick example using [Chronicling America search API](https://chroniclingamerica.loc.gov/about/api/). 

Create a project from clipboard, pasting in this CSV:

```
state,year
Idaho,1865
Montana,1865
Oregon,1865
Washington,1865
```

- From the "state" column, create a new column "url" using: `"https://chroniclingamerica.loc.gov/search/pages/results/?state=" + value.escape('url') + "&date1=" + cells['year'].value.escape('url') + "&date2=" + cells['year'].value.escape('url') + "&dateFilterType=yearRange&sequence=1&sort=date&rows=5&format=json"`
- From "url" column, fetch URLs into new column "results". The "results" will be the JSON response from the search API.
- On the "results" column, use `parseJson()` to explore the contents of the response.
- For example, we may want to extract the unique subject terms represented in the results: `forEach(value.parseJson()["items"], a, a["subject"].join(";")).join(";").split(";").uniques().join("; ")`
