# Technical Interview Study Guide
## Big-O Notation
###
## Data Structures
### Hash Tables
* **Python Data Structures**
	* Dictionaries
	* Sets
* **Performance:**
	* O(1) insertion, lookup, and deletion
* **Use Cases:**
	* When you only need to store and lookup objects (using keys, not values)
	* When you need to partition a list of objects into distinct groups by some property (basically what a group by in sql does) ***research this***
	* When you need to count the number of distinct items in a list ***research this***
* **Explanation**
	* Hash table
		* Definition: a collection of items stored in such a way you can quickly look up values for a given key. Hash tables are built on top of arrays.
	* Hash functions
		* Definition: hash functions take a key as input and map that key to an array index in a hash table using a mapping algorithm.
		* Remainder method
		* Folding method
		* Mid-square method 
	* Hash collision resolution
		* Linear probing
		* Quadratic probing
		* Chaining
* **Example Implementation**
		* (Add hash table using chaining for collision resolution)
### Linked List
* **Python Data Structures:**
* **Performance:**
	* O(1) insertion, lookup and deletion a the ends (head or tail) or next to a node you already have a pointer to.
	* O(n) for random lookup, insert, and delete (i.e. not at the head or tail)
	* O(n) space
* **Use Cases:**
	* The main use case of a linked list revolve around the fact that a linked list maintains relative ordering of elements. 
	* In programming interviews, a linked list is primarily used as either a stack or queue (due to the fact that stacks and queues only need fast operations on the ends).
	* Linked lists are also good for instances where flexible size is needed. You do not need to specify size because nodes are not stored next to each other in memory.
* **Explaination:**
* **Example Implementation (Unordered & Ordered):**
```python
class Node(object):

	def __init__(self, value):
		self.value = value
		self.next_node = None
	
	def get_value(self):
		return self.value

	def get_next_node(self): # Think of this as the previous node.
		return self.next_node

	def set_next_node(self, new_next_node):
		self.next_node = new_next_node
	
	def set_value(self, new_value)
		self.value = new_value

class LinkedList(object):

	def __init__(self):
		self.head = None # Head is the front (where new nodes are added).
	
	def is_empty(self):
		return self.head == None
	
	def add_node(self, value):
		new_node = Node(value)
		new_node.set_next_node(self.head)
		self.head = new_node

	def get_size(self):
		current = self.head # Start at the head and count backwards to tail.
		count = 0
		while current != None:
			count = count + 1
			current = current.get_next_node()
		
		return count
	
	def search(self, search_value):
		current = self.head # Start search at the head and move backwards.
		found = False
		while current != None and not found:
			if current.get_value() == search_value:
				found = True
			else:
				current = current.get_next_node()
		
		return found
	
	def delete_node(self, delete_value):
		current = self.head # Start search for node at the head
		previous = None # Track the previous node location
		found = False
		while not found: # assume provided value is in list
			if current.get_value() == delete_value:
				found = True
			else:
				previous = current
				current = current.get_next_node()
		
		if previous == None: # if it is the first item, then just re-set head 
			self.head == current.get_next_node()
		else: # if not, link the previous node to node after current
			previous.set_next_node(current.get_next_node())




	
```

### Binary Search Trees
* **Python Data Structures:**
* **Performance:**
* **Use Cases:**
* **Explaination:**
* **Example Implementation:**

### Stack
* **Python Data Structures**
		* Lists can be used as stacks
			* pop() and append() when used at the right end of the stack are O(1) time
			* Adding and removing from the front is O(n) time b/c lists are implemented as dynamic arrays
			* lookup / random accessing elements in the list is O(1) time...it's a dynamic array
* **Performance**
	* O(1) time push, pop, peek
	* O(n) space
* **Use Cases:**
	* Depth-first search uses a stack to keep track of which nodes to visit next
* **Explaination:**
* **Example Implementation:**
```python

class Stack(object):

	def __init__(self):
		self.items = []
	
	def push(self, item):
		self.items.append(item)
	
	def pop(self, item):
		return self.items.pop() # pop and return popped item
	
	def peek(self):
		return self.items[-1]
	
# Additional methods

	def is_empty(self):
		return self.stack == [] # return boolean
	
	def size(self):
		return len(self.items)
```

### Queue
* **Python Data Structures:**
* **Performance:**
* **Use Cases:**
* **Explaination:**
* **Example Implementation:**

### Array
* **Python Data Structures:**
* **Performance:**
* **Use Cases:**
* **Explaination:**
* **Example Implementation:**

### Dynamic Array
* **Python Data Structures:**
* **Performance:**
* **Use Cases:**
* **Explaination:**
* **Example Implementation:**


## Algorithms
### Binary Search
* **Performance**
	* Finds an item in a **sorted list** in O(log n) time
* **Use Cases**
	* You need to find the number in a sorted array closest to another number
	* You need to find the smallest number in a sorted array that is larger than another number
	* You need to find the largest number in a sorted array that is smaller than another number
	* If you aren't able to use a hash table for whatever reason, you can use a binary search to check if a given element is in a sorted array
* **Explanation**
	* Finds an item in a sorted list in O(log n) time by continually finding the median number in a range, determining if the search term is greater or less than the median, discarding the half not containing the search term, and repeating with the new range. 
	* In the end, either the item is found or all other possibilities are ruled out and the item is not present.
* **Example Implementation**
* ```python3
	def binary_search(search_term, search_range):
		floor = -1
		ceiling = len(search_range)
		while floor + 1 < ceiling:
			distance = ceiling - floor
			half_distance = distance // 2
			guess_index = floor + half_distance
			
			guess_value = search_range[guess_index]
			if guess_value == search_term:
				return True
			if guess_value > search_term:
				ceiling = guess_value
			if guess_value < search_term:
				floor = guess_value
		return False
     ```

### Depth-first Search
* **Performance:**
* **Use Cases:**
* **Explaination:**
* **Example Implementation:**

### Breath-first Search
* **Performance:**
* **Use Cases:**
* **Explaination:**
* **Example Implementation:**

### Bubble Sort
* **Performance:**
	* O(n^2)
	* Bubble sort is considered the most inefficient sorting algorithm because costly swaps are made before the final location of a value is determined.
	* However, bubble sort has a unique ability other sorting methods do not—namely, it can be modified to stop early if it finds a list is sorted.
	* This ability to stop early is possible because bubble sort makes passes through the entire unsorted portion of a list. If no swaps are needed, then it can be determined the list is already sorted.
	* Thus bubble sort may be a good choice if we know there will not be many passes need.
* **Use Cases:**
	*  
* **Explaination:**
	* The bubble sort is an in-place sorting algorithm.
	* The bubble sort makes multiple passes through a list, comparing adjacent items, and swapping those that are out of order. IMPORTANT: _Each pass through the list places the next largest value in its proper place to the right of lesser values._
	* Remember that lesser values will be on the left and greater values on the right. After the first pass, we know the value in the right most index is sorted/fixed, so the range we need to sort becomes shorter.
	* How many passes will be required? A pass constitutes a number of value comparisons between pairs from left to right. The first comparison takes the first number in the list (index 0) and compares it to its neighbor on the right (index 0 + 1). If the value in index 0 is greater than the value in index 0 + 1, then the two are swapped. Now the new, greater value in index 1 is compared with index 1 + 1 and so on. Thus the first pass will contain n - 1 comparisons (there is not need to compare index 0 with itself.) The second pass will contain n - 2  comparisons because the first pass shortened the list of values needing sorting by moving the largest value in the list to the right most (last) index. The third pass will containe n -3 comparisons and so on. In total, the number of passes required is n -1.  

* **Example Implementation:**
```python
# Basic bubble sort without mechanism to stop early when sorted
def bubble_sort(alist):
	for pass_num in range(len(alist) -1, 0, -1): # Passes 
		for i in range(pass_num): # Compare pairs in pass
			if alist[i] > alist[i+1]:
				temp = alist[i]
				alist[i] = alist[i +1]
				alist[i +1] = temp
			else: # no swap, skip to next comparison
				pass

# Improved bubble sort that will stop early when sorted
def short_bubble_sort(alist):
	swaps = True
	pass_num = len(alist) - 1
	while pass_num > 0 and swaps:
		swaps = False
		for i in range(pass_num):
			if alist[i]>alist[i+1]:
				swaps = True
				temp = alist[i]
				alist[i] = alist[i +1]
				alist[i +1] = temp
		passnum += -1
```

### Selection Sort
* **Performance:**
	* O(n^2)
	* Similar approach to the bubble sort. This algorithm makes the same number of comparisons, but only makes one swap per pass.
* **Use Cases:**
* **Explaination:**
	* Same approach of passes and comparisons as bubble sort.
	* Selection sort finds the max value on each pass (by comparing to the current max value), then moves the max value to its proper position on the right.
* **Example Implementation:**
```python
def selection_sort(alist):
	for fill_slot in range(len(alist)-1,0,-1): # passes
		max_value_idx = 0 # first value is default max
		for idx in range(1, fill_slot+1): # start at 1 since 0 is max
			if alist[idx] > alist[max_value_idx]:
				max_value_idx = idx
			
		temp = alist[fill_slot]
		alist[fill_slot] = alist[max_value_idx]
		alist[max_value_idx] = temp
```

### Insertion Sort
* **Performance:**
	* O(n^2)
* **Use Cases:**
* **Explaination:**
	* Insertions works differently than bubble and selection sorting.
	* Insertion starts with a sorted sublist of 1 value at index 0. Then with each pass another value to the right is added to the sorted sublist. The value to be sorted is compared to the next value in the sorted sublist as it moves left. If the value to be sorted is smaller than the next sublist value on the left, the larger value is _shifted_ over. The place the larger value used to occupy becomes a placeholder. The placeholder will be written over with the next term larger than the value to be sorted. This process is repeated until either the next value in the sublist is smaller than the value to be sorted or we reach index 0. At this point the placeholder is written over with the sort value and we have a completely sorted sublist.
	* There are n-1 such passes. The number of shift operations need will vary depending on input.
	* IMPORTANT: the swap operation performed by the bubble and selection sort methods is different than shift operation performed by the insertion sort method. The shift operation requires 1/3 of the processing resources than swaps due to the single assignment. Insertion sort performs well in benchmarking.
* **Example Implementation:**
```python
def insertion_sort(alist):
	for index in range(1,len(alist)): # 0 is already in our sorted sublist
		sort_value = alist[index]
		pos = index
		while pos > 0 and alist[pos-1]>sort_value: # compare sort value and value to the left
			alist[pos] = alist[pos-1] # shift larger value right
			pos = pos -1 # new sort_value placeholder 
		
		alist[pos] = sort_value # assign sort_value to placeholder
```

### Shell Sort
* **Performance:**
* **Use Cases:**
* **Explaination:**
* **Example Implementation:**

### Merge Sort
* **Performance:**
* **Use Cases:**
* **Explaination:**
* **Example Implementation:**

### Quick Sort
* **Performance:**
* **Use Cases:**
* **Explaination:**
* **Example Implementation:**


### Additional Resources:
* [Dan Bader's (founder Real Python) Fundamental Data Structures in Python](https://dbader.org/blog/fundamental-data-structures-in-python)
* [Python Time Complexity for Data Structures](https://wiki.python.org/moin/TimeComplexity)



