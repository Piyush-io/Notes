***Sorting*** any sequence means to arrange the elements of that sequence according to some specific criterion.
It is one of the most fundamental problems in computer science.
It is used in many Algorithms.

**In-Place Sorting**: An in-place sorting algorithm uses constant extra space for producing the output (modifies the given array only). It sorts the list only by modifying the order of the elements within the list.

**Out-of-Place Sorting** : The Out-of-place sorting algorithm **uses extra space for sorting, which depends upon the size of the input**. The standard merge sort algorithm is an example of the out-of-place algorithm as it requires O(n) extra space for merging.

# TYPES OF SORTING ALGORITHMS BASED ON REQUIREMENT

1.  When we have a binary array or an array with two types of elements:
	- It is solvable using quick sort partition algorithms.
	- Methods:
		- [[Lomuto]] (Faster than Naive)
		- [[Hoare]] (Faster than Naive and Lomato)
		- Naive (Stable but requires extra space, more about stability in [[Stability of Sorting Algorithms]])
2.  Array with three possible values / or with values around a range / elements occur multiple times then:
	 - Solvable using Quick Sort Partition Algorithms.
	 - Methods:
		 - [[Lomuto]] (Faster than Naive)
		 - [[Hoare]] (Faster than Naive and Lomato)
		 - Naive (Stable but requires extra space)
3. Array of Size n and have a ***elements in a small range*** :
	- For example when we have n = 1000 and elements in range 100 to 200.
	- Method: 
		- [[Counting Sort]]
		- It has a time complexity of O(N) if range is small.
		- If range is k = 100 possible values then O(K) extra space is required and O(n+k) time.
4.  If array size if n and the range is of order n^2 or n^3 or near that :
	- Counting Sort is not used as if n = 1000 then the range would be 1000000 or 1000000000 or near that which makes Counting Sort very inefficient.
	- Method used:
		- [[Radix Sort]] 
			- Time Complexity - O(N)
			- Space - O(N)
5. Array with uniformly distributed data over a range:
	- For example 0.02 to 1.00 , there are thousand of elements in between it but in between 0.02 and 0.1 there are 100.
	- Method:
		- [[Bucket Sort]]
			- It has linear time complexity on average
6. When memory writes are costly :
	- Method:
		- [[Selection Sort]] 
			- O(N^2) time complexity in worst case.
		- [[Cycle Sort]]
			- O(N^2) but optimal in memory writes.
7. When only adjacent swaps are allowed:
	- Method:
		- [[Bubble Sort]]
		- [[Cocktail Sort]]
			- Better than bubble because in bubble sort we traverse from left to right but in cocktail sort we move traverse from both sides simultaneously.
8. When array size is small :
	- Methods:
		- [[Insertion Sort]] 
			- Best when n is around 10 to 20.
		- [[Selection Sort]]
	- Standard library algorithm switches to insertion sort when the array size if small.
9. When the available space is less :
	- Standard sorting algorithms require extra space.
	- Method:
		- [[Shell Sort]]
			- Time Complexity - O(n*log^2n) but does not require extra space.
10. When we don't know about the type of data :
	- It is mathematically proven that the time complexity can't be better than O(n*logn).
	- So for general purpose the methods used are:
		- [[Merge Sort]]
		- [[Quick Sort]]
		- [[Heap Sort]]
		- Hybrid (Used in STL) :
			- Tim Sort
				- Python function that used merge sort in general but switches to insertion sort when the array size becomes small
			- [[Intro Sort]]
				- It is the standard [[STL SORT]]
				- It is hybrid of insertion sort quick sort and heap sort.
				- When the divisions become greater than logn it switches from quick sort to heap sort and when size becomes small it switches to insertion sort.
	- Since both Merge sort and Quick Sort use [[divide and conquer]] they can be used for parallel sorting.