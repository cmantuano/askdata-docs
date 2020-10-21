---
title: Askdata and MicroStrategy - REST API integration
keywords: documentation
last_updated: October 15th, 2020
tags: [getting_started]
sidebar: mydoc_sidebar
layout: docs
---

Askdata relies on the MicroStrategy REST API framework to integrate Askdata seamlessly.

The MicroStrategy REST API is a RESTful application that uses HTTP requests such as POST, GET, and DELETE. It is designed to help developers build data-driven client applications quickly and easily. 

It does this by providing light-weight JSON data that is easy to consume because it includes raw data without direct formatting. Developers can use the MicroStrategy REST API programmatically in their own code.  


**Pros:**


* Fast integration
* Data is always updated in line with the MicroStrategy cubes

**Cons:**


* This integration pattern requires the MicroStrategy REST API license module
* Not all aggregation functions are supported due to limited aggregation support available on the MicroStrategy REST API framework

There is an alternative way of integrating MicroStrategy as a datasource though the schedule data batch process: [batch data integration](/docs/microstrategy-batch-integration)



    {% include links.html %}

    