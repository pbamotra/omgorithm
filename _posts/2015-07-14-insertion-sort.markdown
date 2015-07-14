---
title:  "Insertion sort"
date:   2015-07-14 11:15:00
description: Simple implementation and analysis
---

{% highlight c %}
  1 #include <stdio.h>
  2 #include <stdlib.h>
  3 
  4 void swap(int *a, int *b) {
  5         int temp = *a;
  6         *a = *b;
  7         *b = temp;
  8 }
  9 
 10 void printArr(char *msg, int n, int arr[n]) {
 11         int i;
 12         fprintf(stdout, "%s\n", msg);
 13         fflush(stdout);
 14         for(i=0; i<n; i++) {
 15                 fprintf(stdout, "%d\t", arr[i]);
 16         };
 17         printf("\nPress ENTER to continue...");
 18         getchar();
 19 }
 20 
 21 int main(int argc, char* argv[]) {
 22 
 23         int arr[] = {10, -99, 89, 8, 0, 0, 11, 189};
 24         int n = sizeof(arr)/sizeof(int);
 25         int i,j;
 26 
 27         printArr("Before sort", n, arr);
 28 
 29         for(i=0; i<n; i++) {
 30                 j=i;
 31                 while((j>0) && (arr[j] < arr[j-1])) {
 32                         swap(&arr[j], &arr[j-1]);
 33                         j--;
 34                 }
 35         }
 36 
 37         printArr("After sort", n, arr);
 38         exit(EXIT_SUCCESS);
 39 }
{% endhighlight %}

After running,
{% highlight c %}
Before sort
10	-99	89	8	0	0	11	189	
Press ENTER to continue...
After sort
-99	0	0	8	10	11	89	189	
Press ENTER to continue...
{% endhighlight %}

The following figure describes a run instance of the above program.

![Insertion sort at work]({{ site.url }}/assets/images/insertion-sort.png)

The analysis is pretty simple. The best case when the array is already sorted in which case the only traversal is going to all the element once. The worst case is when the array is sorted in reverse order. The average case occurs when the first index element is greater than half of the elements and smaller than the other half.

Thus, best case = O(n), worst case = O(n^2), average case = O(n^2/2) = O(n^2)
