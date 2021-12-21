---
title: AI Task Summarization (English)
keywords: documentation
last_updated: December 1st, 2021
tags: [admin-guide]
sidebar: mydoc_sidebar
layout: doc
---

The Summarization (English) Task is a workflow that generates automatically summaries for documents using proprietarly AI-driven NLP summarization model. 
Get in touch with the Askdata team if you want to bind a custom model.


# About the task #

The workflow requires as input:
- **dataset** (*mandatory*)
- **column_name**: name of a column of the given dataset (*mandatory*)
- **output_column_name**: name of the target column where summaries will be stored (*optional*)

The summarization is done with a T5-base based model. 
Thus, The workflow returns as output a new dataset with the selected **column_name** and the **output_column_name** if specified, **Summarized Text** otherwise.

# Example of usage #

Given the dataset below with some english documents and as **column_name** the *Content* column:

|ID|Content|
|--|-------------|
|0 |I live in a house near the mountains. I have two brothers and one sister, and I was born last. My father teaches mathematics, and my mother is a nurse at a big hospital. My brothers are very smart and work hard in school. My sister is a nervous girl, but she is very kind. My grandmother also lives with us. She came from Italy when I was two years old. She has grown old, but she is still very strong. She cooks the best food! My family is very important to me. We do lots of things together. My brothers and I like to go on long walks in the mountains. My sister likes to cook with my grandmother. On the weekends we all play board games together. We laugh and always have a good time. I love my family very much.|
|1 |First, I wake up. Then, I get dressed. I walk to school. I do not ride a bike. I do not ride the bus. I like to go to school. It rains. I do not like rain. I eat lunch. I eat a sandwich and an apple. I play outside. I like to play. I read a book. I like to read books. I walk home. I do not like walking home. My mother cooks soup for dinner. The soup is hot. Then, I go to bed. I do not like to go to bed.|

The default output, thus without setting **output_column_name**, is:

|ID|Content|Summarized Text|
|--|-|-|
|0 |I live in a house near the mountains. I have two brothers and one sister, and I was born last. My father teaches mathematics, and my mother is a nurse at a big hospital. My brothers are very smart and work hard in school. My sister is a nervous girl, but she is very kind. My grandmother also lives with us. She came from Italy when I was two years old. She has grown old, but she is still very strong. She cooks the best food! My family is very important to me. We do lots of things together. My brothers and I like to go on long walks in the mountains. My sister likes to cook with my grandmother. On the weekends we all play board games together. We laugh and always have a good time. I love my family very much.|my family is very important to me. we do lots of things together. on the weekends we all play board games together.|
|1 |First, I wake up. Then, I get dressed. I walk to school. I do not ride a bike. I do not ride the bus. I like to go to school. It rains. I do not like rain. I eat lunch. I eat a sandwich and an apple. I play outside. I like to play. I read a book. I like to read books. I walk home. I do not like walking home. My mother cooks soup for dinner. The soup is hot. Then, I go to bed. I do not like to go to bed.|my mother cooks soup for dinner. The soup is hot. I do not like to go to bed.|

Otherwise, setting **output_column_name** as *Summary*, we have:

|ID|Content|Summary|
|--|-|-|
|0 |I live in a house near the mountains. I have two brothers and one sister, and I was born last. My father teaches mathematics, and my mother is a nurse at a big hospital. My brothers are very smart and work hard in school. My sister is a nervous girl, but she is very kind. My grandmother also lives with us. She came from Italy when I was two years old. She has grown old, but she is still very strong. She cooks the best food! My family is very important to me. We do lots of things together. My brothers and I like to go on long walks in the mountains. My sister likes to cook with my grandmother. On the weekends we all play board games together. We laugh and always have a good time. I love my family very much.|my family is very important to me. we do lots of things together. on the weekends we all play board games together.|
|1 |First, I wake up. Then, I get dressed. I walk to school. I do not ride a bike. I do not ride the bus. I like to go to school. It rains. I do not like rain. I eat lunch. I eat a sandwich and an apple. I play outside. I like to play. I read a book. I like to read books. I walk home. I do not like walking home. My mother cooks soup for dinner. The soup is hot. Then, I go to bed. I do not like to go to bed.|my mother cooks soup for dinner. The soup is hot. I do not like to go to bed.|

{% include links.html %}
