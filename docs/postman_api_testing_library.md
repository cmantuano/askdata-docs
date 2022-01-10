---
title: Testing Library
keywords: documentation
last_updated: October 15th, 2020
tags: [admin-guide]
sidebar: mydoc_sidebar
layout: doc

---

### Postman API Test Library

```
var jsonData = pm.response.json();

eval(pm.environment.get('loadLibrary'))
checkCard()
checkTable()
checkTable_single_row()
checkTable_single_column()
checkColumn('sales value usd (cy)')
checkTable_multiple_rows()

```
