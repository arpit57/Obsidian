## To create a dictionary of frequency of each element in a list

``` python
def count_frequencies(arr):
    frequency_dict = {}
    
    for item in arr:
        if item in frequency_dict:
            frequency_dict[item] += 1
        else:
            frequency_dict[item] = 1
    
    return frequency_dict
```


## .sort() vs sorted()

1. Mutability:
    - `.sort()` is a method that modifies the original list in place. It sorts the elements of the list directly, and the original list is changed.
    - `sorted()` is a built-in function that returns a new sorted list. It does not modify the original list but instead creates a new list with the sorted elements.
2. Return Value:
    - `.sort()` modifies the list in place and returns `None`. It does not create a new list.
    - `sorted()` returns a new sorted list, leaving the original list unchanged.
3. Syntax:
    - `.sort()` is called on a list object using the dot notation, like `my_list.sort()`.
    - `sorted()` is a built-in function that takes an iterable (e.g., list, tuple) as an argument, like `sorted(my_list)`.
4. Applicability:
    - `.sort()` can only be used with lists since it modifies the list in place.
    - `sorted()` can be used with any iterable, including lists, tuples, strings, and even dictionaries (it sorts the keys).

Here's an example to illustrate the difference:

``` python
# Using .sort()
my_list = [3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5]
my_list.sort()
print(my_list)  # Output: [1, 1, 2, 3, 3, 4, 5, 5, 5, 6, 9]

# Using sorted()
my_list = [3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5]
new_list = sorted(my_list)
print(new_list)  # Output: [1, 1, 2, 3, 3, 4, 5, 5, 5, 6, 9]
print(my_list)   # Output: [3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5] (unchanged)
```

In the first example using `.sort()`, the original `my_list` is modified and sorted in place. The sorted list is printed directly.

In the second example using `sorted()`, a new sorted list `new_list` is created, leaving the original `my_list` unchanged. The sorted list is printed, and then the original list is printed, showing that it remains unmodified.

Both `.sort()` and `sorted()` have optional parameters, such as `key` and `reverse`, which allow for custom sorting based on a specific function or sorting in descending order, respectively.

Choose `.sort()` when you want to modify the original list and don't need the unsorted version anymore. Use `sorted()` when you want to keep the original list unchanged and obtain a new sorted list.

Copy