# Algorithm Library

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
	auto item_1 = std::find(begin(collection), end(collection), 1);
	auto item_2 = std::find(begin(collection), end(collection), 8);

	// Print out the items if you find them.
	if (item_1 != end(collection)) std::cout << "Element found: " << *item_1 << endl;
	if (item_2 != end(collection)) std::cout << "Element found: " << *item_2 << endl;
}

// Output:
// Element found: 1
```

**Complexity**: Linear

### find_if

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
	auto item = std::find_if(begin(collection), end(collection), isBig);

	// Output the result if found
	if (item != end(condition)) std::cout << "Element found: " << *item << endl;
}

// Output:
// Element found: 500
```

### find_if_not

```cpp
#include <iostream>  // std::cout
#include <algorithm> // std::find_if
#include <vector>    // std::vector

int main()
{
	// The collection to search
	std::vector<int> collection { 1, 2, 3, 4, 5 };

	// The search predicate. True for a successful find.
	auto isOdd = [](int value) { return value & 1; };

	// Find the non-odd item in the collection
	auto item = std::find_if(begin(collection), end(collection), isBig);

	// Output the result if found
	if (item != end(condition)) std::cout << "Element found: " << *item << endl;
}

// Output:
// Element found: 2
```

### find_end
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

is_partitioned
partition
stable_partition
partition_copy
partition_point

## Min / Max Algorithms

### min
### max
### minmax
### min_element
### max_element
### minmax_element

## Permutations

### is_permutation
### next_permutation
### prev_permutation
