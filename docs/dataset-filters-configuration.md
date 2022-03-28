---
title: Dataset Filters - Advanced Configuration
keywords: documentation
last_updated: April 06th, 2021
tags: [admin-guide]
sidebar: mydoc_sidebar
layout: doc
---

## Dataset: **Rules**

**Rules** tab provides examples of advanced dataset configuration deploying a business logic rule to a dataset:

### Sorting rules

In this example, we provide the instructions for sorting the results of the query
```javascript
[
{
   "when" : "!query.isSorted()",
   "order" : "PRICE" 
},
{
   "when" : "!query.isSortedByMeasure()",
   "order" : "PRICE ASC" 
},
{
   "when" : "!query.isSortedByDimension()",
   "order" : "PLACE DESC" 
},
{
   "when" : "!query.isSortedBy('place')",
   "order" : "PRICE DESC, PLACE ASC" 
},
{
   "when" : "query.hasAnyEntity('YEAR')", 
   "order" : "YEAR DESC" 
}
]
```
### Filters

Filters are powerful tools that can be used to restrict access to some data. For example if you are a manager in a company and would like one of your employees to access just the data that is related to himself, you could achieve that by defining a simple filter as in the picture:

<p align="center">
  <img src="media/filters-example.PNG" width="650" />
</p>

```javascript
[
{
   "when": "user.details.division",
   "then": "CUSTOMER_DIVISION = '{{user.details.division}}' OR CUSTOMER_REGION = '{{user.details.region}}'",
   "type" : "EXPR" 
}
]
```

For example in the above use case we are specifying that if the user login email is *employee@yourcompany.com* then just show him the records where *name=John* and *surname=Doe*. This obviously is a rather simple example of the definition of a filter, more complex ones can be build in order to guarantee the proper flexibility to your dataset. If you would like to have a deeper overview of filters you can watch (this resource)[filters]

**Example with user defined security:**

This is an example of an advanced filter that could be applied to the dataset.

```javascript

[
    {
        "when": "(user.username == "myuser@mymail.com2") && (user.details.user_type != null)",
        "then": "CASE WHEN '{{user.details.user_type}}' <> 'DIR' THEN AGENZIA IN ( SELECT agenzia_cod FROM VIEW_USERS WHERE user_id = '{{user.details.custom_id}}') WHEN '{{user.details.user_type}}' = 'DIR' THEN 1=1 ELSE 1 <> 1 END"
    }
]

```

This filter is triggered when the conditions specified in the when clause are met.

**Example with default time filter taking the highest year available as default **

This is an example of an advanced filter that is applied to the dataset to automatically filter by the latest available year - when not specified in the user query

```javascript


[
    {
        "when": "!query.hasAnyEntity('year')",
        "then": "\"YEAR\" = (SELECT MAX(YEAR) FROM NAME_OF_MY_TABLE )",
        "type": "EXPR"
    }
]

```


### ChangeQuery
Another feature is the ability to update the query that is running.
Let's consider the following example and discover how it's simple to add some behavior by adding *changeQuery* property.
```
[
   {
      "when" : "query.hasAnyEntity('COUNTRY')", 
      "changeQuery" : {
         "addFields" : ["SALES"], 
         "addOrderBy" : ["SALES DESC"], 
   }
]
```
If the current query is asking for a COUNTRY then, we want add a new field like SALES that we think is useful for the end user and update the sorting by using SALES in DESC order.

Even, it's possibile to apply more complex filters like those that use values from another dataset (similarly to SQL subselect).
The next case will show how to execute a transient query in order to retrieve the entity YEAR from sales dataset sorted in DESC order and add the first value in a new filter of a user query.
```
[
   {
      "when" : "query.hasAnyEntity('SALES')", 
      "changeQuery" : {
         "addFilters" : [ "YEAR IN '{{my_date.0.YEAR}}'" ], 
         "let" : {
            "my_date" : {
               "fields" : [ "YEAR" ], 
               "orderBy" : [ "YEAR DESC" ], 
               "dataset" : "sales_dataset"
            }
         }
      }
   }
]
```

This is possible by ```let``` tag that holds the data that comes from a new transient query. 
In particular:
```
    "let" : {
            "my_date" : {
               "fields" : [ "YEAR" ], 
               "orderBy" : [ "YEAR DESC" ], 
               "dataset" : "sales_dataset"
            }
   }
```
"my_date" is a name that users can choose to significantly assign to the data that the sub-query will return. 
Please note that the use of this name is to address the data into the template used in addFilters tag.
```
 "addFilters" : [ "YEAR IN '{{my_date.0.YEAR}}'" ], 
```
_{{my_date.0.YEAR}}_ means "use the value of YEAR contained in the first row of resultset"
| YEAR    | 
|:-------:|
| _2022_  |
| 2021    |
| 2020    |


Other fields are:
- _fields_, is the list of wanted fields. It's possible to use aggregation functions like MAX YEAR for example.
- _orderBy_, is the list of sorting 
- _dataset_, is the *slug* od dataset on which to execute the query. 

Hence, the final query will have "YEAR IN 2022".

ChangeQuery provides the possibility to add charts to the resulting card too. The only need is to add the type of wanted chart, like in the example.
```[
   {
      "when" : "query.hasAnyEntity('SALES')", 
      "changeQuery" : {
          "addChart" : [ "donut" ]
      }
   }
]
```
The possible chart types are:
- HORIZONTAL_BAR,
- LINE,
- PIE,
- RADAR,
- DONUT,
- VERTICAL_BAR,
- STACKED_AREA,
- STACKED_HORIZONTAL,
- STACKED_VERTICAL
 

 All these capabilities are usable together.

