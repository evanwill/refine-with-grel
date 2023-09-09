---
section: Controls
nav_order: 3
title: Iteration (Loops)
nav: Iteration
---

forEach()
forEachIndex()


Merging all or more than two columns in a project
forEach(row.columnNames,cn,cells[cn].value).join("|")
forEach("colname1|colname2|colname3|colname4|colname5".split("|"),cn,if(isNull(cells[cn]),"",cells[cn].value)).join("|")

get all instances of a key from json array
`forEach(value.parseJson().keywords,v,v.text).join(":::")`

with(expression o, variable v, expression e) [I rarely use, but is sort of a way to write creating an array and then using a control with it in a cleaner way]

forRange(number from, number to, number step, variable v, expression e)

