# Data Structures Cheat Sheet

This guide is a collection of Python code snippets that cover the basic data structures in Python, along with their key features and examples. It is intended to be a quick reference for anyone who is new to Python or needs a refresher.

## Arrays (called Lists)

In Python, arrays are referred to as lists. They are versatile and allow for various operations. Below are the key features and operations you can perform with lists in Python.

#### Time Complexity:

- Access: `O(1)`

- Insertion: `O(1)` on average (append at end), `O(N)` (at index)

- Deletion: `O(1)` (pop from end), `O(N)` (remove by value)

- Search: `O(N)`

#### Space Complexity: `O(N)` where N is the number of elements.

### 1. Basic List Operations

- Creating a List:

```python
arr = [1, 2, 3]  # Create a list
```

- Accessing Elements:

```python
first_elem = arr[0]  # First element
last_elem = arr[-1]  # Last element
```

- Modifying Elements: Directly change the value of an existing index.

```python
arr[1] = 10  # Change second element to 10
```

- Initializing Lists

```python
# Initialize arr of size n with default value of 1
n = 5
arr = [1] * n
print(arr)  # Outputs: [1, 1, 1, 1, 1]
print(len(arr))  # Outputs: 5
```

### 2. Common Methods
- Adding and removing Elements

```python
arr.insert(1, 5)  # Insert 5 at index 1

arr.remove(2)  # Remove the first occurrence of 2

# Using Lists as a Stack
arr.append(4)  # Adds 4 to the end
arr.append(5)  # Adds 5 to the end
print(arr)  # Outputs: [1, 2, 3, 4, 5]

arr.pop()  # Removes the last element (5)
print(arr)  # Outputs: [1, 2, 3, 4]
```

- Clearing the List:

```python
arr.clear()  # Remove all elements
```

- Counting Elements:

```python
count = arr.count(1)  # Count occurrences of 1
```

- Finding Index:

```python
index = arr.index(3)  # Get index of first occurrence of 3
```

### 3. Slicing and Indexing
- Slicing: Extract portions of the list using `start:end`, where the `end` index is exclusive.

```python
# Sublists (aka slicing)
arr = [1, 2, 3, 4]
print(arr[1:3])  # Outputs: [2, 3]

# Similar to for-loop ranges, last index is non-inclusive
print(arr[0:4])  # Outputs: [1, 2, 3, 4]

# But no out of bounds error
print(arr[0:10])  # Outputs: [1, 2, 3, 4]
```
- Negative Indexing: Use negative indices to access elements from the end of the list.

```python
arr = [1, 2, 3]
print(arr[-1])  # Outputs: 3 (last element)
print(arr[-2])  # Outputs: 2 (second to last element)
```

### 4. Unpacking

```python
# Unpacking
a, b, c = [1, 2, 3]
print(a, b, c)  # Outputs: 1 2 3

# Be careful though
# a, b = [1, 2, 3]  # Would raise a ValueError due to unpacking mismatch
```

Unpacking: Assigns elements of a list to multiple variables. Ensure the number of variables matches the list length.

### 5. Looping Through Lists

```python
# Loop through arrays
nums = [1, 2, 3]

# Using index
for i in range(len(nums)):
    print(nums[i])  # Outputs: 1, 2, 3

# Without index
for n in nums:
    print(n)  # Outputs: 1, 2, 3

# With index and value
for i, n in enumerate(nums):
    print(i, n)  # Outputs: (0, 1), (1, 2), (2, 3)
```

- Looping: Iterate through a list using various methods, including index-based and value-based iteration.

### 6. Looping Through Multiple Lists

```python
# Loop through multiple arrays simultaneously with unpacking
nums1 = [1, 3, 5]
nums2 = [2, 4, 6]
for n1, n2 in zip(nums1, nums2):
    print(n1, n2)  # Outputs pairs: (1, 2), (3, 4), (5, 6)
```

Zip Function: Combines two lists into pairs for simultaneous iteration.

### 7. Reversing and Sorting

```python
# Reverse
nums = [1, 2, 3]
nums.reverse()
print(nums)  # Outputs: [3, 2, 1]

# Sorting
arr = [5, 4, 7, 3, 8]
arr.sort()
print(arr)  # Outputs: [3, 4, 5, 7, 8]

# Sort in descending order
arr.sort(reverse=True) 
print(arr)  # Outputs: [8, 7, 5, 4, 3]

arr = ["bob", "alice", "jane", "doe"]
arr.sort()
print(arr)  # Outputs: ['alice', 'bob', 'doe', 'jane']

# Custom sort (by length of string)
arr.sort(key=lambda x: len(x))
print(arr)  # Outputs: ['bob', 'doe', 'jane', 'alice']
```

- Reverse: Use `reverse()` to change the order of elements.

- Sort: The `sort()` method organizes elements. You can sort in ascending/descending order or by a custom key.

### 8. List Comprehension

- List Comprehension is a concise way to create lists based on existing iterables.

```python
# List comprehension
arr = [i for i in range(5)]
print(arr)  # Outputs: [0, 1, 2, 3, 4]

# List of squares
squares = [x**2 for x in range(5)]  # Outputs: [0, 1, 4, 9, 16]
```

- With Conditions:

```python
arr = [1, 2, 3, 4, 5, 6]
evens = [x for x in arr if x % 2 == 0]  # List of even numbers
# Outputs: [2, 4, 6]
```

### 9. 2-D Lists

```python
# 2-D lists
arr = [[0] * 4 for i in range(4)]
print(arr)  # Outputs: [[0, 0, 0, 0], [0, 0, 0, 0], [0, 0, 0, 0], [0, 0, 0, 0]]

element = matrix[1][2]  # Access row 1, column 2
print(arr[0][0], arr[3][3])  # Outputs: 0 0
```

- 2-D Lists: Lists of lists, useful for representing matrices or grids.

<!-- 13. Common Pitfall
```python
# This won't work
# arr = [[0] * 4] * 4  # Creates references to the same inner list
```
- Pitfall: Using multiplication to create a 2-D list this way creates references to the same inner list, leading to unexpected behavior. -->

## Linked List
Python does not have a built-in linked list. Normally, in an interview, you would be given a definition like this.

```python
class LinkedListNode:
    def __init__(self, val, next=None):
        self.val = val
        self.next = next
```
- append to end is `O(N)`.
- finding an element is `O(N)`.

Linked lists are less commonly used in Python compared to other data structures. Besides problems that specifically ask for linked lists, you don't normally define and use linked list. There are a handful of common interview problems on linked lists, such as reversing a linked list, merging two linked lists, getting the middle of a linked list, detecting cycle in a linked list.

Note that Python's built-in `list` is not a linked list, but rather a dynamic array which we have covered above.

## Stack

A stack is a linear data structure that follows the Last In, First Out `(LIFO)` principle, meaning the last element added is the first one to be removed. Common operations include pushing (adding) an element, popping (removing) the top element, and peeking (viewing) the top element without removing it.

#### In Python, you can implement a stack using a list:

```python
# Creating a stack using a list
stack = []

# Pushing elements onto the stack
stack.append(1)  # Stack: [1]
stack.append(2)  # Stack: [1, 2]
stack.append(3)  # Stack: [1, 2, 3]

# Popping the top element
top_element = stack.pop()  # Returns 3, Stack: [1, 2]

# Peeking the top element
peek_element = stack[-1]  # Returns 2

# Checking if the stack is empty
is_empty = len(stack) == 0  # Returns False
```
#### Time Complexity: 

- push: append, `O(1)`
- pop: pop, `O(1)`
- peek or top: stack[-1], `O(1)`
- size: len(stack), `O(1)`

Note: In the case of a dynamic array (like Python's list), there can occasionally be a higher complexity for the push operation due to resizing, but it's amortized O(1) over a sequence of operations. 

#### Space Complexity: 

- The space complexity of a stack is `O(N)`, where N is the number of elements in the stack. This is because the stack needs space for each element added. 

#### In coding interviews, we use stack most often in Graph Traversal (`Depth First Search`), `backtracking` and `Recursion`.

## Queues

A queue is a linear data structure that follows the First In, First Out `(FIFO)` principle, meaning the first element added is the first one to be removed. Common operations include enqueueing (adding) an element, dequeueing (removing) an element, and peeking (viewing) the front element without removing it.

#### In Python, you can implement a stack using a list but a better approach for queues is to use `collections.deque`, which allows for O(1) time complexity for both `enqueue` and `dequeue` operations.

```python
# Queues (double ended queue)
from collections import deque

# Creating a queue using deque
queue = deque()

# Enqueue
queue.append(1)  # Queue: [1]
queue.append(2)  # Queue: [1, 2]
queue.append(3)  # Queue: [1, 2, 3]

# Dequeue
first_element = queue.popleft()  # Returns 1, Queue: [2, 3]

# Peeking the front element
front_element = queue[0]  # Returns 2

# Checking if the queue is empty
is_empty = len(queue) == 0  # Returns False
```
#### Time Complexity: 

- enqueue (Adds an element to the back of the queue): queue.append - `O(1)`
- dequeue (Removes and returns the front element of the queue): queue.popleft() - `O(1)`. pop is also supported but it's for getting element at the end of the double-ended queue.
- peek (Returns the front element without removing it): queue[0] - `O(1)`.
- size: len(queue), `O(1)`

#### Space Complexity: 

- The space complexity of a queue is `O(N)`, where N is the number of elements in the queue.

#### In coding interviews, we see queues most often in `breadth-first search (BFS)`. Check out the `monotonic deque` later.

## Strings

A string is a sequence of characters enclosed in quotes (single, double, or triple). Strings in Python are immutable, meaning once created, they cannot be changed.

### Creating Strings

```python
# Creating strings
string1 = "Hello, World!"
string2 = 'Python is great!'
string3 = """This is a
multiline string."""
```
### Basic String Operations
#### 1. Accessing Characters:

```python
char = string1[0]  # 'H'
last_char = string1[-1]  # '!'
```

#### 2. Slicing:

```python
substring = string1[0:5]  # 'Hello'
```

#### 3. Concatenation:

```python
combined = string1 + " " + string2  # 'Hello, World! Python is great!'
```

#### 4. Repetition:

```python
repeated = "Hello! " * 3  # 'Hello! Hello! Hello! '
```

#### 5. Length:

```python
length = len(string1)  # 13
```

### Common String Methods
#### 1. Changing Case:

```python
upper_case = string1.upper()  # 'HELLO, WORLD!'
lower_case = string1.lower()  # 'hello, world!'

# title() method returns a string where the first character in every word is upper case
title_case = string1.title()  # 'Hello, World!'
```

#### 2. Finding Substrings:

```python
index = string1.find("World")  # 7
contains = "Hello" in string1  # True
```

#### 3. Replacing Substrings:

```python
new_string = string1.replace("World", "Python")  # 'Hello, Python!'
```

#### 4. Stripping Whitespace:

```python
spaced_string = "   Hello!   "
stripped = spaced_string.strip()  # 'Hello!'
```

#### 5. Splitting and Joining:

```python
words = string1.split(", ")  # ['Hello', 'World!']
joined_string = ", ".join(words)  # 'Hello, World!'
```

### String Formatting
#### 1. Old-style (%):

```python
name = "Alice"
greeting = "Hello, %s!" % name  # 'Hello, Alice!'
```

#### 2. New-style (.format()):

```python
greeting = "Hello, {}!".format(name)  # 'Hello, Alice!'
```

#### 3. f-strings (Python 3.6+):

```python
greeting = f"Hello, {name}!"  # 'Hello, Alice!'
```

### Escape Characters

#### Special characters can be included using escape sequences:

- `\'` - Single quote

- `\"` - Double quote

- `\\` - Backslash

- `\n` - New line

- `\t` - Tab

#### Example:

```python
escaped_string = "He said, \"Hello!\"\nWelcome to Python."
print(escaped_string)
# Outputs: He said, "Hello!"
# Welcome to Python.
```

### String Immutability

Strings in Python cannot be changed in place. Any operation that modifies a string will create a new string.

#### Example:

```python
original = "Hello"
modified = original.replace("H", "J")  # 'Jello'
# original is still 'Hello'
```

### Numeric and String Conversion in Python

#### 1. Numeric String Conversion

```python
print(int("123") + int("123")) # Output: 246
# The int() function converts the string "123" to the integer 123.
# The expression adds two integers: 123 + 123, which equals 246.
```

#### 2. Converting Numbers to Strings

```python
print(str(123) + str(123)) # Output: 123123
# The str() function converts the integer 123 to the string "123".
# The expression concatenates two strings: "123" + "123", resulting in "123123".
```

#### 3. Getting ASCII Values

```python
print(ord("a")) # 97
print(ord("b")) # 98
# The ord() function returns the ASCII (or Unicode) value of a character.
```

4. Joining Strings in a List

```python
strings = ["ab", "cd", "ef"]
print("".join(strings)) # Output: abcdef

# The join() method concatenates all the strings in the list strings using the specified delimiter (in this case, an empty string "").
# It combines "ab", "cd", and "ef" to produce the string "abcdef".

string1 = ["Hello", "world"]
result = " ".join(string)  # Joins with a space as the delimiter
print(result)  # Output: "Hello world"
```
<!-- 
## HashSets

```python
# HashSet
mySet = set()

mySet.add(1)
mySet.add(2)
print(mySet)
print(len(mySet))

print(1 in mySet)
print(2 in mySet)
print(3 in mySet)

mySet.remove(2)
print(2 in mySet)

# list to set
print(set([1, 2, 3]))

# Set comprehension
mySet = { i for i in range(5) }
print(mySet)
```

## HashMaps

```python
# HashMap (aka dict)
myMap = {}
myMap["alice"] = 88
myMap["bob"] = 77
print(myMap)
print(len(myMap))

myMap["alice"] = 80
print(myMap["alice"])

print("alice" in myMap)
myMap.pop("alice")
print("alice" in myMap)

myMap = { "alice": 90, "bob": 70 }
print(myMap)

# Dict comprehension
myMap = { i: 2*i for i in range(3) }
print(myMap)

# Looping through maps
myMap = { "alice": 90, "bob": 70 }
for key in myMap:
    print(key, myMap[key])

for val in myMap.values():
    print(val)

for key, val in myMap.items():
    print(key, val)
```

## Tuples

```python
# Tuples are like arrays but immutable
tup = (1, 2, 3)
print(tup)
print(tup[0])
print(tup[-1])

# Can't modify
# tup[0] = 0

# Can be used as key for hash map/set
myMap = { (1,2): 3 }
print(myMap[(1,2)])

mySet = set()
mySet.add((1, 2))
print((1, 2) in mySet)

# Lists can't be keys
# myMap[[3, 4]] = 5
```

## Heaps

```python
import heapq

# under the hood are arrays
minHeap = []
heapq.heappush(minHeap, 3)
heapq.heappush(minHeap, 2)
heapq.heappush(minHeap, 4)

# Min is always at index 0
print(minHeap[0])

while len(minHeap):
    print(heapq.heappop(minHeap))

# No max heaps by default, work around is
# to use min heap and multiply by -1 when push & pop.
maxHeap = []
heapq.heappush(maxHeap, -3)
heapq.heappush(maxHeap, -2)
heapq.heappush(maxHeap, -4)

# Max is always at index 0
print(-1 * maxHeap[0])

while len(maxHeap):
    print(-1 * heapq.heappop(maxHeap))

# Build heap from initial values
arr = [2, 1, 8, 4, 5]
heapq.heapify(arr)
while arr:
    print(heapq.heappop(arr))
``` -->
