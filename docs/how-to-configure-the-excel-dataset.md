---
title: How to Configure the Excel Dataset
keywords: documentation
last_updated: February 15th, 2021
tags: [admin-guide]
sidebar: mydoc_sidebar
layout: doc
---

## Excel Integration

When you add a new Excel dataset you need to provide the file. The procedure will import of the first sheet of the Excel file, do not import format different the tabular data.

### How to avoid importing errors
- Avoid using ' and / and \ in the columns name

### Custom measures and dimensions
The integration use DuckDB SQL dialect in order to define custom expression.
The alias of the columns should be applied with double quote "" while '' for string.

#### Custom Measure
```
SUM("sales") - SUM("profit")
```
#### Custom Dimension
Eg of custim dimension: 
```
case when "AREA_GEOGRAFICA" IN ('North-est', 'North-west') then 'NORTH' else 'OTHER REGION' end
```
