---
title: Configure your Dataset
keywords: documentation
last_updated: April 06th, 2021
tags: [admin-guide]
sidebar: mydoc_sidebar
layout: doc
---

## Configure your dataset

Once the Dataset is connected you will be able to configure it ( change or enrich your data).

1. Go to your **Workspace** and choose the **Dataset** you would like to configure 

2. Click on the selected **Dataset**

<img src="/media/admin-guide/dconf_1.png" class="image-doc p-3">

3. In the opened tab go to the **Schema** to work with data properties.

<img src="/media/admin-guide/dconf_2.png" class="image-doc p-3">

4. Choose the data you would like to work with and click on it as it is shown below.

<img src="/media/admin-guide/dconf_3.png" class="image-doc p-3"> 

5. Work with available parameters on the following tabs:

**Main**
 - Code*: Code to be used when referring to this column
 - Name: Name of the column to be displayed
 - Parameter Type: Type of the parameter: Dimension or Measure

<img src="/media/admin-guide/dconf_4.png" class="image-doc p-3">

**Manage**

 - Enabled: Enable the column for queries

**Metadata**

 - Description: Description of the column
 - Sample Queries: Example of queries to be associated with the column
 - Icon: Change the icon of the column. Either pick one or upload yours.

<img src="/media/admin-guide/dconf_6.png" class="image-doc p-3">

**NLP**

 - Mandatory: Set the column as mandatory.
 - Synonyms: Is an important field used to manually create synonyms to the data to increase data search probability. This means that when I query using the synonyms, the selected data will be displayed.
 
<img src="/media/admin-guide/dconf_7.png" class="image-doc p-3">

**Output**

 - Aggregation: Set an aggregation function among AVG, MIN, MAX and SUM
 - Indexed With: Specify Technical key for the current column (only dimension) to optimise the query
 - Searchable: Make elements in the results clickable to narrow down the dataset

<img src="/media/admin-guide/dconf_9.png" class="image-doc p-3">

**Formatting**

Formatting is a very important tab to work with data format.

**Number** **formatting**:

 - Number Formatting: Set a format for the numbers. Various options available
 - Number Locale: Set the region you are number refers to: us, en, it or fr.
 - Default Time Dimension for Measure - select the Default Time Dimension column for being used for  measure

<img src="/media/admin-guide/dconf_10.png" class="image-doc p-3">

**Date** **formatting**:

 - Is Date: Yes if this column is a date
 - Input Date Format
 - Output Date Format: Set a standard format for the dates
 - Is Default Date Column: Yes or No
 - Value Formatting: Custom Javascript expression to format the values in the column. Must return a string. 

<img src="/media/admin-guide/dconf_12.png" class="image-doc p-3">

**Data**

<img src="/media/admin-guide/dconf_14.png" class="image-doc p-3">

**Dynamic**

 - Synonym Generation Logic: You can use a custom logic to generate synonyms with a specific behaviour
 - Custom: boolean: Yes if you are creating a new column, No otherwise
 - Custom Expression: You can define a custom logic to define a new column
 - Ignore Aggregation for Measures: For custom expressions ignores the default aggregation of the measure
 - Custom Filter: Inject a custom filter when a specific is requested
 - Dynamic Entities: You can define a custom logic to automatically create entities related to that dimension
 - Default Injections: Set another column to be shown with (i.e. when I query sales also show the year, without specifying the word year). Applied when no other dimensions and measures are requested
 - Injections: Set another column to be shown with (i.e. when I query sales also show the year, without specifying the word year). Always applied

<img src="/media/admin-guide/dconf_15.png" class="image-doc p-3">

**GEO**

 - Is Geo Parameter: Yes if this column is a Geo Parameter
 - Latitude: Name of the field where to find the value of the latitude
 - Longitude: Name of the field where to find the value of the longitude
 - External Resource: Path for an external resource where to find the geo attributes
 - Key from external resource: The name of the field in the external resource that contains the join field
 - Value Formatting: Instructions on how to format the values

<img src="/media/admin-guide/dconf_16.png" class="image-doc p-3">

**Value**

<img src="/media/admin-guide/dconf_17.png" class="image-doc p-3">

6. Once is done click **Save** to finish your data configuration.






