
## 6) Data Cleaning

it is important to be able to deal with messy data, whether that means missing values, inconsistent formatting, malformed records, or nonsensical outliers.

We’ll cover the following:

* Dropping unnecessary columns in a DataFrame
* Changing the index of a DataFrame
* detecting and removing na
* Renaming columns to a more recognizable set of labels


```python
## Deleting columns

import pandas as pd

df = pd.read_csv("wine-red.csv", sep=";")

to_drop = ['quality']

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

### Detect Outliers

Outliers need a special mention in this section. In statistics, an outlier is an observation point that is distant from other observations. We are not going to cover this since I think some kind of theoretical knowledge is required but keep in mind that this is really important when analyzing data.

## 7) Lambda functions

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

## Data Visualization

Data visualization is the discipline of trying to understand data by placing it in a visual context so that patterns, trends and correlations that might not otherwise be detected can be exposed. Python offers multiple great graphing libraries that come packed with lots of different features.

Matplotlib is one of the most used libraries: is a comprehensive library for creating static, animated, and interactive visualizations in Python.


```python
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
      <th>quality</th>
      <th>alcohol</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>7.4</td>
      <td>0.700</td>
      <td>0.00</td>
      <td>1.9</td>
      <td>0.076</td>
      <td>11.0</td>
      <td>34.0</td>
      <td>0.99780</td>
      <td>3.51</td>
      <td>0.56</td>
      <td>5</td>
      <td>9.4</td>
    </tr>
    <tr>
      <th>1</th>
      <td>7.8</td>
      <td>0.880</td>
      <td>0.00</td>
      <td>2.6</td>
      <td>0.098</td>
      <td>25.0</td>
      <td>67.0</td>
      <td>0.99680</td>
      <td>3.20</td>
      <td>0.68</td>
      <td>5</td>
      <td>9.8</td>
    </tr>
    <tr>
      <th>2</th>
      <td>7.8</td>
      <td>0.760</td>
      <td>0.04</td>
      <td>2.3</td>
      <td>0.092</td>
      <td>15.0</td>
      <td>54.0</td>
      <td>0.99700</td>
      <td>3.26</td>
      <td>0.65</td>
      <td>5</td>
      <td>9.8</td>
    </tr>
    <tr>
      <th>3</th>
      <td>11.2</td>
      <td>0.280</td>
      <td>0.56</td>
      <td>1.9</td>
      <td>0.075</td>
      <td>17.0</td>
      <td>60.0</td>
      <td>0.99800</td>
      <td>3.16</td>
      <td>0.58</td>
      <td>6</td>
      <td>9.8</td>
    </tr>
    <tr>
      <th>4</th>
      <td>7.4</td>
      <td>0.700</td>
      <td>0.00</td>
      <td>1.9</td>
      <td>0.076</td>
      <td>11.0</td>
      <td>34.0</td>
      <td>0.99780</td>
      <td>3.51</td>
      <td>0.56</td>
      <td>5</td>
      <td>9.4</td>
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
      <th>1594</th>
      <td>6.2</td>
      <td>0.600</td>
      <td>0.08</td>
      <td>2.0</td>
      <td>0.090</td>
      <td>32.0</td>
      <td>44.0</td>
      <td>0.99490</td>
      <td>3.45</td>
      <td>0.58</td>
      <td>5</td>
      <td>10.5</td>
    </tr>
    <tr>
      <th>1595</th>
      <td>5.9</td>
      <td>0.550</td>
      <td>0.10</td>
      <td>2.2</td>
      <td>0.062</td>
      <td>39.0</td>
      <td>51.0</td>
      <td>0.99512</td>
      <td>3.52</td>
      <td>0.76</td>
      <td>6</td>
      <td>11.2</td>
    </tr>
    <tr>
      <th>1596</th>
      <td>6.3</td>
      <td>0.510</td>
      <td>0.13</td>
      <td>2.3</td>
      <td>0.076</td>
      <td>29.0</td>
      <td>40.0</td>
      <td>0.99574</td>
      <td>3.42</td>
      <td>0.75</td>
      <td>6</td>
      <td>11.0</td>
    </tr>
    <tr>
      <th>1597</th>
      <td>5.9</td>
      <td>0.645</td>
      <td>0.12</td>
      <td>2.0</td>
      <td>0.075</td>
      <td>32.0</td>
      <td>44.0</td>
      <td>0.99547</td>
      <td>3.57</td>
      <td>0.71</td>
      <td>5</td>
      <td>10.2</td>
    </tr>
    <tr>
      <th>1598</th>
      <td>6.0</td>
      <td>0.310</td>
      <td>0.47</td>
      <td>3.6</td>
      <td>0.067</td>
      <td>18.0</td>
      <td>42.0</td>
      <td>0.99549</td>
      <td>3.39</td>
      <td>0.66</td>
      <td>6</td>
      <td>11.0</td>
    </tr>
  </tbody>
</table>
<p>1599 rows × 12 columns</p>
</div>



To create a scatter plot in Matplotlib we can use the scatter method. We will also create a figure and an axis using plt.subplots so we can give our plot a title and labels.



```python
import matplotlib.pyplot as plt

# create a figure and axis

fig, ax = plt.subplots()

ax.scatter(df['quality'], df['pH'])
# set a title and labels
# ax.set_title('Red wine Dataset')
# ax.set_xlabel('Quality')
# ax.set_ylabel('pH')
fig.show()
```


![png](dataviz_files/dataviz_15_0.png)


Data visualization is often crucial if you want to transmit someone a message. For this reason, it is always reccomended investing your time in this activity. When I am in need of fancy graphs, I always visit [this website](https://www.python-graph-gallery.com/) which offers a huge variety of graphs with ready to use code snippets. 


```python
### Bar plot

# create a figure and axis 
fig, ax = plt.subplots() 
# count the occurrence of each class 
data = df['quality'].value_counts() 
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


![png](dataviz_files/dataviz_17_0.png)


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


![png](dataviz_files/dataviz_19_0.png)


Why is correlation important?

Multicollinearity refers to a situation in which more than two explanatory variables in a multiple regression model are highly linearly related. This correlation is a problem because independent variables should be independent. If the degree of correlation between variables is high enough, it can cause problems when you fit the model and interpret the results.



[![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1a1eJGot3xd3p0uqxfsxc8ZQWciCIvacG?usp=sharing)