---
section: More 
nav_order: 6
title: Character Encoding
---

Issues with character encoding are especially challenging in metadata work that uses multiple tools / platforms and contains characters from multiple languages.
Corrupted or misinterpreted characters can be hard to detect and go unnoticed. 
The problems are often induced before the data gets to Refine (such as opening UTF-8 with Excel). 

To avoid issues in Refine check the character encoding at import.

If you find corrupted characters, isolate the rows and try using the `reinterpret()` function with an [encoding option supported by Java](https://docs.oracle.com/javase/1.5.0/docs/guide/intl/encoding.doc.html) such as "utf-8". 

The *Facet > Customized facets > Unicode char-code facet*{:.ui-item} or `unicode(value)` function can generate a list of character codes which can be used to detect issues (see [unicode facet](https://openrefine.org/docs/manual/facets#unicode-character-code-facet){:.docs-link}). 
The function `unicodeType(s)` will return a list of the unicode types represented in the string.

If your values have [HTML entities](https://developer.mozilla.org/en-US/docs/Glossary/Entity) such as `&amp;`, you can replace them with conventional characters using `value.unescape("html").unescape("xml")`.
