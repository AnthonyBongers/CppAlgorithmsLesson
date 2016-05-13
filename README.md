# C++ Algorithms

## Searching Algorithms

### find

This algorithm is used to easily find a specific value within a container. Items within the container must be comparable though by the '==' operator. 

The signature of this algorithm takes in an iterator to the first item in the collection (inclusive), an iterator to the last item in the collection (exclusive), and a reference to the value you want to search for. The return-type of the algorithm is an iterator to the found item. If it could not find the item, it will return the 'last' iterator. 

```
Function Signature:
InputIterator find (InputIterator first, InputIterator last, const T& value);
```

Here is an example of 'find' in action. It shows one example of a successful find, and another of an unsuccessful find.

```cpp
#include <iostream>  // std::cout
#include <algorithm> // std::find
#include <vector>    // std::vector

int main()
{
  // The collection to search
  std::vector<int> collection { 1, 2, 3, 4, 5 };

  // Try to find two items in the collection.
  // item_1 exists and item_2 doesn't.
  auto item_1 = std::find(collection.begin(), collection.end(), 1);
  auto item_2 = std::find(collection.begin(), collection.end(), 8);

  // Print out the items if you find them.
  if (item_1 != collection.end()) std::cout << "Element found: " << *item_1 << endl;
  if (item_2 != collection.end()) std::cout << "Element found: " << *item_2 << endl;
}

// Output:
// Element found: 1
```

**Complexity**: Linear

### find_if

std::find_if is very similar to std::find, the only difference being that instead of comparing the elements of the container directly to a value, you give a predicate function. This is useful for finding something in a container where the comparison is based off of logic instead of a direct value comparison. The return type of this algorithm is an iterator to the first element that passes the predicate, or an iterator to the end of the container if the predicate didn't match any elements.

```
Function Signature:
InputIterator find_if (InputIterator first, InputIterator last, UnaryPredicate pred)
```

Here is an example of std::find_if in action. Notice how instead of a direct comparison to a value like in std::find, we're comparing based off of some logic in a lambda. In this case, we're trying to find the first element in a container with the value greater than 100.

```cpp
#include <iostream>  // std::cout
#include <algorithm> // std::find_if
#include <vector>    // std::vector

int main()
{
  // The collection to search
  std::vector<int> collection { 1, 2, 3, 4, 500 };

  // The search predicate. True for a successful find.
  auto isBig = [](int value) { return value > 100; };

  // Find the item in the collection
  auto item = std::find_if(collection.begin(), collection.end(), isBig);

  // Output the result if found
  if (item != condition.end()) std::cout << "Element found: " << *item << endl;
}

// Output:
// Element found: 500
```

**Complexity**: Linear

### find_if_not

std::find_if_not is the complement of std::find_if. Instead of finding the first element that matches the given predicate, it returns the first element that *doesn't* match the predicate. Although useful in some scenarios, the same functionality can be achieved by using std::not1 (included through *functional*) on the predicate of std::find_if with the same result. Whichever one you choose is up to your preference. 

```
Function Signature:
InputIterator find_if (InputIterator first, InputIterator last, UnaryPredicate pred)
```

Here is an example of std::find_if_not. Here we're using a predicate to determine if a number is odd. Since we're using it in std::find_if_not, it will return the first element in the list that **isn't** odd. 

```cpp
#include <iostream>  // std::cout
#include <algorithm> // std::find_if_not
#include <vector>    // std::vector

int main()
{
  // The collection to search
  std::vector<int> collection { 1, 2, 3, 4, 5 };

  // The search predicate. True for a successful find.
  auto isOdd = [](int value) { return value & 1; };

  // Find the first non-odd item in the collection
  auto item = std::find_if_not(collection.begin(), collection.end(), isOdd);

  // Output the result if found
  if (item != condition.end()) std::cout << "Element found: " << *item << endl;
}

// Output:
// Element found: 2
```

**Complexity**: Linear

### find_end

**NOTE: Add predicate version of std::find_end**

std::find_end takes two pairs of iterators. The first pair of iterators is the range of elements that will be searched from. The seconds pair of iterators is the range of elements to search for. std::find_end will return an iterator to the **last** occurence of the second range in the first range. If the second range is empty, it will return the end of the first range.

If you are looking to find the **first** occurence of the second range in the first range, use std::search instead.

```
Function Signature:
ForwardIterator1 find_end (ForwardIterator1 first1, ForwardIterator1 last1,
                           ForwardIterator2 first2, ForwardIterator2 last2)
```

```cpp
#include <iostream>
#include <algorithm>
#include <vector>

int main()
{
  // The collection to search from
  std::vector<int> collection { 1, 2, 3, 7, 4, 9, 1, 2, 3, 5, 8 };
  
  // The collection to search for
  std::vector<int> data { 1, 2, 3 };
  
  auto found = std::find_end(collection.begin(), collection.end(), data.begin(), data.end());
  
  if (found != collection.end()) 
  {
    std::cout << "Element found at index: " << std::distance(collection.begin(), found) << std::endl;
  }
}

// Output:
// Element found at index: 6
```

### find_first_of
### adjacent_find
### search
### search_n

## Conditional Algorithms

### all_of
### any_of
### none_of
### count
### count_if
### mismatch
### equal

## Sequence Algorithms

### for_each

## Sorting Algorithms

### sort
### stable_sort
### partial_sort
### partial_sort_copy
### is_sorted
### is_sorted_until
### nth_element

## Partition Algorithms

### is_partitioned
### partition
### stable_partition
### partition_copy
### partition_point

## Min / Max Algorithms

### min

std::min is used to return the smallest value from the given arguments. 

### max
### minmax
### min_element
### max_element
### minmax_element

## Permutations

### is_permutation
### next_permutation
### prev_permutation
