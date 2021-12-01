---
title: AI Task Italian Sentiment & Emotion Classification
keywords: documentation
last_updated: December 1st, 2021
tags: [getting-started]
sidebar: mydoc_sidebar
layout: doc
---

The Italian Sentiment & Emotion Classification Task is a workflow that generates automatically sentiment and emotion values for italian sentences, using proprietarly AI-driven NLP model.


# About the task #

The workflow requires as input:
- **dataset** (*mandatory*)
- **column_name**: name of a column of the given dataset (*mandatory*)

The classification is done with two models:
- a BERT-based model that outputs **sentiment**, whose possible labels are: ```Positive, Neutral, Negative```
- a model that outputs **emotion**, whose possible labels are: ```Happy, Sad, Angry```

Thus, the workflow returns as output a new dataset with the selected **column_name** and the outputs of the aforementioned model.

# Example of usage #

Given the dataset below with some italian sentences and as column_name the *sentence* column:

|ID|sentence|
|--|-------------|
|0|Questo prodotto per la pelle è fantastico|
|1|Questa zuppa è disgustosa|

The outcome is:

|ID|sentence|sentiment|emotion|
|--|-------------|-|-|
|0 |Questo prodotto per la pelle è fantastico|Positive|Happy|
|1 |Questa zuppa è disgustosa|Negative|Angry|

{% include links.html %}
