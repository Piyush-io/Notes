
The need for stability comes into play when we need to sort an array with items with multiple fields for example key value pairs and there are items in with duplicate keys and we wish to sort them by their keys.

***Stable sorting algorithms are not needed for arrays like integer array or for arrays where the keys are the whole element.***

# What are stable sorting algorithms ?

Stable sorting algorithms preserve the order of the original array. It means that if we have a duplicate keys for example in an array then after sorting the pair which occurred first in the original array would also come first in the sorted array.

### For example:

```c++
arr[] = {("Anil",50)("Aman",80){"Piyush",50}("Umesh",80)};
```

It is evident that after sorting the order of the array would be 50 50 80 80 when sorting according to the keys.
Now if we will be using a stable sorting algorithm then in the modified array(sorted array) *Anil* will come **before** *Piyush* because in the original array Anil occurs first and similarly *Umesh* will come **after** *Aman*.
It would look something like this:
```c++
arr[] = {("Anil",50)("Piyush",50)("Aman",80)("Umesh",80)}
```

Examples of Unstable Sorting algorithms include [[Heap Sort]] , [[Quick Sort]] , [[Selection Sort]].
Some examples of stable sorting algorithms include [[Bubble Sort]] , [[Merge Sort]] and [[Insertion Sort]].

If we take Selection Sort and Bubble sort for example:
- Bubble sort is stable because it does adjacent comparisons and doesn't swaps an element unless its bigger than the next element. So if an element was equal to the adjacent next element it would retain its place, hence its a stable algorithm.
- On the other hand in the case of selection sort in every iteration it find the biggest element it replaces it with the last element. So for example:
	- An array was [2 , 18 , 3 , 5 , 3 ], in this array when we find 18 as the max element we replace it as 3 and this would make the 3 in middle occur after the 3 that was placed last in the original array, thus making it an unstable sorting algorithm.


## **Can we make any sorting algorithm stable?** 

Any given sorting algorithm which is not stable can be modified to be stable. In general, any comparison-based sorting algorithm which is not stable by nature can be modified to be stable by changing the key comparison operation so that the comparison of two keys considers position as a factor for objects with equal keys.