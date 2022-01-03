---
title: Askdata Dataset Integration
keywords: documentation
last_updated: December 12th, 2021
tags: [getting-started]
sidebar: mydoc_sidebar
layout: doc
---

This documents explains how to extend the Askdata integration in order to provice reading capability for new datasets

#### Pre-Requirements

* Python Coding tool
* GIT
* Clone this repository: https://github.com/AskdataHQ/askdata-api-python-client (Askdata SDK)
* Clone this repository: https://github.com/AskdataHQ/askdata-dataset-integrations/tree/master/catalog (Askdata Dataset Catalog)

#### Step 1

Edit the datasets.yaml file in askdata-dataset-integrations/catalog and add the configuration for the new dataset. Remember to specify, in the fields section, what are the inputs that the user must insert in order to connect to the specific dataset.

<div class="alert alert-primary" role="alert">
  IMPORTANT: in order for the system to find the new dataset the driver value must be “Default”
</div>

*Example:*

```

-   code: MY_DATA
    name: My Data
    description : This dataset can be used to read from a My Data datasource
    driver: Default
    documentation : https://docs.askdata.com/docs/dataset-mydata
    icon : "https://icons.askdata.com/datasets/MyData.png"
    github: "AskdataHQ/askdata-dataset-integration/<code>"
    fields:
    -  code: "settings.fields.file"
       label: "Local File"
       type: "file"
       viewType: "upload"
       readOnly: true
       mandatory: true
       settings:
         accept: [ "multipart/form-data" ]
         folder: "dataset"
         uploadUrl: "{{host}}/smartdataset/files/{{agentId}}/dataset/{{datasetId}}"
    -   code: "settings.fields.view_id"
        label: "View Id"
        type: "string"
        viewType: "text"
        readOnly: false
        mandatory: true

```

#### Step 2

Commit the changes and push on the master branch

#### Step 3

Go to the Python SDK repository and open the file *integration.py*

*Example:*

Add a method with this signature:
```python:
def __read_new_dataset(settings: dict):
```

*Example:*

```python:
def __read_my_data(settings: dict):
```

Where the *_new_dataset* must be replaced with the type of the dataset code that is going to be added

The method must contain the code to read from the data source and the transformation of the data collected into a Pandas Dataframe.

The settings dictionary contains all the parameters already declared in the fields section of the YAML file.

Once the data import is complete add these two lines at the end of the method:

```
df = normalize_columns(df)
df.to_parquet(settings["parquet"])
```
Where df is the variable containing the dataframe with the data (you can rename it if necessary).

#### Step 4:

Go edit the read method in the same file
A case for the new dataset must be added so it cal call the method created the previous step.

eg. 
```
if type == "MY_DATA":
   return __read_my_data(settings)
```

#### Step 5:
Commit and push the code and wait a few minutes that the server gets the updates

####  Step 6:

Go to https://app.askdata.com and start using your new dataset!
