---
title: Blog
keywords: documentation
last_updated: May 11th, 2021
tags: [getting-started]
sidebar: mydoc_sidebar
layout: doc
---
# The Script Component
This component allows the user to implement simple javascript transformation for resultset.

Here is an example:

```javascript f

var myAnswer = [];
for (var i = 0; i < q1Result.length; i++) {
myAnswer.push({
'area':q1Result[i].area,
'sales':q1Result[i].sales,
'great':q1Result[i].sales >= 100 ? 'high' : 'low'
});
};
myAnswer

```
