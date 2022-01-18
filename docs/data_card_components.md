---
title: Data Card - Components
keywords: documentation
last_updated: December 12th, 2021
tags: [getting-started]
sidebar: mydoc_sidebar
layout: doc
---

### Definitions round-up

* A **Feed** is a list of Data Cards
* A **Data Card** is composed by an header and a body containing different components
* A **Component** is a single piece of a Data Card, it could be a chart, a table, a button

### Data Card Components:

Each **Data Card** is composed by modular components. Every component belongs to 2 main different categories:

#### Data Components

Components that retrieve data from datasets, transform data or provide data stored locally in the card to other components.

* Queries
* Search
* SQL Queries
* Data (static)
* Script

#### Visual Components

Components that visualize on output in the Data Card itself such as images or charts.

* Table
* Chart
* Button
* [HTML](docs/data_card_html_component)
* List
* Comparison
* Map
* Widget

It is possible to extend the available visual components creating a new Widget: [How to publish a new Widget](https://askdata.com/docs/how-to-publish-a-new-widget).
It's pretty fun giving back (contributing) to the community.

Technical specification of the data-card response: [/docs/data_card_technical_model](/docs/data_card_technical_model)
