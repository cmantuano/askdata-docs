---
title: Dataset Advanced Configuration
keywords: documentation
last_updated: October 15th, 2020
tags: [getting-started]
sidebar: mydoc_sidebar
layout: doc
---

Welcome in the Advanced Configuration. This section of the documentation is specifically designed for proficient and expert users.

## Dataset Advanced Configuration Rules

Examples of datasets rules about sorting:

```javascript

{
   "when" : "!query.isSorted()",
   "order" : "PRICE" 
},
{
   "when" : "!query.isSortedByMeasure()",
   "order" : "PRICE ASC" 
},
{
   "when" : "!query.isSortedByDimension()",
   "order" : "PLACE DESC" 
},

{
   "when" : "!query.isSortedBy('place')",
   "order" : "PRICE DESC, PLACE ASC" 
}

```
