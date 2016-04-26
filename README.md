# python3-interview-questions

## Table of contents

  1. [Questions](#questions)
  2. [Answers] (#answers)
  

### Questions

#### Basic questions
* What are the differences in print command between Python3 and Python2?
* How to write Python3 compatible code in Python2?



### Answers

### Answers to [Basic questions](#questions)
* What are the differences in `print` command between Python3 and Python2?

    1. Python3 `print `requires parantheses around arguments, because Python3 `print` is a function. 
    1. Python2 `print ` is not a function, but a reserved command. Python2 does not require parantheses. If arguments are provided with parantheses in Python2, `print` considers arguments as a tuple.


Python2:
```python
print "Hello, world"
print "Hello", "world"
print("Hello", "world")
```
Result:
````
Hello, world
Hello world
('Hello', 'world')
````

Python3:
```python
print("Hello, world")
print("Hello", "world")
```
Result:
````
Hello, world
Hello world
````


* How to write Python3 compatible code in Python2?

With the usage of Python2  `__future__` module, it is possible  to use Python3 incopatible keywords in Python2.

Python2
````python
from __future__ import print_function
print('Now Python2 print is', 'like', 'Python3 print')
````

```
Now Python2 print is like Python3 print
```
