---
jupyter:
  jupytext:
    formats: ipynb,md
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.1'
      jupytext_version: 1.2.4
  kernelspec:
    display_name: Python 3
    language: python
    name: python3
---

# Name(s)
Mian Uddin


**Instructions:** This is an individual assignment, but you may discuss your code with your neighbors.


# Python and NumPy

While other IDEs exist for Python development and for data science related activities, one of the most popular environments is Jupyter Notebooks.

This lab is not intended to teach you everything you will use in this course. Instead, it is designed to give you exposure to some critical components from NumPy that we will rely upon routinely.

## Exercise 0
Please read and reference the following as your progress through this course. 

* [What is the Jupyter Notebook?](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/What%20is%20the%20Jupyter%20Notebook.ipynb#)
* [Notebook Tutorial](https://www.datacamp.com/community/tutorials/tutorial-jupyter-notebook)
* [Notebook Basics](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/Notebook%20Basics.ipynb)

**In the space provided below, what are three things that still remain unclear or need further explanation?**


* My DATA 301 teacher taught me everything


## Exercises 1-7
For the following exercises please read the Python appendix in the Marsland textbook and answer problems A.1-A.7 in the space provided below.


## Exercise 1

```python
import numpy as np
```

```python
a = np.full((6, 4), 2)
a
```

## Exercise 2

```python
b = np.eye(6, 4) * 2 + np.ones((6, 4))
b
```

## Exercise 3

```python
a * b
```

`np.dot(a, b)` does not work because the columns of `a` need to match the rows of `b` to compute the dot product.


## Exercise 4

```python
np.dot(a.transpose(), b)
```

```python
np.dot(a, b.transpose())
```

The outputs are different because the order matters with dot product and different dimensions in a different order will result in a different dimension for the output.


## Exercise 5

```python
def out():
    print("lmao")

out()
```

## Exercise 6

```python
def six():
    for i in range(0, 3):
        a = np.random.rand(1, 9)
        print("{}, {}, etc.".format(np.sum(a), np.mean(a)))

six()
```

## Exercise 7

```python
def count_ones(arr):
    count = 0
    for a in arr:
        for b in a:
            if b == 1:
                count += 1
    return count
```

```python
count_ones(b)
```

```python
len(np.where(b == 1)[0])
```

## Excercises 8-???
While the Marsland book avoids using another popular package called Pandas, we will use it at times throughout this course. Please read and study [10 minutes to Pandas](https://pandas.pydata.org/pandas-docs/stable/getting_started/10min.html) before proceeding to any of the exercises below.


## Exercise 8
Repeat exercise A.1 from Marsland, but create a Pandas DataFrame instead of a NumPy array.

```python
import pandas as pd
```

```python
a_df = pd.DataFrame(a)
```

## Exercise 9
Repeat exercise A.2 using a DataFrame instead.

```python
b_df = pd.DataFrame(b)
```

## Exercise 10
Repeat exercise A.3 using DataFrames instead.

```python
a_df * b_df
```

## Exercise 11
Repeat exercise A.7 using a dataframe.

```python
b_df.apply(pd.value_counts).loc[1.0].sum()
```

## Exercises 12-14
Now let's look at a real dataset, and talk about ``.loc``. For this exercise, we will use the popular Titanic dataset from Kaggle. Here is some sample code to read it into a dataframe.

```python
titanic_df = pd.read_csv(
    "https://raw.githubusercontent.com/dlsun/data-science-book/master/data/titanic.csv"
)
titanic_df
```

Notice how we have nice headers and mixed datatypes? That is one of the reasons we might use Pandas. Please refresh your memory by looking at the 10 minutes to Pandas again, but then answer the following.


## Exercise 12
How do you select the ``name`` column without using .iloc?

```python
titanic_df["name"]
```

## Exercise 13
After setting the index to ``sex``, how do you select all passengers that are ``female``? And how many female passengers are there?

```python
titanic_df.set_index('sex', inplace=True)
```

```python
titanic_df[titanic_df.index == "female"]
```

```python
titanic_df[titanic_df.index == "female"].shape[0]
```

## Exercise 14
How do you reset the index?

```python
titanic_df.reset_index()
```
