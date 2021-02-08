---
title: How configure dataset filters
keywords: documentation
last_updated: February 1st, 2021
tags: [admin-guide]
sidebar: mydoc_sidebar
layout: doc

---

## Dataset Filter Configuration:

From the *Agent* page click on *Datasets*.

Open the specific dataset you want to configure.

Click on the "Filter" section


{% include links.html %}

User can define one or more filters. The filters are evaluated in sequence on each user query (ask)

A filter has the following structure

    {
        "when": <a condition>
        "then" : <the filter expression>
        "order" : <the order by expression>
        "type" : <type of filter (Null|EXPR)>
    }

### WHEN
The condition is a logical expression of Dimensions and Measures in the dataset. The filter is tested on each user query and, if the condition is meet, the filter is applyed.
To define the condition, there are some predefined function: 

* *query.hasEntity('e1', 'e2', ..., 'en')* the condition is meet if all the Entities in the list are presente in the user query
* *query.hasAnyEntity('e1', 'e2', ... 'en')* the condition is meet if at least one Entities in the list is meet
* *query.hasMeasure('m1','m2', ..., 'mn')* the condition is meet if all the Measure in the list are presente in the user query
* *query.hasAnyMeasure('m1','m2', ..., 'mn')* the condition is meet if at least one Measure in the list is meet
* *query.hasEntityFilter()* __TBD__
* *query.hasAnyEntityFilter()* __TBD__

The User can combine one or more simple conditions into a complex one, eg:

    "when" : "query.hasEntity('date') && query.hasMeasure('qty_stocked')" 
this condition is meet when the user asks a query like *"give me the quantity stocked by product in the last month"*. quantity stocked is 'qty_stocked' and last month is 'date'

    "when" : "!query.hasEntity('data')" 
the condition is meet when the user asks a query like: *"give me quantity stocket"* in this user query no 'date' is specified

### THEN
If the When condition is meet the filter is applyed. The "then" section contains the filter definition, a filter is like the WHERE condition in a SQL query.
So, according with the previous examples, the user can specify eg.:
    
    "then" : "QTY_STOCKED NOT NULL" this filter exclude from the result the NULL value
    "then" : "DATE = '2020-02-01'" this filter specify a date

A filter value can be defined at run-time. In this case the user must specify that the "then" condition is an expression ("type" : "EXPR"). 
the previous example is modified in:

    "then" : "DATE" = "(SELECT MAX(DATE) FROM <table_name>)"
    "type" : "EXPR"

### ORDER
If the condition is meet the order section is applyed. The "order" section contain a condition similar to the ORDER BY in the SQL Query
According with the previous examples, the user can specigy eg.:

    "order" : "AVG(QTY_STOCKED) DESC"

A complete example for a dataset filter 

    [
        {
            "when" : "query.hasEntity('date') && query.hasMeasure('qty_stocked')",
            "then" : "QTY_STOCKED NOT NULL",
            "order" : "AVG(QTY_STOCKED) DESC",
            "type" : null
        },
        {
            "when" : "!query.hasEntity('data')",
            "then" : "\"DATE\"" = (SELECT MAX(DATE) FROM <table_name>)",
            "order" : "",
            "type" : "EXPR"
        }
    ]
