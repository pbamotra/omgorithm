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
 23         int arr[] = {10, -99, 89, 8, 0, 0, 11, 189, 90, -90};
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

The analysis is pretty simple. The following figure describes a run instance of the above program.


[jekyll-gh]: https://github.com/mojombo/jekyll
[jekyll]:    http://jekyllrb.com
