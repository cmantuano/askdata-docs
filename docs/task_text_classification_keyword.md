---
title: AI Task Text Classification Keyword
keywords: documentation
last_updated: November 30th, 2021
tags: [admin-guide]
sidebar: mydoc_sidebar
layout: doc
---

This workflow automatically classify a sentence, basing on a structure that bind a labels with list of words, called keywords. This application is language-free.

# About the task #

The workflow requires as input:
  - Dataset
  - Column: name of a column to classify of the given dataset.
  - Output column name: (*optional*) name of the target column where the outputs will be stored. Default is "Topics".
  - Slug of Dataset Output: slug where the output dataset will be saved.
  - Labels and keywords: dictionary to bind a label (the keys) to a list of keywords (the values).

The workflow returns as output the input dataset with the addition of the *output_column_name* with the model outputs.


## Model and classes ##

A user has the free choice of the dictionary to be inserted. An example is the following: 

Labels and keywords : ```{'sport':['sport', 'calciatore', 'portiere', 'calcio', 'nuoto','basket', 'salto', 'alpinismo', 'karate'], 'mestiere':['panettiere', 'operaio', 'avvocato', 'autista', 'ingegnere', 'medico', 'cassiere']}```


## Example of usage ###

|Sentence|Class|
|-|-|
|Ieri la prima squadra di calcio in classifica ha vinto un grande premio in denaro.|sport|
|Dobbiamo dare al nostro avvocato le spiegazioni che ci ha chiesto.|mestiere|
|Il campione di nuoto Andrea Rossi ha battuto il record mondiale di stile libero.|sport|


{% include links.html %}
