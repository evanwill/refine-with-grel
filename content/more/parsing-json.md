---
section: Examples 
nav_order: 3
title: Parsing JSON
---

It is common to get JSON data when fetching from APIs using Refine. 
It's easy to grab specific dictionary values out of JSON cells using the built in JSON parse function. 
From the column with JSON, create a new column and transform with `value.parseJson().get('key')`, where 'key' is the dictionary key you want to extract. 

For example, if the cell contained
`{ "type" : "dog", "color" : "brown", "size" : "large" }`, 
and your transform was`value.parseJson().get('color')`, 
you would get the value "brown" in your new column. (*note*: if your key does not have spaces, you can use the shorter version like `value.parseJson().color`)

To get multiple values from the same key, combine with `forEach()`.
For example, to extract all the keywords from a cell with the JSON
`{"language": "en", "keywords": [{"text": "dogs", "relevance": 0.979292}, {"text": "muffins", "relevance": 0.977987}, {"text": "cats", "relevance": 0.969001}, {"text": "idaho", "relevance": 0.967973}] }`,
transform with `forEach(value.parseJson().keywords,v,v.text).join("; ")`, resulting in the new cell value of `dogs; muffins; cats; idaho`.
