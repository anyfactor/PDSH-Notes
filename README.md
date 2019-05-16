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

```ctrl + u ``` copy from beginning, ```ctrl + y```` paste

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

[Continue from here](https://jakevdp.github.io/PythonDataScienceHandbook/01.05-ipython-and-shell-commands.html)