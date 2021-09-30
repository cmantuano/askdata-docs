---
title: Data Visualization
keywords: documentation
tags: [learn-to-code]
sidebar: mydoc_sidebar
layout: doc
---


Data visualization is the discipline of trying to understand data by placing it in a visual context so that patterns, trends and correlations that might not otherwise be detected can be exposed. Python offers multiple great graphing libraries that come packed with lots of different features.

Matplotlib is one of the most used libraries: is a comprehensive library for creating static, animated, and interactive visualizations in Python.


```python
##Load Dataset via Askdata

username = "geyos65958@ergowiki.com"
password = "Password"

!pip install askdata

from askdata import Agent, Askdata


askdata = Askdata(username = username, password = password)
agent = askdata.agent("red_wine")
df = agent.load_dataset("red_wine")
```

## Scatter Plot

To create a scatter plot in Matplotlib we can use the scatter method. We will also create a figure and an axis using plt.subplots so we can give our plot a title and labels.


```python

import matplotlib.pyplot as plt

# create a figure and axis

fig, ax = plt.subplots()

ax.scatter(df['Quality'], df['Ph'])
# set a title and labels
# ax.set_title('Red wine Dataset')
# ax.set_xlabel('Quality')
# ax.set_ylabel('pH')
fig.show()
```
<img src="https://s3.eu-central-1.amazonaws.com/innaas.smartfeed/icons/python_course1.png"
     alt="Markdown Monster icon"/>

     
Data visualization is often crucial if you want to transmit someone a message. For this reason, it is always reccomended investing your time in this activity. When I am in need of fancy graphs, I always visit [this website](https://www.python-graph-gallery.com/) which offers a huge variety of graphs with ready to use code snippets. 

## Bar Chart

```python
### Bar plot

# create a figure and axis 
fig, ax = plt.subplots() 
# count the occurrence of each class 
data = df['Quality'].value_counts() 
# get x and y data 
points = data.index 
frequency = data.values 
# create bar chart 
ax.bar(points, frequency) 
# set title and labels 
ax.set_title('Wine Review Quality') 
ax.set_xlabel('Points') 
ax.set_ylabel('Frequency')
fig.show()
```

<img src="https://s3.eu-central-1.amazonaws.com/innaas.smartfeed/icons/python_course2.png"
     alt="Markdown Monster icon" />


## Correlation

Correlation, in the finance and investment industries, is a statistic that measures the degree to which two securities move in relation to each other. Its value must fall between -1.0 and +1.0.Since correlation is really important in ML algorithms, we can analyze it:


```python
f = plt.figure(figsize=(19, 15))
plt.matshow(df.corr(), fignum=f.number)
plt.xticks(range(df.select_dtypes(['number']).shape[1]), df.select_dtypes(['number']).columns, fontsize=14, rotation=45)
plt.yticks(range(df.select_dtypes(['number']).shape[1]), df.select_dtypes(['number']).columns, fontsize=14)
cb = plt.colorbar()
cb.ax.tick_params(labelsize=14)
plt.title('Correlation Matrix', fontsize=16);
```

<img src="https://s3.eu-central-1.amazonaws.com/innaas.smartfeed/icons/python_course3.png"
     alt="Markdown Monster icon" />

Why is correlation important?

Multicollinearity refers to a situation in which more than two explanatory variables in a multiple regression model are highly linearly related. This correlation is a problem because independent variables should be independent. If the degree of correlation between variables is high enough, it can cause problems when you fit the model and interpret the results.


[![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1mGnG1dsDVe4fqSiMPvIBOVxTcZ0r3BuK?usp=sharing)