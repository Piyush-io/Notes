Heap sort is [[Selection Sort]] based algorithm.
- Instead of looking for maximum/minimum element in every iteration and replacing it with last/first element we use max heap data structure.
	- To do this we use Heapify function.
- It's an in-place sorting algorithm.
- It's typically not stable but can be made stable with some modifications.
- Heap sort algorithm has limited use because [[Quick Sort]] and [[Merge Sort]] are better in practice. Nevertheless, the Heap data structure itself is enormously used.
- Time complexity is O(N*logN) where N is size of the array.

# Implementation 

```cpp
// To heapify a subtree rooted with node i which is
// an index in arr[]. n is size of heap
void heapify(int arr[], int n, int i)
{
    int largest = i; // Initialize largest as root
    int l = 2*i + 1; // left = 2*i + 1
    int r = 2*i + 2; // right = 2*i + 2

    // If left child is larger than root
    if (l < n && arr[l] > arr[largest])
        largest = l;

    // If right child is larger than largest so far
    if (r < n && arr[r] > arr[largest])
        largest = r;

    // If largest is not root
    if (largest != i)
    {
        swap(arr[i], arr[largest]);

        // Recursively heapify the affected sub-tree
        heapify(arr, n, largest);
    }
}

// Main function for heap sort
void heapSort(int arr[], int n)
{
    // Build heap (rearrange array)
    for (int i = n / 2 - 1; i >= 0; i--)
        heapify(arr, n, i);

    // One by one extract an element from heap
    for (int i=n-1; i>=0; i--)
    {
        // Move current root to end
        swap(arr[0], arr[i]);

        // call max heapify on the reduced heap
        heapify(arr, i, 0);
    }
}
```

# Working

- We rearrange the array in form of a max heap.
	- With recursively calling heapify on the affected sub node.
- After each iteration we swap the root of the heap with the last element.
- And then  call heapify on the reduced heap.