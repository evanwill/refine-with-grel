---
section: Examples 
nav_order: 5
title: Character Encoding
---

Character encoding, at import, isolate, reinterpret() 
character facet

https://openrefine.org/docs/manual/facets#unicode-character-code-facet
https://groups.google.com/g/openrefine/c/20eDwEJwpn8?pli=1

value.reinterpret("utf-8")
"latin-1"
java encodings, https://docs.oracle.com/javase/1.5.0/docs/guide/intl/encoding.doc.html

html entities (`&amp;`)
value.unescape("html").unescape("xml")

unicode(value)
