---
title: How to train a synonym
keywords: documentation
last_updated: October 15th, 2020
tags: [admin-guide]
sidebar: mydoc_sidebar
layout: doc
---

**Training the Askdata agent**

Open the Askdata Console and select one agent where you have admin rights.

In the datasets, section click on the dataset related to the measures or dimensions that you want to train with a new synonym.

After the opening of the contextual modal click on **Schema**.

Click on the entity (dimension) or measure that you want to train with an additional synomym and add them in the “Synonyms” fields. Synonyms are not case sensitive.

!["updating name and adding synonyms"](media/updating_name_and_adding_sysnonyms.gif)

*Suggestion: to avoid confusion always add the measure\metric name in the list of available synonyms*

*You can also add a synonym for specific values eg. to add the synonym "Great Apple" to the value "New York" inside the dimension "Cities".* 

*In that case, you have to set the "Import Values" setting to true in the dimension and save. And, check the list of values in the "View values" section in the related dimension.*

{% include links.html %}
