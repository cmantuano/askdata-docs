---
title: How to Configure the CSV Dataset
keywords: documentation
last_updated: October 15th, 2020
tags: [admin-guide]
sidebar: mydoc_sidebar
layout: doc

---
## CSV Integration 

To add CSV Dataset:

1. Choose Excel Dataset type from the list:

<img src="/media/admin-guide/csv_1.png" class="image-doc p-3">

2. Click on the **Connection** button

<img src="/media/admin-guide/csv_2.png" class="image-doc p-3">

3. Choose and upload **CSV** **file** from your computer

4. Select **Encoding** and **Separator**

UTF-8 is the modern way of encoding file and the standard for most products. Every CSV has a char that identify the separator. The default is usually the comma , or the semicolumn ; Some CSV could optionally show e separator of thousands. Default is None.

4. Click **Save** to proceed

<img src="/media/admin-guide/csv_3.png" class="image-doc p-3">

Once Dataset is added you will see a successful message:

<img src="/media/admin-guide/csv_4.png" class="image-doc p-3">

5. Click on **Pen** close to CSV icon to rename Dataset and Slug name (Dataset name written in small letters with underscores)

### Special processing commands:
Python code that are run before loading the CSV that let the users to apply some cleaning or transformation

### How to avoid importing errors
- Consider only tabular data with one level of header
- Avoid using special chars in the header
