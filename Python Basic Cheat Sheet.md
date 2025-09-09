# Python Cheat Sheet

This guide is a collection of Python code snippets that cover the basics of the language. It is intended to be a quick reference for anyone who is new to Python or needs a refresher.

## Variables
In Python, variables are used to store data values. Here’s a quick guide on variables in Python:

### 1. Creating Variables
You can create a variable by assigning a value to it using the equals sign (=).
```python
x = 10          # Integer
y = 3.14        # Float
name = "Alice"  # String
is_active = True  # Boolean
```
### 2. Variable Naming Rules
- Must start with a letter (a-z, A-Z) or an underscore (_).

- Can include letters, digits (0-9), and underscores.

- Case-sensitive: myVar and myvar are different.

- Cannot be a reserved keyword (e.g., if, else, while).

### 3. Dynamic Typing
Python is dynamically typed, meaning you don’t need to declare the type of a variable explicitly.

```python
x = 5           # Initially an integer
x = "Hello"     # Now it's a string
```

### 4. Multiple Assignments
You can assign values to multiple variables in a single line.

```python
a, b, c = 1, 2, 3
```

### 5. Constants
By convention, constants are written in uppercase letters.

```python
PI = 3.14159
```

### 6. Type Checking
You can check the type of a variable using the type() function.

```python
# if x is a string
print(type(x))

# Outputs: <class 'str'>
```

### 7. Updating Variables
You can change the value of a variable at any time.

```python
count = 10
count += 5      # Now count is 15

n = n + 1 # good practice
n += 1    # good practice
n++       # bad practice
```
### 8. None in Python

Here are a few key points:

- None: The only null-like value in Python, indicating no value or a null reference.

- Type: `None` has its own type called `NoneType`.

- Usage: Use `None` in conditions and comparisons to check for missing values.

```python
n = 4
n = None
print("n =", n)
>>> n = None

my_var = None
if my_var is None:
    print("my_var is None")
```

## If-statements

If-statements in Python are used for conditional execution of code. Here's a concise guide on how to use them:

### 1. Basic Syntax

```python
if condition:
    # code to execute if condition is True
   
# Example
x = 10
if x > 5:
    print("x is greater than 5")
```

```python
# If statements don't need parentheses or curly braces.
n = 1
if n > 2:
    n -= 1
elif n == 2:
    n *= 2
else:
    n += 2

# Parentheses needed for multi-line conditions.
# and = &&
# or  = ||
n, m = 1, 2
if ((n > 2 and n != m) or n == m):
    n += 1
```

### 2. Else Clause
You can add an else clause to execute code when the condition is False.

```python
if x > 5:
    print("x is greater than 5")
else:
    print("x is 5 or less")
```

### 3. Elif Clause
Use elif (else if) to check multiple conditions.

```python
if x > 5:
    print("x is greater than 5")
elif x == 5:
    print("x is equal to 5")
else:
    print("x is less than 5")
```

### 4. Multiple Conditions
You can combine conditions using logical operators: and, or, not.

```python
if x > 5 and x < 15:
    print("x is between 5 and 15")
```

### 5. Nested If Statements
You can nest if-statements inside other if-statements.

```python
if x > 5:
    if x < 10:
        print("x is between 5 and 10")
```

### 6. Ternary Operator
For simple conditions, you can use a one-liner if-else (ternary operator).

```python
result = "x is high" if x > 10 else "x is low"
```

## Loops

Here's a quick guide on loops in Python, covering both `for` and `while` loops:

### 1. For Loops
Used for iterating over a sequence (like a list, tuple, string, or range).

#### Basic Syntax
```python
for variable in sequence:
    # code to execute for each item
```
#### Example
```python
# Iterate over a list
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit)
```
#### Using range()
You can use range() to iterate a specific number of times.

```python
n = 5
while n < 5:
    print(n)
    n += 1

# Looping from i = 0 to i = 4
for i in range(5):
    print(i)

# Looping from i = 2 to i = 5
for i in range(2, 6):
    print(i)

# Loop over numbers from 5 down to (but not including) 0, stepping by -2.
for i in range(5, 1, -1):
    print(i)

# Output:
# 5
# 3
# 1
```

### 2. While Loops
Used to execute a block of code as long as a condition is True.

#### Basic Syntax
```python
while condition:
    # code to execute
```

#### Example

```python
count = 0
while count < 5:
    print(count)
    count += 1
```

### 3. Loop Control Statements
- `break`: Exits the loop.

- `continue`: Skips the current iteration and moves to the next one.

- `pass`: A placeholder that does nothing (used when a statement is syntactically required).

Example with `break`

```python
for i in range(10):
    if i == 5:
        break
    print(i)  # Prints 0 to 4
```

Example with `continue`

```python
for i in range(10):
    if i % 2 == 0:
        continue
    print(i)  # Prints odd numbers only
```
### 4. Nested Loops
You can use loops inside other loops.

#### Example

```python
for i in range(3):
    for j in range(2):
        print(f"i: {i}, j: {j}")
# Values are printed using f-strings (Python 3.6+)
```

### 5. List Comprehensions
A concise way to create lists using a for loop.

#### Example

```python
squares = [x**2 for x in range(10)]  # Generates a list of squares from 0 to 9
```

## Math

Here's a quick guide to using math in Python, including basic operations, the math module, and common mathematical functions:

### 1. Basic Arithmetic Operations
You can perform basic arithmetic directly with operators.

```python
# Addition
result = 5 + 3  # 8

# Subtraction
result = 5 - 3  # 2

# Multiplication
result = 5 * 3  # 15

# Division and rounding
# The '/' operator performs floating-point division by default, resulting in a decimal value.
result = 5 / 2  # 2.5

# The '//' operator performs floor division, which rounds down to the nearest integer.
result = 5 // 2  # 2

print(-3 // 2)  # Output: -2
# Floor division with negative numbers rounds down towards negative infinity, 
# so -3 // 2 results in -2.

print(int(-3 / 2))  # Output: -1
# This line divides -3 by 2 (resulting in -1.5) and converts it to an integer using int()
# which truncates the decimal and rounds towards zero.

# Modulus (remainder) is similar to other languages
result = 5 % 2  # 1

# Except for negative values
print(-10 % 3) # 2

# The result of -10 % 3 is 2 because Python's modulo operation returns a non-negative remainder.
# it calculates as -10 + 12 (the nearest multiple of 3).

# To be consistent Modulo with Other Languages:

import math
print(math.fmod(-10, 3))  #  -1.0
# math.fmod() behaves more like the modulo operation in some other languages, 
# returning a result with the same sign as the dividend (-10).

# Exponentiation
result = 5 ** 3  # 125
```

### 2. Using the math Module
Python's built-in math module provides access to mathematical functions.

#### Importing the Module

```python
import math
```

#### Common Functions
- Square root: `math.sqrt(x)`

- Factorial: `math.factorial(n)`

- Trigonometric functions: `math.sin(x)`, `math.cos(x)`, `math.tan(x)`

- Logarithm: `math.log(x)`, `math.log10(x)` for base 10

- Constants: `math.pi`, `math.e`

```python
import math

# Calculate square root
sqrt_value = math.sqrt(16)  # 4.0

# Raise 2 to the power of 3.
print(math.pow(2, 3))  # Outputs: 8.0

# Calculate factorial
fact_value = math.factorial(5)  # 120

# Calculate sine of 30 degrees (convert to radians)
sine_value = math.sin(math.radians(30))  # 0.5
```

### 3. Rounding Numbers
You can round numbers using built-in functions.

```python
# Round to nearest integer
rounded = round(4.6)  # 5

# Round down
floored = math.floor(4.6)  # 4

# Round up
ceiled = math.ceil(4.2)  # 5
```

### 4. Random Numbers
For generating random numbers, use the random module.

#### Example
```python
import random

# Random float between 0 and 1
random_float = random.random()

# Random integer between a range
random_int = random.randint(1, 10)  # Includes both 1 and 10
```
### 5. Infinite Values

```python
# Max / Min Int
float("inf")   # Positive infinity
float("-inf")  # Negative infinity

# Python can handle very large integers without overflow.
print(math.pow(2, 200))  # Outputs a very large number

# Any finite number is always less than positive infinity.
print(math.pow(2, 200) < float("inf"))   # Outputs: True
```


## Functions

Here's a concise guide to defining and using functions in Python:

### 1. Defining a Function
You define a function using the def keyword, followed by the function name and parentheses. If the function takes parameters, you list them inside the parentheses.

```python
def function_name(parameters):
    # code to execute
    return value  # optional
```

#### Example

```python
def greet(name):
    return f"Hello, {name}!"
```

### 2. Calling a Function
To execute a function, you call it by its name and pass any required arguments.

```python
message = greet("Alice")
print(message)  # Outputs: Hello, Alice!
```
### 3. Default Parameters
You can provide default values for parameters, which will be used if no argument is passed.

```python
def greet(name="Guest"):
    return f"Hello, {name}!"
```

### 4. Variable-Length Arguments
Use *args for a variable number of positional arguments and **kwargs for a variable number of keyword arguments.

```python
def add_numbers(*args):
    return sum(args)

def print_info(**kwargs):
    for key, value in kwargs.items():
        print(f"{key}: {value}")
```

#### Example

```python
print(add_numbers(1, 2, 3))  # Outputs: 6
print_info(name="Alice", age=30)  # Outputs: name: Alice \n age: 30
```

### 5. Lambda Functions
These are small, anonymous functions defined using the lambda keyword.

```python
square = lambda x: x ** 2
print(square(5))  # Outputs: 25
```

### 6. Docstrings
You can add documentation to your function using triple quotes right after the function definition.

```python
def greet(name):
    """Return a greeting message."""
    return f"Hello, {name}!"
```

### 7. Scope of Variables
Variables defined inside a function are local to that function and cannot be accessed outside of it.

```python
def my_function():
    x = 10  # local variable
    return x

print(my_function())  # Outputs: 10
# print(x)  # Raises NameError
```

### 8. Nested Functions and Scope

```python
def outer(a, b):
    c = "c"

    def inner():
        return a + b + c  # Accessing variables from the outer function
    return inner()  # Calling the inner function

print(outer("a", "b"))  # Outputs: "abc"
```

#### Explanation:

- Outer Function: `outer(a, b)` takes two parameters and defines a local variable `c`.

- Inner Function: `inner()` is defined inside `outer()`. It can access variables from `outer()` (`a`, `b`, and `c`) due to Python’s lexical scoping rules.

- When `outer()` is called, it returns the result of `inner()`, which concatenates `a`, `b`, and `c`.

### 9. Modifying Mutable Objects and Nonlocal Keyword

```python
def double(arr, val):
    def helper():
        # Modifying array works
        for i, n in enumerate(arr):
            arr[i] *= 2  # This modifies the original list in place

        # Trying to modify val directly will not affect the outer val
        # val *= 2  # Uncommenting this would raise an UnboundLocalError

        # Using nonlocal to modify val in the enclosing scope
        nonlocal val
        val *= 2  # This modifies the val in the outer function scope

    helper()
    print(arr, val)  # Prints the modified array and the updated val

nums = [1, 2]
val = 3
double(nums, val)  # Outputs: [2, 4] 3
```
#### Explanation:

- Modifying Lists: The `helper()` function modifies the list `arr` in place. Lists are mutable in Python, so changes to their elements affect the original list.

- Attempting to Modify `val`: The line `val *= 2` would raise an `UnboundLocalError` because Python treats `val` as a local variable within `helper()`, as you tried to assign a new value to it.

- Using `nonlocal`: To modify `val` in the enclosing `double()` scope, the `nonlocal` keyword is used. This tells Python to look for `val` in the nearest enclosing scope that is not global.

## Classes

Here's a concise guide to using classes in Python, including key concepts and examples.

### 1. Defining a Class
You define a `class` using the class keyword. A class can have attributes (variables) and methods (functions).

```python
class ClassName:
    def __init__(self, parameters):
        # Constructor to initialize attributes
        self.attribute = parameters

    def method_name(self):
        # Method to perform an action
        pass
```

#### Example

```python
class Dog:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def bark(self):
        return f"{self.name} says woof!"
```

### 2. Creating an Object
You create an object (instance) of a class by calling the class name.

```python
my_dog = Dog("Buddy", 3)
print(my_dog.bark())  # Outputs: Buddy says woof!
```

### 3. The `self` Keyword
- Reference to the Instance: `self` refers to the specific instance of the class that is calling the method. It allows access to instance attributes and methods.

- Distinguishing Variables: Without `self`, Python cannot differentiate between instance attributes and local variables within methods.

#### Example
```python
class Dog:
    def __init__(self, name):
        self.name = name  # Instance attribute

    def set_name(self, name):
        self.name = name  # 'self.name' refers to the instance attribute
```

### 4. Class Attributes
You can also define attributes that are shared across all instances.

```python
class Dog:
    species = "Canine"  # Class attribute

    def __init__(self, name):
        self.name = name

print(Dog.species)  # Outputs: Canine
```

### 5. Inheritance
You can create a new class that inherits from an existing class.

```python
class Puppy(Dog):  # Puppy inherits from Dog
    def play(self):
        return f"{self.name} is playing!"
```

### 6. Method Overriding
A subclass can override methods of its superclass.

```python
class Puppy(Dog):
    def bark(self):
        return f"{self.name} says yip!"
```

### 7. Using super()
You can call methods from a parent class using super().

```python
class Puppy(Dog):
    def bark(self):
        return super().bark() + " But in a higher pitch!"
```

### 8. Class Methods and Static Methods
- Class Methods: Use `@classmethod` decorator and take `cls` as the first parameter.

- Static Methods: Use `@staticmethod` decorator, don’t take `self` or `cls`.

```python
class Dog:
    species = "Canine"

    @classmethod
    def get_species(cls):
        return cls.species

    @staticmethod
    def bark():
        return "Woof!"
```

