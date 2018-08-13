
 # Reading Data with Pandas

## Introduction

Another library that is integral to data science is Pandas. Have you ever looked at a table of data, maybe excel, and thought, "I wish I had that in a format I could use in Python!"? We'll you're in luck because that is exactly the type of problem that this new library can solve for us. In this lesson, we will introduce the ways in which Pandas is used and why it is such a powerful tool. We'll also show exactly how to get started using Pandas and common operations. 

## Objectives
* Importing Pandas
* Creating a DataFrame
* Reading a CSV

## Importing Pandas

The first thing we do with all librarys is import them into our code. And we know that our code is usually following some kind of pattern or convention, right? Well, Pandas is no exception to that. Just as we alias the NumPy library import `as np`, we alias Pandas `as pd`. Let's check it out.


```python
import pandas as pd
print(pd)
```

    <module 'pandas' from '/usr/local/lib/python3.6/site-packages/pandas/__init__.py'>


Great! we have Pandas imported and aliased, so that, now we can refer to the Pandas module as simply `pd`.

# Creating a DataFrame

A DataFrame is a new data type for us. So, in order to understand what a DataFrame is, it is important to have a visualization of the object. Below, we are taking some lists (some multi-dimensional), and using it to create a Pandas DataFrame.

Essentially, a DataFrame is an organized, formatted object containing rows and columns with data contained in the cells between the rows and colums. You can think of it as almost the Python equivalent of looking at a matrix in a CSV or excel file.

First, let's see the DataFrame without any real values populated. We will create the DataFrame with just columns and Rows.

> The syntax for creating a DataFrame is:


```python
pd.DataFrame(DATA, COLUMNS, INDEX(optional))
# without an index, the left column will just auto index using integers (i.e. 1, 2, 3, etc.)

OR

pd.DataFrame(data=['Python', 'Pandas', 'Flatiron School'], 
             columns=['Coolest Programming Lang','Neatest Python Library','Best Programming School']
            )
```


```python
days_of_class = ['day1', 'day2', 'day3', 'day4']
attendance = ['absent', 'present']
empty_students = []
pd.DataFrame(data=empty_students, columns=attendance, index=days_of_class)
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
      <th>absent</th>
      <th>present</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>day1</th>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>day2</th>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>day3</th>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>day4</th>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



Now, if we add in a list of lists such as 4 lists containing 1 student who was absent, and 1 student who was present all inside another list (i.e. `[ [1,2], [1,2], [1,2], [1,2] ]`), we can provide the data we need for our DataFrame! 

Don't think too much about the multidimensional list. We will see those again in the future. But for now, focus on DataFrames! Below, we are creating the list of lists that will be used to show absent and present students for class.


```python
present_stds = ['Anna', 'Billy', 'Meghan', 'George']
absent_stds = ['Hunter', 'Francine', 'Gail', 'Tucker']
students = [[absent_stds[0], present_stds[0]], [absent_stds[1], present_stds[1]], [absent_stds[2], present_stds[2]], [absent_stds[3], present_stds[3]]]

pd.DataFrame(students, index=days_of_class, columns=attendance)
```

Now, let's see what we were talking about when we said our DataFrame would **auto index**... Well, our DataFrame will always need an index (or line number) and without the days of the week as our indexes, our DataFrame will populate the index with a list of integers for the number of rows of data in the DataFrame. Let's look at the same example as we have from above, but this time without the index.


```python
pd.DataFrame(students, columns=attendance)
```

Now, it looks like we have a *day **0***, but that's alright. The important thing here is to note that without data for your index, Pandas will simply use integers to denote rows. In fact, if we remove the data for the columns, Pandas will also use integers to create column titles. 


```python
pd.DataFrame(students)
```
