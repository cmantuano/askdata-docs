Askdata Python client is a friendly Python library that helps developers, data scientists and engineers build and manage agent using Askdata platform. Creating an Agent will allow you to enhance your experience with data and have fun playing with it.


# Getting Started with the Askdata Python SDK

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
You will be prompted to insert your user details. Once you have done that, you good to go.

## Query your data

This is an example of a query using the SDK. We select the agent called *Sales Demo* and we ask: *give me sales by countries*
```python
# Load the list of the agents connected to your account as a pandas dataframe
get_agents_df = askdata.agents_dataframe()
# Get one agent
agent = Agent(askdata, 'Sales Demo')
# Simple query
df = agent.ask('give me sales by countries')
df
```

## How to create or replace a dataset for a given Agent

```python

# the first three parameters are mandatory, they are needed to understand if the dataset already exists (i.e. needs to be replaced)
# or needs to be created
my_second_agent.create_or_replace_dataset(frame=df, dataset_name='Web Sources', slug="timesheet" , icon_url=None,
                                  settings = None):
```


## Example Notebooks

You can easily understand how to integrate the Askdata SDK using these Python Notebooks step-by-step walkthrough.

https://github.com/AskdataHQ/askdata-docs/tree/gh-pages/notebooks

{% include links.html %}