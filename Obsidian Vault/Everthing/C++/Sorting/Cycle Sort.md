- It has worst case TC : O(N^2)
- It has minimum memory writes and is useful when memory writes is costly.
	- Like in case EEPROM.
- It's an in-place sorting algorithm.
- It's not a stable sorting algorithm, more about it in [[Stability of Sorting Algorithms]].
- It is useful in questions where we need to find the minimum number of swaps to sort the array.

# Implementation 

```cpp
#include <iostream>
using namespace std;
 
// Function sort the array using Cycle sort
void cycleSort (int arr[], int n)
{
    // count number of memory writes
    int writes = 0;
 
    // traverse array elements and put it to on
    // the right place
    for (int cycle_start=0; cycle_start<=n-2;   cycle_start++)
    {
        // initialize item as starting point
        int item = arr[cycle_start];
 
        // Find position where we put the item. We basically
        // count all smaller elements on right side of item.
        int pos = cycle_start;
        for (int i = cycle_start+1; i<n; i++)
            if (arr[i] < item)
                pos++;
 
        // If item is already in correct position
        if (pos == cycle_start)
            continue;
 
        // ignore all duplicate  elements
        while (item == arr[pos])
            pos += 1;
 
        // put the item to it\'s right position
        if (pos != cycle_start)
        {
            swap(item, arr[pos]);
            writes++;
        }
 
        // Rotate rest of the cycle
        while (pos != cycle_start)
        {
            pos = cycle_start;
 
            // Find position where we put the element
            for (int i = cycle_start+1; i<n; i++)
                if (arr[i] < item)
                    pos += 1;
 
            // ignore all duplicate  elements
            while (item == arr[pos])
                pos += 1;
 
            // put the item to it\'s right position
            if (item != arr[pos])
            {
                swap(item, arr[pos]);
                writes++;
            }
        }
    }
 
    // Number of memory writes or swaps
    // cout << writes << endl ;
}
 
// Driver program to test above function
int main()
{
    int arr[] = {1, 8, 3, 9, 10, 10, 2, 4 };
    int n = sizeof(arr)/sizeof(arr[0]);
    cycleSort(arr,  n) ;
 
    cout << "After sort : " <<endl;
    for (int i =0; i<n; i++)
        cout << arr[i] << " ";
    return 0;
}
```

# Working

- It's based on the idea that arrays can be divided into cycles.
- In this we start from the first element and count how many elements are smaller or equal to that element and put the element at that count and taking the element we swapped it with as our new element.
- But for the new element we only check on half right to it.
- We continue till array is sorted.