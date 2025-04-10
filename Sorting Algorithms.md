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
        j = i - 1     # Index of last element in the sorted portion: j is 0 in 1st iteration

        # Move elements of arr[0..i-1] that are greater than key,
        # to one position ahead of their current position
        while j >= 0 and key < arr[j]:
            arr[j + 1] = arr[j]  # Shift the element to the right
            j -= 1               # Move left to continue checking the sorted portion

        # Insert the key in its correct position
        arr[j + 1] = key

    return arr  # Return the sorted array
```

## 4. Merge Sort
Merge Sort is a `divide-and-conquer` algorithm that sorts a list by dividing it into `smaller sublists`, sorting those sublists, and then `merging` them back together. It works by `recursively` splitting the list into halves until each sublist has only one element, which is inherently sorted. Then, it merges the sorted sublists back together to produce the final sorted list.
- Intuituin:
    - Base Case: Check if the array has more than one element.
    - Find `Midpoint`: Calculate the midpoint to split the array.
    - `Recursive` Calls: Recursively call the merge sort function for both halves.
    - `Merge` Process:
        - Initialize pointers for both halves and the main array.
        - Use a loop to compare and merge elements.
        - Handle any remaining elements after the loop.

- Time Complexity: `O(n log n)` The array is divided in half at each recursive step, which takes O(logn) time and merging the two halves takes O(n) at each level. Therefore, the overall time complexity is O(nlogn).


- Space Complexity: `O(n)` because Merge sort requires additional space for the temporary arrays (left_half and right_half) used during the merging process

```python
def merge_sort(arr):
    # Base case: if the array has more than one element
    if len(arr) > 1:
        # Find the middle index
        mid = len(arr) // 2
        
        # Divide the array into two halves
        left_half = arr[:mid]   # Left half of the array
        right_half = arr[mid:]  # Right half of the array

        # Recursively sort both halves
        merge_sort(left_half)
        merge_sort(right_half)

        # Pointers that tracks the current index of left_half, right_half, and main array
        i = j = k = 0

        # Merge the sorted halves back into the original array
        while i < len(left_half) and j < len(right_half):
            # Compare elements from both halves
            if left_half[i] < right_half[j]:
                arr[k] = left_half[i]  # Place smaller element in the original array
                i += 1  # Move to the next element in left_half
            else:
                arr[k] = right_half[j]  # Place smaller element in the original array
                j += 1  # Move to the next element in right_half
            k += 1  # Move to the next position in the original array

        # If there are remaining elements in left_half, add them to arr
        while i < len(left_half):
            arr[k] = left_half[i]  # Copy remaining elements
            i += 1
            k += 1

        # If there are remaining elements in right_half, add them to arr
        while j < len(right_half):
            arr[k] = right_half[j]  # Copy remaining elements
            j += 1
            k += 1
            
    return arr  # Return the sorted array
```

## 5. Quick Sort
Quick Sort is also a Divide and Conquer algorithm like Merge Sort, but it works differently in how it splits and combines data. It works by selecting a `pivot` element from the list and partitioning the other elements into two sub-arrays: those less than the pivot and those greater than the pivot. 
- Intuition:
    - Pick a `pivot` element from the array.
    - `Partition` the array:
        - Move all elements smaller than the pivot to its left,
        - Move all elements greater than the pivot to its right.
    - Now, the pivot is in its correct final position.
    - `Recursively` sort the left and right parts.

- Time Complexity:

  - Best: `O(n log n)`

  - Average: `O(n log n)`

  - Worst: `O(n²)` (rare, with poor pivot choices)

- Space Complexity: `O(log n)` (due to recursion)

```python
def quick_sort(arr):
    # Base case: If the array has 0 or 1 elements, it's already sorted
    if len(arr) <= 1:
        return arr  # Return the array as is

    # Choose the pivot element (middle element in this case)
    pivot = arr[len(arr) // 2]

    # Create a list of elements using list comprehension
    # less than the pivot
    left = [x for x in arr if x < pivot]    

    # equal to the pivot
    middle = [x for x in arr if x == pivot] 

    # greater than the pivot
    right = [x for x in arr if x > pivot]

    # Recursively sort the left and right parts, and concatenate the results
    return quick_sort(left) + middle + quick_sort(right)
``` 