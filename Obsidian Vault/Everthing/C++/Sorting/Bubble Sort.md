It is the simplest sorting algorithm that works by swapping adjacent elements.
It should not be used for large data sets because its average and worst case time complexity is O(N^2) which is quite high.

Its implementation is as follows:

```c++

#include <iostream>
using namespace std;

int main()
{
int arr[] = {5, 18, 2, 3, 6, 3};
int n = 6;
for (int i = 0; i < n - 1; i++)
{
	bool swapped = false; //variable to check if swapping occurred   in between any iteration
	for (int j = 0; j < n - i - 1; j++)
	{
		if (arr[j] > arr[j + 1])
			{
				int temp = arr[j];
				arr[j] = arr[j + 1];
				arr[j + 1] = temp;
				swapped = true; //this marks that there was some swapping in the iteration
			}
	if(swapped == false)
		{
			break; //this means that if there was no swapping in the whole iteration the array is already sorted and we dont need any ![bubble-sort](https://media.geeksforgeeks.org/wp-content/cdn-uploads/gq/2014/02/bubble-sort1.png)more iterations making it more efficient
		}
	}
}
for (int i = 0; i < n; i++)
{
	cout << arr[i] << " " << endl;
}
return 0;
}
```

It doesn't require any extra space and its time complexity is made better by swapped variable.


### **How Bubble Sort Works?**  
 

Consider an array arr[] = {5, 1, 4, 2, 8}

> **First Pass:** 
> 
> - Bubble sort starts with very first two elements, comparing them to check which one is greater.
>     - ( **5** **1** 4 2 8 ) --> ( **1** **5** 4 2 8 ), Here, algorithm compares the first two elements, and swaps since 5 > 1. 
>     - ( 1 **5** **4** 2 8 ) -->  ( 1 **4** **5** 2 8 ), Swap since 5 > 4 
>     - ( 1 4 **5** **2** 8 ) -->  ( 1 4 **2** **5** 8 ), Swap since 5 > 2 
>     - ( 1 4 2 **5** **8** ) --> ( 1 4 2 **5** **8** ), Now, since these elements are already in order (8 > 5), algorithm does not swap them.
> 
> **Second Pass:** 
> 
> - Now, during second iteration it should look like this:
>     - ( **1** **4** 2 5 8 ) --> ( **1** **4** 2 5 8 ) 
>     - ( 1 **4** **2** 5 8 ) --> ( 1 **2** **4** 5 8 ), Swap since 4 > 2 
>     - ( 1 2 **4** **5** 8 ) --> ( 1 2 **4** **5** 8 ) 
>     - ( 1 2 4 **5** **8** ) -->  ( 1 2 4 **5** **8** ) 
> 
> **Third Pass:** 
> 
> - Now, the array is already sorted, but our algorithm does not know if it is completed.
> - The algorithm needs one **whole** pass without **any** swap to know it is sorted.
>     - ( **1** **2** 4 5 8 ) --> ( **1** **2** 4 5 8 ) 
>     - ( 1 **2** **4** 5 8 ) --> ( 1 **2** **4** 5 8 ) 
>     - ( 1 2 **4** **5** 8 ) --> ( 1 2 **4** **5** 8 ) 
>     - ( 1 2 4 **5** **8** ) --> ( 1 2 4 **5** **8** ) 