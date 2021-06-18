---
title: How to Publish a New Widget
keywords: documentation
last_updated: June 17th, 2021
tags: [getting-started]
sidebar: mydoc_sidebar
layout: doc
---

In order to publish a new widget, follow these steps:

## STEP 1: Create a folder named as the &lt;unique_code&gt; of the widget

In the following [Github repositoy] create a new folder with the same name as the widget's identifier **&lt;unique_code&gt;** (here [`widget_example`] in Figure below):

<p align="center">
  <img src="https://github.com/AskdataHQ/askdata-docs/raw/gh-pages/docs/media/folder_example_widget.png">
</p>

**Note** that the folder must be created inside the following path: [`/widgets/askdata/`] as in Figure.


## STEP 2: Copy the HTML widget you have developed


> For further information on *How to develop a HTML widget* 
> or if you need support about consuming the web-service for a specific data-card 
> you can refer to this [guide example for creating a HTML widget]


In the folder just created with path `/widgets/askdata/<unique_code>/` add the HTML file named `index.htm` as in figure below.

<p align="center">
  <img src="https://github.com/AskdataHQ/askdata-docs/raw/gh-pages/docs/media/folder_index_widget.png">
</p>

The main objective of the HTML template is to consume web-service with the convention (widgetId, widgetTypeCode):
- *widgetId* is the the identifier related to a specific widget within a datacard filled with data;
- *widgetTypeCode* is the unique identifier of the widget itself.

This means that when producing different widgets of the same type, these will have different *widgetId* but same *widgetTypeCode*.



## STEP 3: Create a configuration file to define settings

Each widget has its own configuration in order to define and visualize its setting on the right window.

It must be a *json* file structured as in the follow example:


```JSON
{
	"configuration": [{
        "code": "code",
        "label": "Chart code",
        "type": "string",
        "viewType": "hidden",
        "readOnly": false,
        "mandatory": false
    }, {
        "code": "name",
        "label": "Name",
        "type": "string",
        "viewType": "text",
        "readOnly": false,
        "mandatory": false
    }, {
        "code": "description",
        "label": "Description",
        "type": "string",
        "viewType": "text",
        "readOnly": false,
        "mandatory": false
    }, 
{
        "code": "queryIds",
        "label": "Queries",
        "type": "queryIds",
        "readOnly": false,
        "viewType": "dropdown",
        "mandatory": true
    }, {
        "code": "settings.m1_id",
        "label": "Measure",
        "type": "params",
        "viewType": "dropdown",
        "readOnly": false,
        "mandatory": true,
        "tooltip": "Choose the measure"
    }, {
        "code": "settings.s1_id",
        "label": "Dimension",
        "type": "params",
        "viewType": "dropdown",
        "readOnly": false,
        "mandatory": true,
        "tooltip": "Choose the Dimension"
    }]
}


```

where `m1_id` and `s1_id` in the last two chunks of code are the parameters id that will be used in the HTML file `index.htm`.



The previous example produces the following result:


<p align="center">
  <img width="500" src="https://github.com/AskdataHQ/askdata-docs/raw/gh-pages/docs/media/widget_properites.png">
</p>


Specifically the fields
```JSON 
"label": "Description"
```

```JSON 
"mandatory": true
```

```JSON 
"viewType": "dropdown"
```

are those circled in output with respectively blue, red and green colours.


## STEP 4: Copy the configuration file in the folder

In the same folder `/widgets/askdata/<unique_code>/` where you copied the `index.htm`, add the json file name `configuration.json`.

## STEP 5: Publish on `catalog.json`

In the folder [`/widgets/`] update the pre-existing file [`catalog.json`] with four **mandatory** fields:
+ **Code**: is the **<unique_code>** of the widget
+ **Name**: is the name visualized on the widget selector;
+ **Icon** is the path of the image preview:
+ **Description**: a short description of the widget.


For instance, the following chunk of code gives the result in the next screen of the *Widget selector*:

```JSON

...
{"code": "card-with-3-measure",
"name": "Card with 3 measure",
"icon": "_lib/icons/test.png",
"description": "Card with 3 KPIs"}
...

```

<p align="center">
  <img width="500" src="https://github.com/AskdataHQ/askdata-docs/raw/gh-pages/docs/media/screen_widget_selector.png">
</p>




## STEP 6: Check on DEV, promote on QA and finally on PROD

Once everything is correctly set, from Github the widget will be automatically updated on [**DEV**]. From here, if the widget works as you expecting you can ask an issue through Github for a promotion of the widget in [**QA**].

Finally, once tested in **QA** you can do open another issue in order to deploy the widget on [**PROD**]!


[Github repositoy]: <https://github.com/AskdataHQ/askdata-charts-components/tree/main/widgets/askdata>
[`/widgets/askdata/`]: <https://github.com/AskdataHQ/askdata-charts-components/tree/main/widgets/askdata>
[`widget_example`]: <https://github.com/AskdataHQ/askdata-charts-components/tree/main/widgets/askdata/_widget_example>
[guide example for creating a HTML widget]: </docs/widget_creation_example_of_html>
[`/widgets/`]: <https://github.com/AskdataHQ/askdata-charts-components/tree/main/widgets>
[`catalog.json`]: <https://github.com/AskdataHQ/askdata-charts-components/blob/main/widgets/catalog.json>
[**DEV**]: <https://app-dev.askdata.com/>
[**QA**]: <http://app-qa.askdata.com/>
[**PROD**]: <http://app.askdata.com/>

{% include links.html %}
