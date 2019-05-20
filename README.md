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

```ctrl + u ``` copy from beginning, ```ctrl + y``` paste

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

```
import array
l = list(range(5))
a = array.array('i', l) # array('i', [0,1,2,3,4])
```

'i' here declare the type of the array. If we put "f" it would have been a array containing float elements.

But NumPy's ```ndarray``` is better than what python's array module has to offer.

```
import numpy as np
np.array([1,54,123,123]) # array([1,54,123,123])
```

NumPy array's contain the same type of element, unlike python's list that may have different types of elements.

```
# To declare the data type of the array
np.array([1,2,4,5,9], dtype=float32) # array([1,2,4,5,9], dtype=float32)
```

For multidimensional array ```np.array([[1,2], [2,3]])``` or ```np.array([range(0,4), range(1,5)])``` or ```np.array([range(i, i+2) for i in [2, 4, 5]])```

```
array([[2, 3],
       [4, 5],
       [5, 6]])
```

The inner lists are treated as rows.

Creating an array of zeros of length 5 ```np.zeros(5, dypte=int)```

Creating a multidimensional floating point array which is 3X5 (RC = Row, Column) on ```1.```s (. for floating numbers) ```np.ones((3, 5), dtype=float)```

Creating or filling an array with a specific number. ```np.full((3, 5), 7)``` fills a 3X5 array with 7s.

[continue from here](https://jakevdp.github.io/PythonDataScienceHandbook/02.01-understanding-data-types.html)