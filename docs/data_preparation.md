---
title: Data preparation
keywords: documentation
tags: [learn-to-code]
sidebar: mydoc_sidebar
layout: doc
---

## Data Cleaning

it is important to be able to deal with messy data, whether that means missing values, inconsistent formatting, malformed records, or nonsensical outliers.

We’ll cover the following:

* Dropping unnecessary columns in a DataFrame
* Changing the index of a DataFrame
* detecting and removing na
* Renaming columns to a more recognizable set of labels


```python
#Load df from askdata, explicit way

username = "geyos65958@ergowiki.com"
password = "Password"

!pip install askdata

from askdata import Agent, Askdata


askdata = Askdata(username = username, password = password)
agent = askdata.agent("red_wine")
df = agent.load_dataset("red_wine")

to_drop = ['Quality']

df.drop(to_drop, axis=1).head(3)
```




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
      <th>fixed acidity</th>
      <th>volatile acidity</th>
      <th>citric acid</th>
      <th>residual sugar</th>
      <th>chlorides</th>
      <th>free sulfur dioxide</th>
      <th>total sulfur dioxide</th>
      <th>density</th>
      <th>pH</th>
      <th>sulphates</th>
      <th>alcohol</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>7.4</td>
      <td>0.70</td>
      <td>0.00</td>
      <td>1.9</td>
      <td>0.076</td>
      <td>11.0</td>
      <td>34.0</td>
      <td>0.9978</td>
      <td>3.51</td>
      <td>0.56</td>
      <td>9.4</td>
    </tr>
    <tr>
      <th>1</th>
      <td>7.8</td>
      <td>0.88</td>
      <td>0.00</td>
      <td>2.6</td>
      <td>0.098</td>
      <td>25.0</td>
      <td>67.0</td>
      <td>0.9968</td>
      <td>3.20</td>
      <td>0.68</td>
      <td>9.8</td>
    </tr>
    <tr>
      <th>2</th>
      <td>7.8</td>
      <td>0.76</td>
      <td>0.04</td>
      <td>2.3</td>
      <td>0.092</td>
      <td>15.0</td>
      <td>54.0</td>
      <td>0.9970</td>
      <td>3.26</td>
      <td>0.65</td>
      <td>9.8</td>
    </tr>
  </tbody>
</table>
</div>




```python
## Indexing

# Unlike primary keys in SQL, a Pandas Index doesn’t make any guarantee of being unique, 
# although many indexing and merging operations will notice a speedup in runtime if it is.
# It enhances slicing and labeling

#Often you need to take into account the index of a given row... For example:

df1 = df[df["quality"]!=5]
# df1 = df[df["quality"]==5].reset_index(drop=True)

df1
```




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
      <th>fixed acidity</th>
      <th>volatile acidity</th>
      <th>citric acid</th>
      <th>residual sugar</th>
      <th>chlorides</th>
      <th>free sulfur dioxide</th>
      <th>total sulfur dioxide</th>
      <th>density</th>
      <th>pH</th>
      <th>sulphates</th>
      <th>alcohol</th>
      <th>quality</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>11.2</td>
      <td>0.28</td>
      <td>0.56</td>
      <td>1.9</td>
      <td>0.075</td>
      <td>17.0</td>
      <td>60.0</td>
      <td>0.99800</td>
      <td>3.16</td>
      <td>0.58</td>
      <td>9.8</td>
      <td>6</td>
    </tr>
    <tr>
      <th>1</th>
      <td>7.3</td>
      <td>0.65</td>
      <td>0.00</td>
      <td>1.2</td>
      <td>0.065</td>
      <td>15.0</td>
      <td>21.0</td>
      <td>0.99460</td>
      <td>3.39</td>
      <td>0.47</td>
      <td>10.0</td>
      <td>7</td>
    </tr>
    <tr>
      <th>2</th>
      <td>7.8</td>
      <td>0.58</td>
      <td>0.02</td>
      <td>2.0</td>
      <td>0.073</td>
      <td>9.0</td>
      <td>18.0</td>
      <td>0.99680</td>
      <td>3.36</td>
      <td>0.57</td>
      <td>9.5</td>
      <td>7</td>
    </tr>
    <tr>
      <th>3</th>
      <td>8.5</td>
      <td>0.28</td>
      <td>0.56</td>
      <td>1.8</td>
      <td>0.092</td>
      <td>35.0</td>
      <td>103.0</td>
      <td>0.99690</td>
      <td>3.30</td>
      <td>0.75</td>
      <td>10.5</td>
      <td>7</td>
    </tr>
    <tr>
      <th>4</th>
      <td>7.4</td>
      <td>0.59</td>
      <td>0.08</td>
      <td>4.4</td>
      <td>0.086</td>
      <td>6.0</td>
      <td>29.0</td>
      <td>0.99740</td>
      <td>3.38</td>
      <td>0.50</td>
      <td>9.0</td>
      <td>4</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>913</th>
      <td>6.3</td>
      <td>0.51</td>
      <td>0.13</td>
      <td>2.3</td>
      <td>0.076</td>
      <td>29.0</td>
      <td>40.0</td>
      <td>0.99574</td>
      <td>3.42</td>
      <td>0.75</td>
      <td>11.0</td>
      <td>6</td>
    </tr>
    <tr>
      <th>914</th>
      <td>6.8</td>
      <td>0.62</td>
      <td>0.08</td>
      <td>1.9</td>
      <td>0.068</td>
      <td>28.0</td>
      <td>38.0</td>
      <td>0.99651</td>
      <td>3.42</td>
      <td>0.82</td>
      <td>9.5</td>
      <td>6</td>
    </tr>
    <tr>
      <th>915</th>
      <td>5.9</td>
      <td>0.55</td>
      <td>0.10</td>
      <td>2.2</td>
      <td>0.062</td>
      <td>39.0</td>
      <td>51.0</td>
      <td>0.99512</td>
      <td>3.52</td>
      <td>0.76</td>
      <td>11.2</td>
      <td>6</td>
    </tr>
    <tr>
      <th>916</th>
      <td>6.3</td>
      <td>0.51</td>
      <td>0.13</td>
      <td>2.3</td>
      <td>0.076</td>
      <td>29.0</td>
      <td>40.0</td>
      <td>0.99574</td>
      <td>3.42</td>
      <td>0.75</td>
      <td>11.0</td>
      <td>6</td>
    </tr>
    <tr>
      <th>917</th>
      <td>6.0</td>
      <td>0.31</td>
      <td>0.47</td>
      <td>3.6</td>
      <td>0.067</td>
      <td>18.0</td>
      <td>42.0</td>
      <td>0.99549</td>
      <td>3.39</td>
      <td>0.66</td>
      <td>11.0</td>
      <td>6</td>
    </tr>
  </tbody>
</table>
<p>918 rows × 12 columns</p>
</div>




```python
# NAs are nusually not useful when handling data, for this reason you have to identify them and remove them

df = pd.read_csv("wine-red.csv", sep=";")
df.isna().sum()
df.loc[len(df)] = ["32", "2", "2", "32", "1", "1", "1", "1", "1", "2", None, "4"]
# df = df.dropna()
```


```python
# if you need to replace the name of a column 

osservatorio_data.rename(columns = {'quality':'Wine quality'}, inplace = True)
```

## Detect Outliers

Outliers need a special mention in this section. In statistics, an outlier is an observation point that is distant from other observations. We are not going to cover this since I think some kind of theoretical knowledge is required but keep in mind that this is really important when analyzing data.

## Lambda functions

A **lambda function** is just like any normal python function, except that it has no name when defining it, and it is contained in one line of code. A lambda function evaluates an expression for a given argument. You give the function a value (argument) and then provide the operation (expression). The keyword lambda must come first. A full colon (:) separates the argument and the expression.



```python
#Normal python function
def a_name(x):
    return x+x

#Lambda function
lambda x: x+x
```


**Pros**

* Good for simple logical operations that are easy to understand. This makes the code more readable too.
* Good when you want a function that you will use just one time.

**Cons**
* They can only perform one expression. It’s not possible to have multiple independent operations in one lambda function.
* Bad for operations that would span more than one line in a normal def function (For example nested conditional operations). If you need a minute or two to understand the code, use a named function instead.
* Bad because you can’t write a doc-string to explain all the inputs, operations, and outputs as you would in a normal def function.




```python
(lambda x: x*2)(25)
```




    50




```python
## Lambda function with filter
# This is a Python inbuilt library that returns only those values that fit certain criteria. 

list_1 = [1,2,3,4,5,6,7,8,9]
list(filter(lambda x: x%2==0, list_1))
```




    [2, 4, 6, 8]




```python
## Lambda function with map
# This returns a modified list where every value in the original list has been changed based on a function.

list_1 = [1,2,3,4,5,6,7,8,9]
cubed = map(lambda x: pow(x,3), list_1)
list(cubed)
```




    [1, 8, 27, 64, 125, 216, 343, 512, 729]



### Exercises

a) Write a Python program to create a lambda function that adds 15 to a given number passed in as an argument, also create a lambda function that multiplies argument x with argument y and print the result.

b) given this list nums = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]  filter a list of integers using Lambda.


```python
# r = lambda a : a + 15
# print(r(10))
# r = lambda x, y : x * y
# print(r(12, 4))

# nums = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
# print("Original list of integers:")
# print(nums)
# print("\nEven numbers from the said list:")
# even_nums = list(filter(lambda x: x%2 == 0, nums))
# print(even_nums)
```

[![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1A0qGwLr3R9iFJpPaFWv8OAKtdlPz1Vym?usp=sharing)