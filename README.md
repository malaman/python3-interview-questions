# python3-interview-questions

## Table of contents

  1. [Questions](#questions)
  2. [Answers] (#answers)
  

### Questions

#### Basic questions
* What are the differences in print command between Python3 and Python2?
* How to write Python3 compatible code in Python2?
* What is the differences in the string types for Python3 and Python2?



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
