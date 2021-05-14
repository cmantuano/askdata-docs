---
title: Create a Data Card - HTML Component
keywords: documentation
last_updated: April 26th, 2021
tags: [getting-started]
sidebar: mydoc_sidebar
layout: doc
---
# The HTML Component
This component allows the user to implement HTML code to enhance the Data Card. 
The code could be used for graphical reason (as shown in the picture below) but also for more practical ones. 
In fact, the results of the query can be accessed within the HTML editor(the variable name must be specified in the settings tab), which is available by clicking the **Edit button**. 

Here is an example:

<p align="center">
  <img src="media/result_html.PNG" style="max-width:500px" />
</p>

## How templating format work

HTML components supports Handlebar, a powerful stateless templating system that give you the power necessary to let you build semantic templates effectively with no frustration.

```javascript f

This is the first result element of the resultset data1Reseult with the column brand:  {{#data1Result.1.brand}}
```

## How to bind an array to the HTML component

```javascript f

<ul>
{{#data1Result}}
<li>
<b>Brand:</b> {{brand}} for total ${{vendite}}; 
</li>
{{/data1Result}}
</ul>

```
