# Insertion Sort

It is one of the simple sorting algorithms like bubble sort and selection sort.
- Its time complexity is O(N^2).
- It is an in-place and stable algorithm.
- Insertion sort is part of hybrid STL algorithms in C++ like [[Intro Sort]]. It is a combination of [[Heap Sort]] , [[Quick Sort]] and Insertion Sort.
- It is best for arrays where n(size of the array) is small.

# Working

Insertion sort works on the principle of maintaining a sorted and an unsorted array. By traversing through the unsorted array and placing each element in its correct position in the already sorted array in each iteration we get a sorted array.

## Implementation 

```cpp
#include <bits/stdc++.h>
using namespace std;

// Function to sort an array using 
// insertion sort
void insertionSort(int arr[], int n) 
{ 
    int i, key, j; 
    for (i = 1; i < n; i++)
    { 
        key = arr[i]; 
        j = i - 1; 

        // Move elements of arr[0..i-1],  
        // that are greater than key, to one 
        // position ahead of their 
        // current position
        while (j >= 0 && arr[j] > key)
        { 
            arr[j + 1] = arr[j]; 
            j = j - 1; 
        } 
        arr[j + 1] = key; 
    } 
} 

// A utility function to print an array 
// of size n 
void printArray(int arr[], int n) 
{ 
    int i; 
    for (i = 0; i < n; i++) 
        cout << arr[i] << " "; 
    cout << endl;
} 

// Driver code
int main() 
{ 
    int arr[] = { 12, 11, 13, 5, 6 }; 
    int N = sizeof(arr) / sizeof(arr[0]); 

    insertionSort(arr, N); 
    printArray(arr, N); 

    return 0; 
} ```

