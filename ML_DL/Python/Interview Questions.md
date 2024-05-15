# Questions

1.  What is the difference between a list and a tuple in Python?
2.  Explain list comprehensions and provide an example.
3.  What are lambda functions? How do you use them?
4.  What is the purpose of the `__init__` method in Python classes?
5.  What are Python decorators and how do you use them?
6.  What is the difference between "is" and " == " in Python?
7.  What are the main differences between Python 2 and Python 3?
8.  How do you handle exceptions in Python?
9.  What are Python generators and how do they differ from regular functions?
10.  How do you create and use a context manager in Python?
11.  What are the differences between the `*args` and `**kwargs` syntax in Python function definitions?
12.  Explain the concept of duck typing in Python.
13.  What is the purpose of the `global` keyword in Python?
14.  What are Python modules and packages? How do you create and import them?
15.  How do you use the `with` statement in Python?
16.  How does Python handle memory management and garbage collection?
17.  What is a Python virtual environment, and why is it useful?
18.  How do you create and use a classmethod and a staticmethod in Python?
19.  How does Python's multiple inheritance work?
20.  What are Python's metaclasses and how do you use them?
21.  How do you use the `map`, `filter`, and `reduce` functions in Python?
22.  What is the difference between `shallow copy` and `deep copy` in Python?
23.  What is the Global Interpreter Lock (GIL) in Python, and what are its implications for concurrency?
24.  What is the difference between threads and processes in Python, and when should you use each?
25.  Explain the concept of list slicing in Python and provide an example.
26.  What is the difference between an iterator and an iterable in Python?
27.  How do you sort a list of dictionaries by a specific key value in Python?
28.  How do you manage and maintain multiple versions of Python on the same machine?
29.  Explain the difference between a shallow and a deep copy in Python.
30.  What are some common ways to optimize Python code for performance?
31. what are type hints?
32. what are annotations?
33. string formatting

## Data Structures

![[1_ADbePjuNR5OqGDzzgOj63Q.jpg]]

## Lists and tuples

Lists and tuples are both ordered collections of items in Python. The main differences between them are:

-   Lists are mutable, which means you can change their content (add, remove, or modify elements) after creating them. Lists are defined using square brackets, e.g., `my_list = [1, 2, 3]`.
-   Tuples are immutable, which means you cannot change their content once they are created. Tuples are defined using parentheses, e.g., `my_tuple = (1, 2, 3)`.

Because tuples are immutable, they are generally faster and consume less memory than lists. Tuples are commonly used when you want to create a collection of items that should not be changed.

## List comprehensions

  List comprehensions are a concise way to create lists in Python. They are often used for creating new lists by applying an operation to each item in an existing list or other iterable object. The resulting list comprehension consists of an output expression followed by a `for` statement and optionally one or more `if` statements. The syntax is:

    `[output_expression for item in iterable if condition]`
    
    For example, to create a list of the squares of the numbers from 0 to 9, you would use a list comprehension like this:
    
    `squares = [x**2 for x in range(10)]`

## Lambda functions

Lambda functions are small, anonymous functions defined using the `lambda` keyword. They can have any number of arguments but can only have one expression. Lambda functions are useful when you need a simple function for a short period of time and don't want to define a full function using `def`. The syntax for a lambda function is:

pythonCopy code

`lambda arguments: expression`

For example, to create a lambda function that adds two numbers, you would do:


``` python
add = lambda x, y: x + y 
result = add(5, 3)
````

In this example, `result` would be `8`.

## init method

The `__init__` method is a special method in Python classes, often referred to as the class constructor. It is called automatically when you create a new instance of a class. The purpose of the `__init__` method is to initialize the object's attributes with default or provided values. For example:
```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

person = Person("Alice", 30)
```
In this example, the `__init__` method initializes the `name` and `age` attributes of the `Person` class.

## Decorators

Decorators are a way to modify or extend the behavior of a function or method without changing its code. They are implemented as higher-order functions that take a function as input and return a new function with the desired modifications. Decorators are applied to functions using the `@decorator` syntax. For example:

```python
def my_decorator(func):
    def wrapper():
        print("Something is happening before the function is called.")
        func()
        print("Something is happening after the function is called.")
    return wrapper

@my_decorator
def say_hello():
    print("Hello!")

say_hello()
```
In this example, `my_decorator` is a decorator that wraps the `say_hello` function, adding a print statement before and after the function is called.

## is vs ==

In Python, "is" and " == " are used to compare objects, but they serve different purposes:

-   " == " is used to compare the values of two objects to check if they are equal. It compares the content of the objects.
-   "is" is used to compare the identity of two objects to check if they are the same. It compares the memory addresses of the objects.

For example:

list1 = [1, 2, 3]
list2 = [1, 2, 3]
list3 = list1

print(list1 == list2)  # True, because the contents of both lists are the same
print(list1 is list2)  # False, because they are two different objects in memory
print(list1 is list3)  # True, because list3 refers to the same object as list1

## pyhton2 vs python3

Python 2 and Python 3 are two major versions of the Python programming language. Python 3 introduced many improvements and changes that make it incompatible with Python 2. Some key differences include:

-   Print function: In Python 2, "print" is a statement, while in Python 3, "print" is a function that requires parentheses.
-   Integer division: In Python 2, dividing two integers results in an integer (truncated), while in Python 3, it results in a float.
-   Unicode support: In Python 3, strings are Unicode by default, whereas in Python 2, strings are ASCII by default.
-   xrange function: In Python 2, the "xrange()" function is used for efficient iteration in loops, while in Python 3, the "range()" function has the same functionality and "xrange()" is removed.
-   Exception handling: In Python 2, exceptions are caught using "except ExceptionType, e:" syntax, while in Python 3, the syntax is "except ExceptionType as e:".

## Exception handeling

Exceptions are events that occur during the execution of a program, usually due to errors or exceptional conditions. To handle exceptions in Python, you can use a try-except block. The "try" block contains the code that might raise an exception, while the "except" block contains the code that will be executed if an exception occurs.

```python
try:
    # Code that might raise an exception
    result = 10 / 0
except ZeroDivisionError as e:
    # Code to handle the exception
    print("Cannot divide by zero:", e)

except Exception as e:
    # Code to handle any other exception type that was not caught above
    print("An unexpected error occurred:", e)
```

## Generators

Generators are special types of functions that allow you to create an iterator in a memory-efficient way. Instead of returning a whole list or sequence, generators use the "yield" keyword to produce items one at a time, on-demand. This makes them ideal for working with large datasets or infinite sequences. Here is an example of a generator function:

```python
def count_up_to(max):
    count = 1
    while count <= max:
        yield count
        count += 1

counter = count_up_to(5)
for number in counter:
    print(number)
```


In this example, the "count_up_to" function is a generator that yields numbers from 1 up to the specified maximum value.

In one Simpsons episode, Homer crashes his car into a deer statue, followed by three
lines of dialogue. 

```python
def doh():
	return ["Homer: D'oh!", "Marge: A deer!", "Lisa: A female deer!"]
for line in doh():
	print(line)
```

Homer: D'oh!
Marge: A deer!
Lisa: A female deer!

This works perfectly when lists are relatively small. But what if we’re grabbing all the
dialogue from all the Simpsons episodes? Lists use memory.
```python
def doh2():
	yield "Homer: D'oh!"
	yield "Marge: A deer!"
	yield "Lisa: A female deer!"

for line in doh2():
	print(line)
```

Homer: D'oh!
Marge: A deer!
Lisa: A female deer!
## Context Manager

## args vs kwargs

`*args` and `**kwargs` are special syntaxes in Python function definitions that allow you to pass a variable number of arguments to a function.

-   `*args`: This syntax is used to pass a variable number of non-keyword (positional) arguments to a function. Inside the function, these arguments are received as a tuple.
-   `**kwargs`: This syntax is used to pass a variable number of keyword arguments to a function. Inside the function, these arguments are received as a dictionary.

Here's an example:

```python
def example_function(*args, **kwargs):
    print("Positional arguments:", args)
    print("Keyword arguments:", kwargs)

example_function(1, 2, 3, a=4, b=5, c=6)
```
Positional arguments: (1, 2, 3)
Keyword arguments: {'a': 4, 'b': 5, 'c': 6}


```python

def my_func(*args):
  for a in args:
    print(a)

my_func(1, 2, 3)
```
1
2
3

```python
def my_func(**kwargs):
  for key, value in kwargs.items():
    print(key, value)

my_func(first='a', second='b', boy = "arpit")
```

first a
second b
boy arpit

## Duck typing

Duck typing is a programming concept in which the type of an object is determined by its behavior (i.e., the methods and properties it has) rather than its class. In Python, duck typing is used extensively in favor of strict type checking. This allows for more flexible and reusable code, as you can write functions that work with any object that provides the required behavior, rather than being limited to a specific type or class. The term comes from the saying, "If it looks like a duck, swims like a duck, and quacks like a duck, then it probably is a duck."

## 'global' keyword

The `global` keyword in Python is used to indicate that a variable is a global variable, meaning it is accessible from anywhere in the code, not just within the function or block of code where it is defined. By default, variables defined within a function are local to that function and cannot be accessed outside of it. To modify a global variable within a function, you need to use the `global` keyword before the variable. Here's an example:

```python
counter = 0

def increment_counter():
    global counter
    counter += 1

increment_counter()
print(counter)  # Output: 1
```

## Modules, Packages, Library and Framework

1. Module:
    - A module is a single Python file that contains Python definitions, statements, and instructions.
    - It is used to organize related code into a single unit and can be imported into other Python scripts or modules.
    - Modules help in breaking down large programs into smaller, more manageable files.
    - Examples of built-in Python modules include `math`, `random`, `os`, and `datetime`.
2. Package:
    - A package is a collection of Python modules organized in a directory hierarchy.
    - It is a way to structure and organize related modules into a single unit.
    - A package typically contains an `__init__.py` file in each directory, which makes Python treat the directory as a package.
    - Packages provide a way to avoid naming conflicts between modules and allow for better organization of code.
    - Examples of popular Python packages include `numpy`, `pandas`, `requests`, and `matplotlib`.
3. Library:
    - A library is a collection of packages and modules that provide a set of related functionality.
    - It is a reusable piece of code that can be imported and used in different projects.
    - Libraries are typically designed to solve specific problems or provide tools for a particular domain.
    - They encapsulate complex functionality and provide a high-level interface for developers to use.
    - Examples of Python libraries include `NumPy` (numerical computing), `Pandas` (data manipulation and analysis), and `Matplotlib` (data visualization).
4. Framework:
    - A framework is a more comprehensive and opinionated collection of libraries, tools, and conventions.
    - It provides a structured approach and a set of rules for building applications in a specific domain.
    - Frameworks often dictate the architecture, design patterns, and best practices to follow when building applications.
    - They provide a foundation and a set of abstractions that developers can build upon, saving time and effort.
    - Examples of Python frameworks include Django (web development), Flask (web development), and PyTorch (machine learning).

In summary:

- A module is a single Python file containing related code.
- A package is a collection of related modules organized in a directory hierarchy.
- A library is a collection of packages and modules that provide a set of related functionality.
- A framework is a comprehensive and opinionated collection of libraries, tools, and conventions for building applications in a specific domain.

These terms are often used interchangeably, but they represent different levels of abstraction and organization in Python code. Modules and packages are the building blocks, while libraries and frameworks provide higher-level functionality and structure for building applications.

## 'with' statement


## Memory management and Garbage collection

Python handles memory management automatically, using a combination of reference counting and garbage collection. When an object is created, Python allocates memory for it and keeps track of the number of references to that object. When an object's reference count drops to zero (i.e., it is no longer used), the memory occupied by the object is automatically reclaimed.

Python also has a cyclic garbage collector, which is responsible for detecting and collecting objects involved in reference cycles (i.e., when a group of objects reference each other but are not used elsewhere). The cyclic garbage collector runs periodically and is implemented using a generational garbage collection algorithm to improve efficiency.

## Virtual environment

A Python virtual environment is an isolated environment where you can install and manage packages without affecting the global Python installation on your system. Virtual environments are useful because they allow youMeta to work on multiple projects with different dependencies and Python versions, without causing conflicts between packages or versions.

## Classmethod and staticmethod

## Multiple inheritence

## Metaclasses

## Map, filter, reduce

-   `map(function, iterable)`: Applies a given function to all items in the input iterable and returns an iterator (map object) of the results. Example:
```python
numbers = [1, 2, 3, 4]
squares = list(map(lambda x: x ** 2, numbers))  # Output: [1, 4, 9, 16]
```

-   `filter(function, iterable)`: Filters the input iterable based on a given function, which should return a boolean value. Only the items for which the function returns `True` are retained in the output iterator (filter object). Example:

```python
numbers = [1, 2, 3, 4, 5]
even_numbers = list(filter(lambda x: x % 2 == 0, numbers))  # Output: [2, 4]
```

    
-   `reduce(function, iterable[, initializer])`: Applies a given function cumulatively to the items in the input iterable, from left to right, reducing the iterable to a single value. The `reduce()` function is part of the `functools` module. Example:

```python
from functools import reduce
numbers = [1, 2, 3, 4]
product = reduce(lambda x, y: x * y, numbers)  # Output: 24
```

## Shallow vs Deep copy

-   Shallow copy: Creates a new object and inserts references to the original elements. Changes to the original elements are reflected in the shallow copy. You can create a shallow copy using the `copy()` method or the `copy` module's `copy()` function.
    
-   Deep copy: Creates a new object and recursively inserts copies of the original elements, rather than references. Changes to the original elements do not affect the deep copy. You can create a deep copy using the `copy` module's `deepcopy()` function.

## Global Interpreter Lock (GIL)

## Threads vs processes

## Iterator vs Iterable

-   Iterable: An iterable is an object that can be looped over using a for loop. It implements the `__iter__()` method, which returns an iterator. Examples of iterables include lists, tuples, sets, and dictionaries.
    
-   Iterator: An iterator is an object that implements the `__iter__()` and `__next__()` methods. The `__iter__()` method returns the iterator itself, and the `__next__()` method returns the next value in the sequence. When there are no more items left, the `__next__()` method raises the `StopIteration` exception. You can create custom iterators by defining a class with these two methods.

## Sorting a list of dictionaries by a specific key value

```python
data = [{'name': 'Alice', 'age': 30}, {'name': 'Bob', 'age': 25}, {'name': 'Eve', 'age': 35}]
sorted_data = sorted(data, key=lambda x: x['age'])
```

## Managing and maintaining multiple versions of Python on the same machine

To manage multiple versions of Python on the same machine, you can use a version management tool like `pyenv`. `pyenv` allows you to install, switch between, and manage different Python versions easily.

To install `pyenv`, follow the instructions for your operating system from the official repository: [https://github.com/pyenv/pyenv](https://github.com/pyenv/pyenv)

After installing `pyenv`, you can install different Python versions using the `pyenv install` command, and switch between them using the `pyenv global` or `pyenv local` commands.

## Common ways to optimize Python code for performance

-   Use built-in functions and libraries: Built-in functions and standard libraries are usually implemented in C and optimized for performance.
    
-   Use list comprehensions: List comprehensions are more concise and often faster than using for loops to create lists.
    
-   Use generators: Generators allow you to create iterables that produce items on-the-fly, reducing memory consumption for large data sets.
    
-   Use sets and dictionaries for membership testing: Sets and dictionaries have O(1) average-case lookup time, making them more efficient than lists for membership testing.
    
-   Profile and optimize hotspots: Use profiling tools like `cProfile` to identify performance bottlenecks in your code and focus on optimizing those hotspots.
    
-   Use the right data structures and algorithms: Choosing appropriate data structures and algorithms for your problem can significantly improve performance.
    
-   Use multiprocessing for CPU-bound tasks: For CPU-bound tasks, the `multiprocessing` module can help bypass the Global Interpreter Lock (GIL) and utilize multiple CPU cores.
    
-   Use multithreading for I/O-bound tasks: For I/O-bound tasks, using threads can improve performance by allowing your program to continue executing other tasks while waiting for I/O operations to complete.

## Ternary expression

```python
x = 10
y = 20
max_value = x if x > y else y
```

## Zip function

```python
names = ["Alice", "Bob", "Charlie"]
ages = [25, 30, 35]
for name, age in zip(names, ages):
    print(name, age)
```

## os and re module

The `os` module provides a way to interact with the operating system, such as working with files, directories, and environment variables.

The `re` module provides support for regular expressions, allowing you to search, match, and manipulate strings based on patterns.

## Enumerate function

```python
fruits = ["apple", "banana", "cherry"]
for index, fruit in enumerate(fruits):
    print(index, fruit)
```

## type hints

Type hints allow developers to specify the expected type of variables, function parameters, and return values. They are used by static type checkers like `mypy`, IDEs, and linters to find type errors in code before it runs.

```python

def greet(name: str) -> str:     
	return f'Hello, {name}'
```

In this function, `name: str` is a type hint indicating that `name` should be a string, and `-> str` indicates that the function returns a string.

## Annotations

Annotations are a more general form of type hints, allowing for any expression to be associated with function parameters and return values. While type hints are a subset of annotations specifically for type information, annotations can be used for other purposes as well.

```python
def multiply(a: int, b: int) -> int:    
	return a * b
```

Here, `a: int` and `b: int` are annotations indicating that both `a` and `b` should be integers.

## String Formatting

```python
prompt = "You are a content creator. Write a technical blog about {topic}."

topic = "vector databases"

prompt.format(topic=topic)
```

Output: 'You are a content creator. Write a technical blog about vector databases.'

```python
prompt = f"You are a content creator. Write a technical blog about {topic}."

topic = "vector databases"

prompt
```

Output: 'You are a content creator. Write a technical blog about vector databases.'

## Async/Await

