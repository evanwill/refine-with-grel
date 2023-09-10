---
section: Examples 
nav_order: 3
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
