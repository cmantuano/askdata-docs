---
title: How to dynamically transform the value from a dataset query result
keywords: documentation
last_updated: October 15th, 2020
tags: [getting_started]
sidebar: mydoc_sidebar
layout: doc

---

    In order to dynamically transform the output of a value returned by a query without changing the data-source you can use the field **Value Formatting** available in your dimension property. 

Dataset contextual window -> Schema -> Select your Dimension -> **Value Formatting**

**Examples:**  


In order to extract "John Doe" from a string that is "Prefix - John Doe - Suffix"

**You can use the following function:**

var my\_list = value.split('-'); var first = my\_list[list\_gestore.length-1] ; var last = first.split('–') ; last[last.length-1]

‍

‍



    {% include links.html %}

    