---
title: AI Task Sentence Classification (Italian)
keywords: documentation
last_updated: November 30th, 2021
tags: [getting-started]
sidebar: mydoc_sidebar
layout: doc
---

This workflow automatically classify italian sentence or tickets using a proprietarly AI-driven NLP classification model.

# About the task #

The workflow requires as input:
  - dataset
  - column_name: name of a column to classify of the given dataset
  - output_column_name: optional name of the target column where the outputs will be stored. Default is "Topics".
  - model: optional string to specify the model, used to classify the input sentence. Default model is [...].

The workflow returns as output a new dataset with the selected *column_name* and the *output_column_name*.


## Model and classes ##

Default model is a one-shot classifier based on Bert model. The labels are: ```internet, mail, phone, technology, other, assistance, disservice, report, product, problem, price,  access, video, audio, games, light, building```.

Get in touch with the Askdata team if you want to bind a new model.


## Example of usage ###

|Sentence|Classes|
|-|-|
|Salve, ho chiamato più volte ma l'assistenza non risponde! Il mio smartphone non si carica ed ha quale problema.|Consumer, Experience, Mercato, Tecnologia|
|Buongiorno, la mia linea internet va un pò lenta da qualche giorno, potete inviare un tecnico?|Consumer, Experience, Mercato|


{% include links.html %}
