# python3-interview-questions

## Table of contents

  1. [Questions](#questions)
    1. [Basic Questions](#basic-questions)
    2. [Nerd questions](#nerd-questions)
  2. [Answers] (#answers)


### Questions


<a name="basic-questions"></a> 
#### Basic questions
* What are the differences in print command between Python3 and Python2?
* How to write Python3 compatible code in Python2?
* What is the differences in the string types for Python3 and Python2?
* What is the differences between range, map, filter commands for Python3 and Python2?
* What is the differences in integer division operations between Python3 and Python2?
* What is the differences in exception handling between Python3 and Python2?
* What is the decorators in Python?
* What are absolute and explicit relative imports in Python3?
* What is the simplest way to merge two dicts in Python3?

<a name="nerd-questions"></a> 
### Nerd questions
* Is it possible to write python code with curly braces?
* What is The Zen of Python?

### Answers

### Answers to [Basic questions](#questions)
* What are the differences in `print` command between Python3 and Python2?

    1. Python3 `print `requires parantheses around arguments, because Python3 `print` is a function. 
    1. Python2 `print ` is not a function, but a reserved command. Python2 does not require parantheses. If arguments are provided with parantheses in Python2, `print` considers arguments as a tuple.


Python2:
```python
>>> print "Hello, world"
Hello, world
>>> print "Hello", "world"
Hello world
>>> print("Hello", "world")
('Hello', 'world')
```
Python3:
```python
>>> print("Hello, world")
Hello, world
>>> print("Hello", "world")
Hello world
```

* How to write Python3 compatible code in Python2?

With the usage of Python2  `__future__` module, it is possible  to use Python3 incopatible keywords in Python2.

Python2
````python
>>> from __future__ import print_function
>>> print('Now Python2 print is', 'like', 'Python3 print')
Now Python2 print is like Python3 print
````

* What is the differences in the string types for Python3 and Python2?

Python2 strings by default don't have an encoding: they are raw byte data.

Python3 strings are unicode by default. Python3 has also byte data type, which equals to Python2 default string representation. Every string in Python3  can be encoded and stored in bytes, or decoded back into unicode string again.

Python2
```python
>>> str = 'München'
>>> str
'M\xc3\xbcnchen'
>>> str = b'München'
>>> str
'M\xc3\xbcnchen'
>>> str = u'München'
>>> str
u'M\xfcnchen'
```
Python3

```python
>>> str = 'München'
>>> str
'München'
>>> str2 = str.encode()
>>> str2
b'M\xc3\xbcnchen'
>>> str2.decode()
'München'
```

* What is the differences between range, map, filter commands for Python3 and Python2?

In Python2 range, map, filter commands return lists, in Python3 the commands return iterable objects. Iterable object can be converted to list via `list(iterable)` command.

Python2
```python
>>> a = range(5)
>>> a
[0, 1, 2, 3, 4]
>>> filter(lambda x: x > 2, a)
[3, 4]
>>> map(lambda x: x * 2, a)
[0, 2, 4, 6, 8]
```

Python3
```python
>>> a = range(5)
>>> a
range(0, 5)
>>> a = list(a)
>>> a
[0, 1, 2, 3, 4]
>>> filter(lambda x: x > 2, a)
<filter object at 0x101c18278>
>>> list(filter(lambda x: x > 2, a))
[3, 4]
>>> map(lambda x: x * 2, a)
<map object at 0x101c182b0>
>>> list(map(lambda x: x * 2, a))
[0, 2, 4, 6, 8]
```

* What is the differences in integer division operations between Python3 and Python2?

In Python2 integer division with `/` or `//` operators always returns integer as a result. 
In Python3 integer division with `/` operator returns float, but `//` operator returns integer. 

Python2
```python
>>> 15 / 6
2
>>> 15 // 6
2
```

Python3
```python
>>> 15 / 6
2.5
>>> 15 // 6
2
```

* What is the differences in exception handling between Python3 and Python2?

In Python2 if during exception handling another exception is occur, only last exception is shown. 
In Python3 in such case all chain of exceptions is shown.

Python2
```python
>>> try:
...     v = int('x')
... except ValueError:
...     raise Exception('Something Wrong')
... 
Traceback (most recent call last):
  File "<stdin>", line 4, in <module>
Exception: Something Wrong
```
Python3
```python
>>> try:
...     v = int('x')
... except ValueError:
...     raise Exception('Something Wrong')
... 
Traceback (most recent call last):
  File "<stdin>", line 2, in <module>
ValueError: invalid literal for int() with base 10: 'x'

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "<stdin>", line 4, in <module>
Exception: Something Wrong
```
* What is the decorators in Python?

Decorator is a callable object (i.e. function), which receives a function as an argument and returns other function.
Decorators are used to add common functionality to the functions (for example add logging or debug information).

```python
>>> def decorate(func):
...     def inner(*args, **kwargs):
...         print('args: {} kwargs: {}'.format(args, kwargs))
...         return func(*args, **kwargs)
...     return inner
...
>>>  @decorate
... def add(a, b):
...     return a+b
...
>>> 
>>> add(1, 2)
args: (1, 2) kwargs: {}
3
>>> def sub(a, b):
...     return a-b
... 
>>> sub = decorate(sub)
>>> sub(1,2)
args: (1, 2) kwargs: {}
-1
```

* What are absolute and explicit relative imports in Python3?

Absolute imports are the imports from `sys.path` (example: `from some_package import something`. Search of `some_package` will be performed in the `sys.path` locations.).

Explicit relative imports are the imports from a module relative to that module's location, (example: `from .some_package import something`. Search of `some_package` will be performed in the current directory.).

In Python2 `from some_package import something` statement searches also in the current directory.
Python3 also allows `from same_package import *` imports only in the begining of file.
Python2 allows such imports in any place of a file.

* What is the simplest way to merge two dicts in Python3?

Python3.5 introduces unpacking operators in literals and allows to use following:
```python
>>> dict1 = {'x': 1, 'y': 2}
>>> dict2 = {'z': 3}
>>> dict3 = {**dict1, **dict2}
>>> dict3
{'x': 1, 'y': 2, 'z': 3}
```
If you use pre Python3 version, following method could be used:
```python
>>> dict3 = dict1.copy()
>>> dict3.update(dict2)
>>> dict3
{'x': 1, 'y': 2, 'z': 3}
```



### Answers to [Nerd questions](#nerd-questions)

* Is it possible to write python code with curly braces?

There is special import from `__future__` module, which was designed to enable possibility to code in python with curly braces, but for misterios reasons interpreter reports `SyntaxError: not a chance`. Some developers consider this error as the most funniest error in python :)

```python
>>> from __future__ import braces
  File "<stdin>", line 1
SyntaxError: not a chance
```

* What is The Zen of Python?

This is probably the most famous python joke. You should `import this` to receive the answer.

```python
>>> import this
The Zen of Python, by Tim Peters

Beautiful is better than ugly.
Explicit is better than implicit.
Simple is better than complex.
Complex is better than complicated.
Flat is better than nested.
Sparse is better than dense.
Readability counts.
Special cases aren't special enough to break the rules.
Although practicality beats purity.
Errors should never pass silently.
Unless explicitly silenced.
In the face of ambiguity, refuse the temptation to guess.
There should be one- and preferably only one -obvious way to do it.
Although that way may not be obvious at first unless you're Dutch.
Now is better than never.
Although never is often better than *right* now.
If the implementation is hard to explain, it's a bad idea.
If the implementation is easy to explain, it may be a good idea.
Namespaces are one honking great idea - let's do more of those!

```


