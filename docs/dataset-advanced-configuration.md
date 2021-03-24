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

**Examples of datasets rules about sorting:**

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

**Example with user defined security:**

```javascript

[
    {
        "when": "(user.username == "myuser@mymail.com2) && (user.details.user_type != null)",
        "then": "CASE WHEN '{{user.details.user_type}}' <> 'DIR' THEN AGENZIA IN ( SELECT agenzia_cod FROM VIEW_USERS WHERE user_id = '{{user.details.custom_id}}') WHEN '{{user.details.user_type}}' = 'DIR' THEN 1=1 ELSE 1 <> 1 END"
    }
]

```
