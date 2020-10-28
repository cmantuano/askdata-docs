---
title: Askdata Python SDK
keywords: documentation
last_updated: October 15th, 2020
tags: [getting-started]
sidebar: mydoc_sidebar
layout: doc
---

Askdata Python client is a friendly Python library that helps developers, data scientists and engineers build and manage agent using Askdata platform.

### Getting Started with the Askdata Python SDK

Getting up and running with Askdata python client is easy. Install client from [pypi](https://pypi.org/project/askdata/):

<h1 align="center">
	<img width="300" src="https://uploads-ssl.webflow.com/5dff758010bfa7f94c98e37e/5e9b0ff61b847f206e4c8da8_askdata-logo-black-p-500.png" alt="Askdata">
	<br>
	<br>
</h1>

# Askdata Examples

[![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/AskdataInc/askdata-examples/blob/master/notebooks/Askdata%20-%20Quickstart.ipynb)
This repository contains examples of [Askdata](https://www.askdata.com/) usage in serving different types of data.

## Installation
``
 pip install askdata 
``
or
``
pip install -r requirements.txt
``
## Authentication
Lets handle our authenticaton
```python
import askdata as ad
from askdata.askdata_client import Askdata, Agent
askdata = Askdata()
```
Once your insert your account and password you're all set
## Query your data
```python
# Load the list of the agents connected to your account as a pandas dataframe
get_agents_df = askdata.agents_dataframe()
#get one agent
agent = Agent(askdata, 'Sales Demo')
# Simple query
df = agent.ask('give me sales by countries')
df
```
## How to create a new Askdata Agent and to Create a dataset

```python
# Load the list of the agents connected to your account as a pandas dataframe
my_second_agent.save_to_dataset(frame=df, dataset_name='Web Sources')
```
## Askdata Video Demo
Check the following tutorial, to learn more about Askdata end-to-end. 
[![Askdata Tutorial](https://img.youtube.com/vi/uEc9ogi2-10/0.jpg)](https://youtu.be/uEc9ogi2-10) 


{% include links.html %}
