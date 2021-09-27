
## 1. Introduction to Python

<p align="center">
  <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/f8/Python_logo_and_wordmark.svg/1200px-Python_logo_and_wordmark.svg.png"/>
</p>


Main Features:

* Python works on different platforms (Windows, Mac, Linux, Raspberry Pi, etc).
* Python has a simple syntax similar to the English language.
* Python has syntax that allows developers to write programs with fewer lines than some other programming languages.
* Python runs on an interpreter system, meaning that code can be executed as soon as it is written. This means that prototyping can be very quick.
* Python can be treated in a procedural way, an object-oriented way or a functional way.
* Standards for style: [PEP 8](https://www.python.org/dev/peps/pep-0008/)

Main Data types:

- Integers
- Floats
- String
- Lists
- Set
- Arrays
- Dictionaries


```python
var_int = 1
var_float = 1.1
var_string = "Hello, I am a String"
var_list = [1, 2, "a", 4, 2]
var_array = np.array([1, 2, "a"]) # Some operations are different w.r.t to lists
var_set = set(var_list)
var_dict = {"a" : 10, "b" : 20}
```

All these structures are mainly divided into two categories.

<p align="center">
  <b>Mutable Vs. Immutable</b>
</p>

Mutable is a fancy way of saying that the internal state of the object is changed/mutated. So, the simplest definition is: An object whose internal state can be changed is mutable. On the other hand, immutable doesn’t allow any change in the object once it has been created.
<p align="center">
  <img src="https://miro.medium.com/max/538/1*sAoqf0mk34ij9RomTq2zdQ.png"/>
</p>

## 2. Introduction to Jupyter Notebooks and Colab Environment

Notebook documents (or “notebooks”) are documents produced by the Jupyter Notebook App, which contain both computer code (e.g. python) and rich text elements (paragraph, equations, figures, links, etc…). Notebook documents are both **human-readable** documents containing the analysis description and the results (figures, tables, etc..) as well as executable documents which can be run **to perform data analysis**.


<p align="center">
  <img src="https://colab.research.google.com/img/colab_favicon_256px.png"/>
</p>


Google Colaboratory, or “Colab” for short, is a product from Google Research. Colab allows anybody to write and execute arbitrary python code through the browser, and is especially well suited to machine learning, data analysis and education. More technically, Colab is a hosted Jupyter notebook service that requires no setup to use, while providing fr**ee access to computing resources including GPUs**. Link to colab example [click here](https://colab.research.google.com/notebooks/basic_features_overview.ipynb#scrollTo=d-S-3nYLQSHb)



```python
# Variable Definition
a = 10
a
```


```python
print('    /|')
print("   / |")
print("  /  |")
print(" /   |")
print("/____|")
```


```python
# Ask the user for an input
print("What's your name?")
n = input()
print("Hello", n, ", Nice to meet you!")
```

    What's your name?
    Edoardo
    Hello Edoardo , Nice to meet you!



```python
# IF Statement
a = 222
b = 200
if b > a:
  print("b is greater than a")
elif a > b:
  print("a is greater than b")
else: 
  print("a == b")
```


```python
# For loop
fruits = ["apple", "banana", "cherry"]
for x in fruits:
  print(x)

# Or

fruits = ["apple", "banana", "cherry"]
for x in range(len(fruits)):
  print(fruits[x])

```


```python
# It is possible to define functions... and even classes

def sum_values(a, b):
  sum = a + b
  return sum

sum_values(3,4)

```


```python
#  # Executions might be time consuming sometimes...just interrupt them

# import time
# print("Sleeping")
# time.sleep(30) # sleep for a while; interrupt me!
# print("Done Sleeping")
```


```python
# Drive can be mounted as well
from google.colab import drive
drive.mount('/content/drive')

# With free usage, some limits are inevitable:

# Google Colab has a 'maximum lifetime' limit of running notebooks that is 12 hours with the browser open, and the 'Idle' notebook instance is interrupted after 90 minutes.
# In addition, you can have a maximum of 2 notebooks running simultaneously.
```

### List comprehension

List comprehension offers a shorter syntax when you want to create a new list based on the values of an existing list.


```python
fruits = ["apple", "banana", "cherry", "kiwi", "mango"]
newlist = []

for x in fruits:
  if "a" in x:
    newlist.append(x)

print(newlist)
```


```python
# List comprehensions

fruits = ["apple", "banana", "cherry", "kiwi", "mango"]

newlist = [x for x in fruits if "a" in x]

print(newlist)

# newlist = [expression for item in iterable if condition == True]
```

### Exercise

a) For example, let's say we need to create a list of integers which specify the length of each word in a certain sentence, but only if the word is not the word for".
```python
sentence = "Big Data Management for Executive"
words = sentence.split()
word_lengths = []
for word in words:
      if word != "the":
          word_lengths.append(len(word))
print(words)
print(word_lengths)
```
Using a list comprehension, we could simplify this process..

b) Using a list comprehension, create a new list called "newlist" out of the list "numbers", which contains only the positive numbers from the list, as integers (int function).



```python
numbers = [34.6, -203.4, 44.9, 68.3, -12.2, 44.6, 12.7]
newlist = []
print(newlist)
```




```python
# sentence = "Big Data Management for Executive"
# words = sentence.split()
# word_lengths = []
# for word in words:
#       if word != "for":
#           word_lengths.append(len(word))
# print(words)
# print(word_lengths)

# numbers = [34.6, -203.4, 44.9, 68.3, -12.2, 44.6, 12.7]
# newlist = [int(x) for x in numbers if x > 0]
# print(newlist)
```


[![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1tLEGZlkQWUssBsNacUyU_Nvp8Eo66vRG?usp=sharing)