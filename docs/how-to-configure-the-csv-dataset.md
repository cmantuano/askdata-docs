---
title: How to Configure the CSV Dataset
keywords: documentation
last_updated: October 15th, 2020
tags: [admin-guide]
sidebar: mydoc_sidebar
layout: doc

---

In order to create a new dataset you need to have a new workspace set up. If you don't have one already, follow this guide.

# Dataset Configuration

When you add a new CSV dataset you need to provide up to 4 settings in the configuration form.

### Econding:
UTF-8 is the modern way of encoding file and the standard for most products

### Separator:
Every CSV has a char that identify the separator. The default is usually the comma , or the semicolumn ; 

### Thousands Separator:
Some CSV could optionally show e separator of thousands. Default is None

### Special processing commands:
Python code that are run before loading the CSV that let the users to apply some clearning or transformation

### How to avoid importing errors
- Consider only tabular data with one level of header
- Avoid using special chars in the header
