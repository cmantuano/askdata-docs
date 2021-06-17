---
title: NLP Pipeline Overview
keywords: documentation
last_updated: June 17th, 2021
tags: [getting-started]
sidebar: mydoc_sidebar
layout: doc
---

## NLP PIPELINE

Every time a user interacts in Natural Language with the search pulling data from a specific Workspace 
the input token e.g. *"Give me revenue by regions”* is analyzed not by a single algorithm but by a sequence of [NLP algorithms] optimized for specific NLP tasks:


<p align="center">
  <img src="https://github.com/AskdataHQ/askdata-docs/raw/gh-pages/docs/media/pipeline_overview.png">
</p>


Specifically, the input is classified by the first algorithm and if it fails, the input passes through the second algorithm:


<p align="center">
  <img src="https://github.com/AskdataHQ/askdata-docs/raw/gh-pages/docs/media/pipeline_overview_second.png">
</p>


## Default pipeline: SmartIntent + Human2SQL

The default pipeline is composed by **SmartIntent** + **Human2SQL**.

**SmartIntent** is a machine learning classifier that recognize similarities between texts, giving a score between the input and all the possible outputs.


<p align="center">
  <img src="https://github.com/AskdataHQ/askdata-docs/raw/gh-pages/docs/media/pipeline_smartintent_human2sql.png">
</p>


[NLP algorithms]: https://github.com/AskdataHQ/askdata-docs/blob/gh-pages/docs/nlp-advanced-configuration.md

{% include links.html %}
