---
title: Pandas Tutorial
keywords: documentation
tags: [learn-to-code]
sidebar: mydoc_sidebar
layout: doc
---

## Pandas Basics

<p align="center">
  <img src="https://miro.medium.com/max/798/1*93CVLqnQESmvfOhzvYUgQw.png"/>
</p>



Pandas is a fast, powerful, flexible and easy to use open source data analysis and manipulation tool,
built on top of the Python programming language. By far, the most used python library to handle dataframes. 

Scope of Data Science: clean, analyze your data and build models with it. Final objective is to **derive insight **and retrieve useful information.

Personally speaking, if you will ever face a large dataset (>1.000.000 records) I advise you to use Modin that will speed up your operations.



```python
# !pip install pandas
```


```python
import pandas as pd
# print(pd.__version__)

#Explicit definition of a dataframe

mydataset = {
  'cars': ["BMW", "Volvo", "Ford", "Tesla"],
  'Country': ["Italy", "Spain", "Italy", "Italy"],
  'sales': [3, 7, 2, 1]
}

df_cars = pd.DataFrame(mydataset)

df_cars.head(3)
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
      <th>cars</th>
      <th>Country</th>
      <th>sales</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>BMW</td>
      <td>Italy</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Volvo</td>
      <td>Spain</td>
      <td>7</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Ford</td>
      <td>Italy</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Alternatively, a dataframe can also be created from lists


auto = ["BMW", "Volvo", "Ford", "Tesla"]
sales =  [3, 7, 2, 1]
country = ["Italy", "Spain", "Italy", "Italy"]
  
# Calling DataFrame constructor after zipping
# both lists, with columns specified
df = pd.DataFrame(list(zip(auto, country, sales)),
               columns =['Auto', "Nazione", "Vendite"])
df
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
      <th>Auto</th>
      <th>Nazione</th>
      <th>Vendite</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>BMW</td>
      <td>Italy</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Volvo</td>
      <td>Spain</td>
      <td>7</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Ford</td>
      <td>Italy</td>
      <td>2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Tesla</td>
      <td>Italy</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Load df from askdata, explicit way

username = "geyos65958@ergowiki.com"
password = "Password"

!pip install askdata
from askdata import Agent, Askdata


askdata = Askdata(username = username, password = password)
agent = askdata.agent("red_wine")
df = agent.load_dataset("red_wine")
```


```python
# red
# red.head(5)
# red.info()
#red.columns()
# red.dtypes
```

### Create a new column or delete an existing one


```python
df["total acidity"] = df["fixed acidity"] + df["volatile acidity"]
# del df["total acidity"]
df.drop(columns = ["total acidity"]).head(3)
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
      <td>5</td>
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
      <td>5</td>
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
      <td>5</td>
    </tr>
  </tbody>
</table>
</div>



### Exercises module 3



a) create a dataframe with the method of your choice

## 4. Learn how to use Pandas data structures in data science to manipulate data (group by, pivot, melt)

Pandas offers a wide variety of different method to transform and manipulate your data. I will provide examples of some functions. For further details please check the [Pandas Official Documentation](https://pandas.pydata.org/docs/)

### Sorting


```python
df.sort_values(['quality'], ascending=False)
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
      <th>total acidity</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>495</th>
      <td>10.7</td>
      <td>0.350</td>
      <td>0.53</td>
      <td>2.60</td>
      <td>0.070</td>
      <td>5.0</td>
      <td>16.0</td>
      <td>0.99720</td>
      <td>3.15</td>
      <td>0.65</td>
      <td>11.0</td>
      <td>8</td>
      <td>11.050</td>
    </tr>
    <tr>
      <th>1403</th>
      <td>7.2</td>
      <td>0.330</td>
      <td>0.33</td>
      <td>1.70</td>
      <td>0.061</td>
      <td>3.0</td>
      <td>13.0</td>
      <td>0.99600</td>
      <td>3.23</td>
      <td>1.10</td>
      <td>10.0</td>
      <td>8</td>
      <td>7.530</td>
    </tr>
    <tr>
      <th>390</th>
      <td>5.6</td>
      <td>0.850</td>
      <td>0.05</td>
      <td>1.40</td>
      <td>0.045</td>
      <td>12.0</td>
      <td>88.0</td>
      <td>0.99240</td>
      <td>3.56</td>
      <td>0.82</td>
      <td>12.9</td>
      <td>8</td>
      <td>6.450</td>
    </tr>
    <tr>
      <th>1061</th>
      <td>9.1</td>
      <td>0.400</td>
      <td>0.50</td>
      <td>1.80</td>
      <td>0.071</td>
      <td>7.0</td>
      <td>16.0</td>
      <td>0.99462</td>
      <td>3.21</td>
      <td>0.69</td>
      <td>12.5</td>
      <td>8</td>
      <td>9.500</td>
    </tr>
    <tr>
      <th>1202</th>
      <td>8.6</td>
      <td>0.420</td>
      <td>0.39</td>
      <td>1.80</td>
      <td>0.068</td>
      <td>6.0</td>
      <td>12.0</td>
      <td>0.99516</td>
      <td>3.35</td>
      <td>0.69</td>
      <td>11.7</td>
      <td>8</td>
      <td>9.020</td>
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
      <td>...</td>
    </tr>
    <tr>
      <th>690</th>
      <td>7.4</td>
      <td>1.185</td>
      <td>0.00</td>
      <td>4.25</td>
      <td>0.097</td>
      <td>5.0</td>
      <td>14.0</td>
      <td>0.99660</td>
      <td>3.63</td>
      <td>0.54</td>
      <td>10.7</td>
      <td>3</td>
      <td>8.585</td>
    </tr>
    <tr>
      <th>1478</th>
      <td>7.1</td>
      <td>0.875</td>
      <td>0.05</td>
      <td>5.70</td>
      <td>0.082</td>
      <td>3.0</td>
      <td>14.0</td>
      <td>0.99808</td>
      <td>3.40</td>
      <td>0.52</td>
      <td>10.2</td>
      <td>3</td>
      <td>7.975</td>
    </tr>
    <tr>
      <th>899</th>
      <td>8.3</td>
      <td>1.020</td>
      <td>0.02</td>
      <td>3.40</td>
      <td>0.084</td>
      <td>6.0</td>
      <td>11.0</td>
      <td>0.99892</td>
      <td>3.48</td>
      <td>0.49</td>
      <td>11.0</td>
      <td>3</td>
      <td>9.320</td>
    </tr>
    <tr>
      <th>1299</th>
      <td>7.6</td>
      <td>1.580</td>
      <td>0.00</td>
      <td>2.10</td>
      <td>0.137</td>
      <td>5.0</td>
      <td>9.0</td>
      <td>0.99476</td>
      <td>3.50</td>
      <td>0.40</td>
      <td>10.9</td>
      <td>3</td>
      <td>9.180</td>
    </tr>
    <tr>
      <th>832</th>
      <td>10.4</td>
      <td>0.440</td>
      <td>0.42</td>
      <td>1.50</td>
      <td>0.145</td>
      <td>34.0</td>
      <td>48.0</td>
      <td>0.99832</td>
      <td>3.38</td>
      <td>0.86</td>
      <td>9.9</td>
      <td>3</td>
      <td>10.840</td>
    </tr>
  </tbody>
</table>
<p>1599 rows × 13 columns</p>
</div>



### Select cells based on condition


```python
df[df["quality"]==3].head(3)

#This does not affect the original df, if you want to create a new copy just assign it to a new variable
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
      <th>251</th>
      <td>8.5</td>
      <td>0.26</td>
      <td>0.21</td>
      <td>16.2</td>
      <td>0.074</td>
      <td>41.0</td>
      <td>197.0</td>
      <td>0.9980</td>
      <td>3.02</td>
      <td>0.50</td>
      <td>9.8</td>
      <td>3</td>
    </tr>
    <tr>
      <th>253</th>
      <td>5.8</td>
      <td>0.24</td>
      <td>0.44</td>
      <td>3.5</td>
      <td>0.029</td>
      <td>5.0</td>
      <td>109.0</td>
      <td>0.9913</td>
      <td>3.53</td>
      <td>0.43</td>
      <td>11.7</td>
      <td>3</td>
    </tr>
    <tr>
      <th>294</th>
      <td>9.1</td>
      <td>0.59</td>
      <td>0.38</td>
      <td>1.6</td>
      <td>0.066</td>
      <td>34.0</td>
      <td>182.0</td>
      <td>0.9968</td>
      <td>3.23</td>
      <td>0.38</td>
      <td>8.5</td>
      <td>3</td>
    </tr>
  </tbody>
</table>
</div>



### slicing


* loc gets rows (and/or columns) with particular labels.

* iloc gets rows (and/or columns) at integer locations.


```python
# df["quality"]
# df.iloc[1]
# df.iloc[1004,3]
# df.loc[1,"fixed acidity"]
```

#### EXERCISES

a) Check if the cell in position 1004, column residual sugar and  print "Yes" if column residual sugar (3) is greater than 2.0

b) Check if the cell in position 1004, column quality. Print "Yes" if the quality is equal to the one of row 1400




```python
# if df.iloc[1004,3] > 2.0:
#   print(True)

# if df.loc[1004,"residual sugar"] != 0:
#   print(True)

# if df.loc[1004,"quality"] == df.loc[1400,"quality"]:
#   print("Yes")
```

### Filtering


```python
df.loc[(df['quality'] == 5) & (df['volatile acidity'] == 0.700) & (df['residual sugar'] > 1.9)]
# df.loc[(df['quality'] == 5) & (df['volatile acidity'] == 0.700) & (df['residual sugar'] > 1.9)].reset_index(drop=True)
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
      <th>360</th>
      <td>8.2</td>
      <td>0.7</td>
      <td>0.23</td>
      <td>2.00</td>
      <td>0.099</td>
      <td>14.0</td>
      <td>81.0</td>
      <td>0.99730</td>
      <td>3.19</td>
      <td>0.70</td>
      <td>9.4</td>
      <td>5</td>
    </tr>
    <tr>
      <th>1471</th>
      <td>6.7</td>
      <td>0.7</td>
      <td>0.08</td>
      <td>3.75</td>
      <td>0.067</td>
      <td>8.0</td>
      <td>16.0</td>
      <td>0.99334</td>
      <td>3.43</td>
      <td>0.52</td>
      <td>12.6</td>
      <td>5</td>
    </tr>
    <tr>
      <th>1519</th>
      <td>6.6</td>
      <td>0.7</td>
      <td>0.08</td>
      <td>2.60</td>
      <td>0.106</td>
      <td>14.0</td>
      <td>27.0</td>
      <td>0.99665</td>
      <td>3.44</td>
      <td>0.58</td>
      <td>10.2</td>
      <td>5</td>
    </tr>
  </tbody>
</table>
</div>



### groupby


```python
df.groupby(['quality']).count() #mean, sum ....
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
    <tr>
      <th>quality</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>3</th>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
    </tr>
    <tr>
      <th>4</th>
      <td>53</td>
      <td>53</td>
      <td>53</td>
      <td>53</td>
      <td>53</td>
      <td>53</td>
      <td>53</td>
      <td>53</td>
      <td>53</td>
      <td>53</td>
      <td>53</td>
    </tr>
    <tr>
      <th>5</th>
      <td>681</td>
      <td>681</td>
      <td>681</td>
      <td>681</td>
      <td>681</td>
      <td>681</td>
      <td>681</td>
      <td>681</td>
      <td>681</td>
      <td>681</td>
      <td>681</td>
    </tr>
    <tr>
      <th>6</th>
      <td>638</td>
      <td>638</td>
      <td>638</td>
      <td>638</td>
      <td>638</td>
      <td>638</td>
      <td>638</td>
      <td>638</td>
      <td>638</td>
      <td>638</td>
      <td>638</td>
    </tr>
    <tr>
      <th>7</th>
      <td>199</td>
      <td>199</td>
      <td>199</td>
      <td>199</td>
      <td>199</td>
      <td>199</td>
      <td>199</td>
      <td>199</td>
      <td>199</td>
      <td>199</td>
      <td>199</td>
    </tr>
    <tr>
      <th>8</th>
      <td>18</td>
      <td>18</td>
      <td>18</td>
      <td>18</td>
      <td>18</td>
      <td>18</td>
      <td>18</td>
      <td>18</td>
      <td>18</td>
      <td>18</td>
      <td>18</td>
    </tr>
  </tbody>
</table>
</div>



#### EXERCISES

a) Calculate the average citric acid for red wine having "quality = 3"

b)  Calculate the number of observations for every quality class


### unique


```python
names = df["quality"].unique()
names
```




    array([6, 5, 7, 8, 4, 3, 9])



#### EXERCISES

a) How many different quality classes are represented in the df? Check if we have a quality == 10 

### pivot

The pivot() function is used to reshaped a given DataFrame organized by given index / column values. This function does not support data aggregation, multiple values will result in a MultiIndex in the columns.


```python
df_cars
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
      <th>cars</th>
      <th>Country</th>
      <th>sales</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>BMW</td>
      <td>Italy</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Volvo</td>
      <td>Spain</td>
      <td>7</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Ford</td>
      <td>Italy</td>
      <td>2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Tesla</td>
      <td>Italy</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_cars.pivot(index='cars', columns='Country', values='sales')
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
      <th>Country</th>
      <th>Italy</th>
      <th>Spain</th>
    </tr>
    <tr>
      <th>cars</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>BMW</th>
      <td>3.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Ford</th>
      <td>2.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Tesla</th>
      <td>1.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Volvo</th>
      <td>NaN</td>
      <td>7.0</td>
    </tr>
  </tbody>
</table>
</div>



## 5. Understand techniques for accessing and using files

Different functions to deal with different files.


```python
pd.read_excel('data.xlsx', index_col = 0)
df.to_excel("output.xlsx", index = False)
```


```python
pd.read_csv()
df.to_csv("output.csv")
```


```python
# .to_json()
# .to_html()
# .to_sql()
# .to_pickle() ...
```


```python
# When dealing with huge amount of data better work with chunks

chunk_list = []  # append each chunk df here 

# Each chunk is in df format
for chunk in df_chunk:  
    # perform data filtering 
    chunk_filter = chunk_preprocessing(chunk)
    
    # Once the data filtering is done, append the chunk to list
    chunk_list.append(chunk_filter)
    
# concat the list into dataframe 
df_concat = pd.concat(chunk_list)
```

### Final exercise
For this final exercise, you are going to use the (in)famous titanic dataset. Here is a brief description:

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



a) Load the dataset "titanic" (via Askdata, username = "fosic56191@ppp998.com" , password = "Luiss1234!") 

b) Explore the dataset and get a basic understanding of it (How many columns are numerical, categorical, ecc..)

c) How many passengers survived? What was the average age of the survivors? 

d) Which port of Embarkation had the greatest rate of survivors? (hint: **help(df.groupby)**)

e) How many passengers were below 22 years old? How old was the youngest passenger ( hint help(df.min())

f) write a for loop to append values to a brand new list called survivors. If the i-th record survived append "Survived" to the list, else "Not Survived" 

g) Create a subset of the dataframe taking only the survivors (Survived == 1) and export it as "survivors.csv"


### List comprehensions

Find all of the numbers from 1–1000 that have a 6 in them

Find all of the words in a string that are less than 5 letters



```python
# A
from askdata import Askdata

askdata = Askdata(username = "fosic56191@ppp998.com", password = "Luiss1234!")
agent_name = "titanic"


# C
# df.groupby("Survived").count()
# df[df["Survived"] ==1]["Age"].mean()

# D
# df.groupby(["Embarked", "Survived"]).count()



# E
# df[df["Age"]< 22] 800
# min(df["Age"]) 0.42


#F
# survived = ["Survived" for x in range(len(df)) if df.loc[x,"Survived"]==1]


#G
# temp = df[df["Survived"]==1]
# temp.to_csv("df.csv")

#LIST 1
# q2_answer = [num for num in nums if "6" in str(num)]

#LIST 2
# sentence = ["I love radio rock"]
# words = string.split(" ")
# q5_answer = [word for word in words if len(word) < 5]
```


[![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/19PW3m7FeBxXBhFGEygZqRA90rWD-c8-R?usp=sharing)