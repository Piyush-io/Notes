# Merge Sort 

It is relatively faster algorithm than some of the basic sorting algorithms like insertion sort, bubble sort and selection sort.
- It uses [[divide and conquer]] approach.
- It is stable sorting algorithm. (More about that in [[Stability of Sorting Algorithms]]). 
- It works really well for linked lists.
	- It is because unlike in array in which we need to store elements in contiguous memory, in case of linked lists the elements may not be stores continuously in the memory and we can insert elements in between them in theta(1) time and theta(1) space. Therefore the merge sort algorithm can applied on linked lists without extra space.
	- It is also the reason why sorting algorithms like quick sort and heap sort work poorly for linked lists for its poor random access speed.
- Merge Sort is outperformed by Quick Sort in case of arrays.
- Merge Sort is very useful in case of external sorting. When our data is too big to be stored in the RAM we can make use of an external storage like hard drive and take separate portions of the data and sort them and them sort them together afterwards. More about that in the link below:
	- https://www.geeksforgeeks.org/external-sorting/
- We can also make use of parallel sorting in case of Merge sort which means that we can outsource it to different processor(cores) and perform sorting faster.

# Concepts used in Merge Sort

1. First we need the idea of how to merge two sorted arrays.
2. Secondly using the above idea we need to learn how to sort two sorted portions of the same array(they should be continuous).
3. Finally third is the merge sort algorithm where we use [[Recursion]].

# Working

1. The first step of the merge sort function is the base case where we check if the array contains at least one element or not. It is given as follow:
```c++
	if(high<=low)
		return;
```

2. If the base condition is passed we move on to the second step that is to calculate the mid of the given array(low and high may not be 0 and n-1 respectively, we can also sort a part of an array).
	- It is done so as to divide the array into two halves.
1. The third step is to make a recursive call of the merge sort function where we pass the array and updated low and high which are low and mid respectively.
2. The fourth step is to repeat the third step but this time we pass low and high as mid+1 and high respectively.
3. The last step of the Merge Sort is to call the merge_array function where merge two sorted halves.

# Implementation 

```c++
#include <iostream>
using namespace std;
 
// Merges two subarrays of array[].
// First subarray is arr[begin..mid]
// Second subarray is arr[mid+1..end]
void merge(int array[], int const left, int const mid,
           int const right)
{
    auto const subArrayOne = mid - left + 1;
    auto const subArrayTwo = right - mid;
 
    // Create temp arrays
    auto *leftArray = new int[subArrayOne],
         *rightArray = new int[subArrayTwo];
 
    // Copy data to temp arrays leftArray[] and rightArray[]
    for (auto i = 0; i < subArrayOne; i++)
        leftArray[i] = array[left + i];
    for (auto j = 0; j < subArrayTwo; j++)
        rightArray[j] = array[mid + 1 + j];
 
    auto indexOfSubArrayOne
        = 0, // Initial index of first sub-array
        indexOfSubArrayTwo
        = 0; // Initial index of second sub-array
    int indexOfMergedArray
        = left; // Initial index of merged array
 
    // Merge the temp arrays back into array[left..right]
    while (indexOfSubArrayOne < subArrayOne
           && indexOfSubArrayTwo < subArrayTwo) {
        if (leftArray[indexOfSubArrayOne]
            <= rightArray[indexOfSubArrayTwo]) {
            array[indexOfMergedArray]
                = leftArray[indexOfSubArrayOne];
            indexOfSubArrayOne++;
        }
        else {
            array[indexOfMergedArray]
                = rightArray[indexOfSubArrayTwo];
            indexOfSubArrayTwo++;
        }
        indexOfMergedArray++;
    }
    // Copy the remaining elements of
    // left[], if there are any
    while (indexOfSubArrayOne < subArrayOne) {
        array[indexOfMergedArray]
            = leftArray[indexOfSubArrayOne];
        indexOfSubArrayOne++;
        indexOfMergedArray++;
    }
    // Copy the remaining elements of
    // right[], if there are any
    while (indexOfSubArrayTwo < subArrayTwo) {
        array[indexOfMergedArray]
            = rightArray[indexOfSubArrayTwo];
        indexOfSubArrayTwo++;
        indexOfMergedArray++;
    }
    delete[] leftArray;
    delete[] rightArray;
}
 
// begin is for left index and end is
// right index of the sub-array
// of arr to be sorted */
void mergeSort(int array[], int const begin, int const end)
{
    if (begin >= end)
        return; // Returns recursively
 
    auto mid = begin + (end - begin) / 2;
    mergeSort(array, begin, mid);
    mergeSort(array, mid + 1, end);
    merge(array, begin, mid, end);
}
 
// UTILITY FUNCTIONS
// Function to print an array
void printArray(int A[], int size)
{
    for (auto i = 0; i < size; i++)
        cout << A[i] << " ";
}
```

## Analysis of Merge Sort

- Merge sort take theta(n*\logn) time to sort which is faster than most sorting algorithms.
- It takes theta(n) auxiliary space(small disadvantage).
	- We can make use of some modifications to do in constant space.
- It is slower compared to quick sort in terms of array.
- It is also slower because it traverses through the whole array even if the array is sorted.