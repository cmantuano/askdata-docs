---
title: AI Task Sentence Classification (Italian)
keywords: documentation
last_updated: November 30th, 2021
tags: [getting-started]
sidebar: mydoc_sidebar
layout: doc
---

This workflow automatically classify italian sentence or tickets using a proprietarly AI-driven NLP classification model.

# Instruction to use #

The workflow requires as input:
  - dataset
  - column_name: name of a column to classify of the given dataset
  - output_column_name: optional name of the target column where the outputs will be stored. Default is "Topics".
  - model: optional string to specify the model, used to classify the input sentence. Default model is.

The workflow returns as output a new dataset with the selected *column_name* and the *output_column_name*.


### Model and classes ###

Default model is a one-shot classifier.

Two owner models can be used writing in the box "timmodel" to use a sentence classifier or "sogeimodel" to use a ticket classifier.

Get in touch with the Askdata team if you want to bind a new model.


## Example of output ###

|Sentence|Topics|
|-|-|
|we|a|


{% include links.html %}
