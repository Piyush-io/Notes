Quick sort is a divide and conquer sorting algorithm where we partition the array around a pivot with elements smaller than it to the left of it and greater than it to right of it.

- It is not a stable algorithm, so we use merge sort when need stability of the array elements.
- Its worst case time complexity is O(N^2) but it is still considered as one of the fastest algorithms if not the fastest:
- It is an in-place algorithm.
	-  Now it uses extra space for recursion calls but doesn't use any auxiliary space to create an array unlike in merge sort, except when we use the naive method of partitioning
- It is cache friendly.
	-  Which means we can use the cache the place where we run the algorithm because it doesn't require huge space to run and cache is much faster and closer to the processor than its slower counterpart *"RAM"*.
- Its average time complexity is O(n\*logn).  
- Its a tail recursive function so it can be converted into a loop.
	- Although modern day compilers do it itself.
- Three types of partition algorithms can be used in Quick Sort
	- Naive
	- [[Lomuto]]
	- [[Hoare]]
		- More about them in there respective pages.
- We generally use Hoare partition algorithm because it take less comparisons than Lomuto partition, but Naive partition is the only one which maintains the stability of array but we don't use it because of its memory inefficiency.
- There are many different versions of quickSort that pick pivot in different ways: 
	1. Always pick first element as pivot. (Hoare)
	2. Always pick last element as pivot (Lomuto)
	3. Pick a random element as pivot.
	4. Pick median as pivot.

Its implementation is shown below: 

# Implementation

```cpp
/* This function takes last element as pivot, places
   the pivot element at its correct position in sorted
   array, and places all smaller (smaller than pivot)
   to left of pivot and all greater elements to right
   of pivot */
int partition (int arr[], int low, int high)
{
    int pivot = arr[high];    // pivot
    int i = (low - 1);  // Index of smaller element

    for (int j = low; j <= high- 1; j++)
    {
        // If current element is smaller than or
        // equal to pivot
        if (arr[j] <= pivot)
        {
            i++;    // increment index of smaller element
            swap(&arr[i], &arr[j]);
        }
    }

    swap(&arr[i + 1], &arr[high]);
    return (i + 1);
}

/* The main function that implements QuickSort
   arr[] --> Array to be sorted,
   low  --> Starting index,
   high  --> Ending index */
void quickSort(int arr[], int low, int high)
{
    if (low < high)
    {
        /* pi is partitioning index, arr[p] is now
           at right place */
        int pi = partition(arr, low, high);

        // Separately sort elements before
        // partition and after partition
        quickSort(arr, low, pi - 1);
        quickSort(arr, pi + 1, high);
    }
}
```
