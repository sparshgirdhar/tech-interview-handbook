# Sorting Algorithms

Sorting algorithms are used to arrange the elements of a list or array in a specific order (typically ascending or descending). Here’s a breakdown of some common sorting algorithms:

## 1. Selection Sort
Selection sort works by repeatedly finding the minimum element from the unsorted portion of the array and swapping it with the first element of that unsorted portion, effectively building a sorted array from the beginning.

- Intuition:
    - `Divide and Conquer`: Implicitly divides the array into two parts: a sorted portion (initially empty) and an unsorted portion (initially the entire array). 
    - `Find the Minimum`: In each iteration, the algorithm finds or `selects` the smallest element within the unsorted portion. 
    - `Swap`: The smallest element is then swapped with the first element of the unsorted portion, effectively moving it to its correct sorted position. 
    - `Repeat`: This process of finding the minimum and swapping is repeated until the entire array is sorted. 

- Time Complexity: `O(n²)`

- Space Complexity: `O(1)`

```python
def selection_sort(arr):
    n = len(arr)
    for i in range(n):
        # Assume the minimum element is the first in the unsorted portion
        min_index = i

        # Check the remaining unsorted elements
        for j in range(i+1, n):
            # If a smaller element is found, update min_index
            if arr[j] < arr[min_index]:
                min_index = j
                
        # Swap the found minimum element with the first element of the unsorted portion,
        # effectively moving it to its correct sorted position.
        arr[i], arr[min_index] = arr[min_index], arr[i]
    return arr
```

## 2. Bubble Sort
Bubble Sort is a sorting algorithm that repeatedly steps through the list, compares `adjacent elements`, and `swaps` them if they are in the wrong order. The process is repeated until the list is sorted. It is called Bubble Sort because bigger elements `bubble` to the end of the list.

- Intuition:
    - `Comparison and Swapping`: Comparing each pair of adjacent elements in the list. If the element on the left is greater than the element on the right, they are swapped.
    - `"Bubbling" to the End`: After the first pass, the largest element will be at the end of the list. With each subsequent pass, the next largest element "bubbles" up to its correct position, moving towards the end of the list. 
    - `Repeated Passes`: This process of comparing and swapping is repeated until the entire list is sorted. 

- Time Complexity:

    - Best: `O(n)` - when the list is already sorted or almost sorted

    - Average: `O(n²)`

    - Worst: `O(n²)`

- Space Complexity: `O(1)`

```python
def bubble_sort(arr):
    n = len(arr)

    for i in range(n):
        for j in range(0, n-i-1):
            # Compare adjacent elements
            if arr[j] > arr[j+1]:
                # Swap if the current element is greater than the next
                arr[j], arr[j+1] = arr[j+1], arr[j]
    return arr
```

## 3. Insertion Sort
Insertion Sort is a sorting algorithm that builds a sorted array one element at a time by repeatedly taking the next element from the unsorted part and `inserting` it into the correct position in the sorted part.

- Intuition:
    - `Start with a Sorted Portion`: Imagine that you have a hand of playing cards. At the beginning, you consider the first card to be sorted.
    - `Pick the Next Element`: Take the next unsorted element from the list.
    -  `Insert it in the Correct Position`: Compare this element with the elements in the sorted portion and insert it into its correct position. This involves shifting larger elements to the right to make space for the new element.
    - `Repeat`: Continue this process until all elements are sorted.

- Time Complexity:

  - Best: `O(n)`

  - Average: `O(n²)`

  - Worst: `O(n²)`

- Space Complexity: `O(1)`

```python
def insertion_sort(arr):
     # Get the length of the array
    n = len(arr)
    
    # Traverse through the array starting from the second element
    for i in range(1, n):
        key = arr[i]  # The current element to be inserted into the sorted portion
        j = i - 1     # Index of last element in the sorted portion - j is 0 in 1st iteration

        # Move elements of arr[0..i-1] that are greater than key,
        # to one position ahead of their current position
        while j >= 0 and key < arr[j]:
            arr[j + 1] = arr[j]  # Shift the element to the right
            j -= 1               # Move to the left in the sorted portion till it is at 0

        # Insert the key in its correct position
        arr[j + 1] = key

    return arr  # Return the sorted array
```

## 4. Merge Sort
- Description: A divide-and-conquer algorithm that splits the list into halves, sorts each half, and merges them back together.

- Time Complexity: O(n log n)

- Space Complexity: O(n)

```python
def merge_sort(arr):
    if len(arr) > 1:
        mid = len(arr) // 2
        left_half = arr[:mid]
        right_half = arr[mid:]

        merge_sort(left_half)
        merge_sort(right_half)

        i = j = k = 0

        while i < len(left_half) and j < len(right_half):
            if left_half[i] < right_half[j]:
                arr[k] = left_half[i]
                i += 1
            else:
                arr[k] = right_half[j]
                j += 1
            k += 1

        while i < len(left_half):
            arr[k] = left_half[i]
            i += 1
            k += 1

        while j < len(right_half):
            arr[k] = right_half[j]
            j += 1
            k += 1
    return arr
```

## 5. Quick Sort
- Description: A divide-and-conquer algorithm that selects a "pivot" element, partitions the array around the pivot, and recursively sorts the sub-arrays.

- Time Complexity:

  - Best: O(n log n)

  - Average: O(n log n)

  - Worst: O(n²) (rare, with poor pivot choices)

- Space Complexity: O(log n) (due to recursion)

```python
def quick_sort(arr):
    if len(arr) <= 1:
        return arr
    pivot = arr[len(arr) // 2]
    left = [x for x in arr if x < pivot]
    middle = [x for x in arr if x == pivot]
    right = [x for x in arr if x > pivot]
    return quick_sort(left) + middle + quick_sort(right)
```