# python3-interview-questions

## Table of contents

  1. [Questions](#questions)
  2. [Answers] (#answers)
  

### Questions

#### Basic questions
* What are the differences in print command between Python3 and Python3 ?



### Answers

### Answers to [Basic questions](#questions)
* What are the differences in print command between Python3 and Python3 ?

1. Python3 `print `requires brackets () around arguments, because python3 `print` is a function. 
1. Python2 `print ` is not a function, but reserved command. Python2 does not require parantheses. If aruments is provided with parantheses python2 `print` considers argument as a tuple


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


