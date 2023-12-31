# Selection Sort

Its one of the basic sorting algorithms used in C++.
- It has theta(N^2) time complexity in all cases.
- It is the basic idea of [[Heap Sort]] its just that in Heap sort we use [[Heap ]]data structure.
- Comparing to other algorithms it makes less memory writes but it is not optimal in its memory writes.
	- So for better/Optimal memory writes we use [[Cycle Sort]].
- It is not a stable sorting algorithm, more about that in [[Stability of Sorting Algorithms]]. 
- Also, it is an in-place sorting algorithm which means it does not require any extra space to run.

What is meant by costly memory writes?
- Here in selection sort in every iteration it writes the minimum element to the memory so in a case where the array size very large it will write the minimum element in every iteration making it not optimal in terms of memory writes. It can be the case in EEPROM where the age of the memory reduces when writing to it. Similarly a SSD where you a limit and read and writes.

# Working 
Selection sort is a simple sorting algorithm which works by finding the minimum element in the array in every iteration form the unsorted part and putting it in the beginning.

Below is the code for Selection sort:
```c++
#include <iostream>
using namespace std;

int main()
{
int arr[] = {5, 18, 2, 3, 6, 3};
int n = 6;

for (int i = 0; i < n-1; i++)
{
	int min_ind = i;
	for (int j = i+1; j < n; j++)
	{
		if (arr[j] < arr[min_ind]
			{
				min_ind = j;
			}

	}
swap(arr[min_ind],arr[i]);
}
			
for (int i = 0; i < n; i++)
{
	cout << arr[i] << " " << endl;
}
return 0;
}
```


