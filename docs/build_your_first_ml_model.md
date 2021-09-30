---
title: Your first machine learning algorithm
keywords: documentation
tags: [learn-to-code]
sidebar: mydoc_sidebar
layout: doc
---
## Build the Model

Remember that the final goal is always to discover and exploit the information that is hidden in the data. For this reason, since we have cleaned our data and checked that everything is in place we are going to build our first (super basic) machine learning model. The simplest option is the **linear regression**, you can' t call yourself an acknowledged person in the Big Data world if you do not know what linear regression is. For this reason, I am going to provide a little bit of context here:

Linear regression attempts to model the relationship between two variables by fitting a linear equation to observed data. One variable is considered to be an explanatory variable, and the other is considered to be a dependent variable. For example, a modeler might want to relate the weights of individuals to their heights using a linear regression model.


<p align="center">
  <img src="https://miro.medium.com/max/1400/1*dG6m4wnx3ARPtZPd8qf1tQ.gif"/>
</p>

The equation of the line is:
Y = a + bX, where X is the explanatory variable and Y is the dependent variable. The slope of the line is b, and a is the intercept (the value of y when x = 0).


```python
import numpy as np
from sklearn.linear_model import LinearRegression
```


```python
##Load Dataset via Askdata

username = "geyos65958@ergowiki.com"
password = "Password"

!pip install askdata

from askdata import Agent, Askdata


askdata = Askdata(username = username, password = password)
agent = askdata.agent("red_wine")
df = agent.load_dataset("red_wine")

#IGNORE THIS
df1 = df.pop('alcohol') # remove column b and store it in df1
df['alcohol']=df1 


X = df.iloc[:,:-1]
y = df.iloc[:,-1:]

```


```python
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.33, random_state=42)
```


```python
reg = LinearRegression().fit(X_train, y_train)

reg.intercept_
reg.coef_

reg.score(X_test, y_test) #Returns R^2..not that bad
```




    0.7016255861966023



## Integration with Askdata

Our mission is to make data accessible and useful to everyone.

AskData empowers people to interact with data in the most natural way: through natural language.


```python
#  Please use the following credentials to login to the platform

# username: fosic56191@ppp998.com
# password: Luiss1234!
```


```python
!pip install askdata
```


```python
from askdata import Askdata

askdata = Askdata()
agent_name = "titanic"
```

    Askdata Username: fosic56191@ppp998.com
    Askdata Password: ··········



```python
# Query askdata

askdata.get(query="sopravvissuti per classe", workspace = agent_name)
```


<p>Pclass , Survived from the dataset: titanic / Titanic_passengers</p>





<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Pclass</th>
      <th>Survived</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>136</td>
    </tr>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>119</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>87</td>
    </tr>
  </tbody>
</table>
</div>




```python
# or you can load the entire dataframe
agent = askdata.agent(agent_name)
df = agent.load_dataset("titanic_passengers")
df
```

## Exercises

Given the titanic dataset

| Variable      | Definition | Key |
| ----------- | ----------- |      |
| survival      | Survival   | 0 = No, 1 = Yes  |
| pclass   | Ticket class| 1 = 1st, 2 = 2nd, 3 = 3rd |
| sex   | Sex        |  |
| Age  | Age in years     |  |
| sibsp   | # of siblings / spouses aboard the Titanic       |  |
| parch   | # of parents / children aboard the Titanic |  |
| ticket   | Ticket number	   |  |
| fare   | Passenger fare	       |  |
| cabin   | 	Cabin number        |  |
| embarked   | Port of Embarkation	        | C = Cherbourg, Q = Queenstown, S = Southampton |


**Tasks**

a) load the dataset from askdata

b) Are there any Nan values? if Yes, please remove them since they are not relevant for the analysis.

c) print some useful information about the dataset. For example, The distribution of Survived w.r.t. Ticket class

d) Build a Logistic Regression model. 
(hint: clf = LogisticRegression(random_state=0).fit(X_train, y_train)

e) are you happy with the results? 




```python
from askdata import Askdata

askdata = Askdata()
agent_name = "titanic"
```

    Askdata Username: fosic56191@ppp998.com
    Askdata Password: ··········



```python
agent = askdata.agent(agent_name)
df = agent.load_dataset("titanic_passengers")
```

    [askdata_client.py:422 -  get_dataset_by_slug() ] - 2021-09-18 10:16:02,090 --> AUTH URL https://api.askdata.com/smartbot/agents/agentslug/titanic/datasetslug/titanic_passengers
    [askdata_client.py:309 -        _load_dataset() ] - 2021-09-18 10:16:02,731 --> AUTH URL https://api.askdata.com/smartdataset/datasets/a570f020-e2f1-44d3-85a1-106ee5921d22-CSV-80ffa4f0-cb0a-47e5-8677-7c99839d3f40/grid/data



```python
df.iloc[0,10]
df.isna().sum()
```




    ''




```python
import matplotlib.pyplot as plt


### Bar plot

# create a figure and axis 
# fig, ax = plt.subplots() 
# # count the occurrence of each class 
# data =df[df["Survived"]=="1"].groupby(["Pclass"]).count()["Survived"]
# # get x and y data 
# points = data.index 
# frequency = data.values 
# # create bar chart 
# ax.bar(points, frequency) 
# # set title and labels 
# ax.set_title('Titanic data') 
# ax.set_xlabel('Survivors') 
# ax.set_ylabel('Frequency')
# fig.show()
```




```python
df = agent.load_dataset("titanic_passengers")

## Handling Categorical Data in Python
## https://www.datacamp.com/community/tutorials/categorical-data Sezione Encoding Categorical Data

df1 = df[["Survived", "Pclass", "Age", "Sibsp", "Parch"]]

df1 = df1.replace(['N/A'], 28)


X = df1.iloc[:,:]
y = df1["Survived"]
del X["Survived"]

```

    [askdata_client.py:422 -  get_dataset_by_slug() ] - 2021-09-18 10:39:14,839 --> AUTH URL https://api.askdata.com/smartbot/agents/agentslug/titanic/datasetslug/titanic_passengers
    [askdata_client.py:309 -        _load_dataset() ] - 2021-09-18 10:39:15,529 --> AUTH URL https://api.askdata.com/smartdataset/datasets/a570f020-e2f1-44d3-85a1-106ee5921d22-CSV-80ffa4f0-cb0a-47e5-8677-7c99839d3f40/grid/data



```python
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.33, random_state=42)
```


```python
from sklearn.linear_model import LogisticRegression

reg = LogisticRegression(random_state=0).fit(X_train, y_train)

reg.intercept_
reg.coef_

reg.score(X_test, y_test) #Returns R^2..not that bad
```




    0.7322033898305085




```python
reg.predict(X_test)[0:10]
```


```python
df.groupby(["Pclass","Survived"]).size()
```




    Pclass  Survived
    1       0            80
            1           136
    2       0            97
            1            87
    3       0           372
            1           119
    dtype: int64



[![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/17TA0MoPhE75e9hczSTO7Kp1IGZ_kjkbe?usp=sharing)