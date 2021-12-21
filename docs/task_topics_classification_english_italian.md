---
title: AI Task Topics Classification (English, Italian)
keywords: documentation
last_updated: November 30th, 2021
tags: [admin-guide]
sidebar: mydoc_sidebar
layout: doc
---

This workflow automatically finds topics of given input sentences, using an AI-driven NLP classification model.

# About the task #

The workflow requires as input:
  - Dataset
  - Column: name of a column to classify of the given dataset.
  - Output column name: (*optional*) name of the target column where the outputs will be stored. Default is "Topics".
  - Slug of Dataset Output: slug where the output dataset will be saved.
  - Labels: (*optional*) list of labels or classes to classify the input sentence. Default classes are described in the next section.

The workflow returns as output the input dataset with the addition of the *output_column_name* with the model outputs.


## Model and classes ##

Default model is a zero-shot classification model based on BERT, with output labels: ```Greeting, Error, Report, Solved, Request, Payment, View, Documents, Other, Action, Office, Blocked, Income```.

Also, other labels can be specified, as: ```mobile, fixed, fiber, internet, network, mail, phone, technology, decoder, other, missing operators, assistance, disservice, forum, report, product, problem, tim box, tim vision, dazn, price, registration problem, access problem, video problem, connection problem, charge problem```.

Get in touch with the Askdata team if you want to bind a new model.


## Example of usage ###

The following examples are used with labels = ```mobile, fixed, fiber, internet, network, mail, phone, technology, decoder, other, missing operators, assistance, disservice, forum, report, product, problem, tim box, tim vision, dazn, price, registration problem, access problem, video problem, connection problem, charge problem```.


|Sentence|Topics|
|-|-|
|Salve, ho parlato con un operatore ma non ha risolto il mio problema. La mia linea internet non funziona da 7 giorni.|access problem, internet|
|Salve, ho chiamato più volte ma l'assistenza non risponde! Il mio smartphone non si carica ed ha quale problema.|phone, assistance|

{% include links.html %}
