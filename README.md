# PDSH-Notes

Python Data Science Handbook by Jake VanderPlas notes. Notes are based on my stream on twitch and Youtube.

[Python Data Science Handbook by Jake VanderPlas](https://jakevdp.github.io/PythonDataScienceHandbook/)

[Support the author buying the book](http://shop.oreilly.com/product/0636920034919.do)

[anyfactor.xyz](https://www.anyfactor.xyz)

## Day 1

Initiating ipython shell in terminal ```ipython```

Initiating Jupyter notebook in terminal ```jupyter notebook```

```help(len)``` = ```len?```

To get the source code ```len??```

Both of this even works for the functions you have created.

Tab completion is awesome. ```len.<tab>```

Tab completion is great in conjunction with ```from pandas import <tab>``` and ```import <tab>``` to list out the objects and libraries.

```*``` with ```?``` for wildcard matching. ```*warning?``` and ```str.*find*?```

```ctrl + u``` copy from beginning, ```ctrl + y``` paste

```ctrl + p``` previous command in history, ```ctrl + r``` history command

```ctrl + l``` clear, ```ctrl + d``` Exit

```%paste``` paste without indentation problem

```%run test.py``` run a .py file in the same folder, and functions of that file is now available in the shell, and you can call them.

```%timeit``` for single line execution, and ```%%timeit``` for multiline codes.

```%magic``` and ```%lsmagic``` to get a list of magic functions.

Everything you input is stored in ```In``` which is a list (Input number is index number) and Everything you output is stored in ```Out``` as a dictionary (Output number is Key).

For easy access to output use ```print(_)```, 1 underscore is the last one, 2 underscore as in ```print(__)``` for the 2nd last ```Out``` or output result.

```Out[2]``` = ```_2```

for not displaying an output end the statement with a semicolon. ```math.e;```

```%history -n 1-4``` return history input, ```-n``` for index number,  ```1-4``` for limiting the return statement.

## Day 2

shell commands work in ipython by prefixing them with ```!```, i.e. ```!ls```

We can also assign variables to the output of this ipython shell commands i.e. ```files = !ls```, which returns a special kind of list.

You can also use python variables as shell variables by using ```{varname}``` i.e. ```!echo {message}```

You can ```cd``` by magic command ```%cd``` or simply ```cd```. This works for every shell command.

```%xmode``` limits the exception (/error) message. ```%xmode``` takes a single argument of the three, ```Plain```(less information), ```Context```(Default), and ```Verbose```(More information). i.e. ```%xmode Plain```.

python's standard debugger ```pdb```, and ipython's is ```ipdb```. We enter into debugging with ```%debug```. Then start giving commands (```print```, ```type``` etc.) to check, and ```quit```.

To run a file in debugging mode ```%run -d test.py```

In the debugger ```help```. ```help <specific command>```.

```%prun``` code profiler.  Very important chapter to write efficient codes. [here is the link to the chapter](https://jakevdp.github.io/PythonDataScienceHandbook/01.07-timing-and-profiling.html).

[Resources and Book Recommendation](https://jakevdp.github.io/PythonDataScienceHandbook/01.08-more-ipython-resources.html)

## Day 3

The goal is to efficiently store and manage numerical arrays.

NumPy arrays are more efficient and versatile than python's ```list```.

Dynamic languages such as python does not require explicit declaration of variable type, unlike statically typed languages such as java & C.

Integer in python contains 4 information, reference count for memory allocation, type of the variable, size for the data members, and digit for the integer value.

List is the standard multi element container in python.

Lists can contain heterogenous elements, which is handy but in a scenario where all the elements are same type the extra information each elements has to identify them is redundant. It would be more efficient to store this homogenous element set to a fixed-type array which a numpy array.

The built-in ```array``` module provides an solution for dense arrays of a uniform type.

```python
import array
l = list(range(5))
a = array.array('i', l) # array('i', [0,1,2,3,4])
```

'i' here declare the type of the array. If we put "f" it would have been a array containing float elements.

But NumPy's ```ndarray``` is better than what python's array module has to offer.

```python
import numpy as np
np.array([1,54,123,123]) # array([1,54,123,123])
```

NumPy array's contain the same type of element, unlike python's list that may have different types of elements.

```python
# To declare the data type of the array
np.array([1,2,4,5,9], dtype=float32) # array([1,2,4,5,9], dtype=float32)
```

For multidimensional array ```np.array([[1,2], [2,3]])``` or ```np.array([range(0,4), range(1,5)])``` or ```np.array([range(i, i+2) for i in [2, 4, 5]])```

```python
array([[2, 3],
       [4, 5],
       [5, 6]])
```

The inner lists are treated as rows.

Creating an array of zeros of length 5 ```np.zeros(5, dypte=int)```

Creating a multidimensional floating point array which is 3X5 (RC = Row, Column) on ```1.```s (. for floating numbers) ```np.ones((3, 5), dtype=float)```

Creating or filling an array with a specific number. ```np.full((3, 5), 7)``` fills a 3X5 array with 7s.

## Day 4

Creating an array that utilizes a range function ```np.arange(0, 10, 2)```, this will create a one dimensional array similar to this ```list(range(0, 10, 2))```

Creating array of evenly spaced numbers  ```np.linspace(1, 10, 5)``` 1 is starting value, 10 is ending value & interval is (10-1)/(5-1). Output is ```[ 1., 3.25, 5.5, 7.75, 10.]```

Creating a multidimensional 3X3 array filled with random values between 0, 1 ```np.random.random((3, 3))```

Creating 3X3 array of normally distributed random values with mean 0, and SD 1 ```np.random.normal(0, 1 (3X3))```

3X3 random integer array start at 0, ends at 10 ```np.random.randint(0, 10, (3X3))```

3X3 identity matrix ```np.eye(3)``` returns the following below.

```python
array([[1., 0., 0.],
       [0., 1., 0.],
       [0., 0., 1.]])
```

Creating an uninitialized array of three integers. ```np.empty(3)``` returns ```array([1., 1., 1.])```

To assign a datatype to the array give the keyword ```dtype='int16'``` or ```dtype=np.int16```

[Learn more about types of datatypes scroll down bottom](https://jakevdp.github.io/PythonDataScienceHandbook/02.01-understanding-data-types.html)

## Day 5

Seeding ensure reproducibility when generating random numbers. ```np.random.seed(0)```

```np.random.randint(10, size- (3, 4))``` created a random array which contains random integers from 0-10 in the size 3X4.

```array.ndim``` return number of dimensions, as in one, two or three.

```array.shape``` returns the shape of the array, as in number of rows, and columns

```array.size``` returns the size of the array, as in number of elements in the array and which is the multiplication of shape output.

```array.dtype``` returns the datatype of the array.

```array.itemsize``` for size of each element in the array, ```array.nbytes``` for size of the entire array, which equal to ```itemsize```X```size```.

Indexing an array is similar to standard indexing operation. For 2 dimensional arrays follow RC which is ```[Row, Column]```. Negative index numbers will work also.

Values can be modified through indexing ```arry[0,2] = 12```. As array contain uniform data type adding mismatched data type will be truncated (converted to match the array datatype).

*Slicing* is also possible with arrarys, ```x[<start>, <stop>, <step>]```. Slicing examples >> ```x[::2]``` every other element, ```x[1::2]``` starts at index 1 then every other element, ```x[::-1]``` reverse, ```x[5::-1]``` starts at 5 then goes reverse.

*Multidimensional subarrays(slicing)* row and commas are seperated by commas. ```x[:2, :2]``` first 2 rows, and first 2 columns.

```x[:3, ::2]``` first 3 rows, then every other column element.

```x[::-1, ::-1]``` reverses the array.

To access a single row or column it can be done through ```:```, so ```x[:, 0]``` first single column, ```x[2, :]``` third single row. Single row can be access by only giving the row number ```x[2]```

*Subarray as no copy views* modifying a variable that assigned a subarray with modify the original array. This behavior is similar to python list's reference of values concept. Suppose ```x2 = x[:2, :2]``` modifying ```x2``` will modify the original array of ```x```.

To create a copy of the original when creating the subarrays and evade referencing, use ```x2_copy = x[:3, :4].copy()```

[Restart from here](https://jakevdp.github.io/PythonDataScienceHandbook/02.02-the-basics-of-numpy-arrays.html#Reshaping-of-Arrays)