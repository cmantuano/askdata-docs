---
title: Dataset Synonyms generator
keywords: documentation
last_updated: April 06th, 2021
tags: [admin-guide]
sidebar: mydoc_sidebar
layout: doc
---

## Synonyms Generator Logic

Askdata let you configure a business logic to automatically generate synonyms during the synchronization.

**ret** is the name of the variable that has to be set to provide a working synonuym to the platform
**value** is the original value from the dataset column

### Example 1:

Imagine that you have on your source dataset a column containing the values:

- Amazon Alexa
- Amazon Prime
- Amazon Fresh

And you want to assign a synonum to every single word of the value.

- Original value "Amazon Alexa" => Synonyms: "Amazon", "Alexa"
- Original value "Amazon Prime" => Synonyms: "Amazon", "Prime"
- Original value "Amazon Fresh" => Synonyms: "Amazon", "Fresh"

You can setup the ***Synonym Generation Logic*** with the following code

```lang-js

var ret = value.trim().toLowerCase();ret.split(' ')

```

The field can contains different business logic accpeting an array of string. Every string is a business logic like the example provided above.

**Example 2:**

```lang-js

// Push a new value to ret if value is different from the first word of the variable value
var ret = value.trim().toLowerCase().split(' ')[0]
if (value != value.trim().toLowerCase().split(' ')[0]) {
    ret = []
    ret.push(value.trim().toLowerCase())
    ret.push(value.trim().toLowerCase().split(' ')[0])
}

```
