19 nov 2019

## Data Structure & Algorithms

#### Time complexity

- find the relationship between time and the number of elements

- usually the coefficients are dropped because what is important is the shape of the graph 

  

#### Sequential Search

Example - searching through a sequential search

best case = constant time 

- when the search item is the first item in the array

worse case = linear time

- when the search item is the last item in the array



**measuring time** = depends on the input size

- depends on the machine instruction



##### Asymptotic notation

- 6n^2 + 100n + 300 - where n is the number of items in the array
- when the n increases to a very large value, essentially the 100n + 300 run time becomes insignificant
- thus the 6n^2 becomes the more significant time



##### Big - Theta notation

- represents the tight bound

- best case = theta 1
- average case = 1/2(n+1) = theta n
  - drops all the coefficient and constant as they are not significant
- worse case = n = theta n



##### Big O notation

- upper bound of an algorithm



https://www.bigocheatsheet.com/



#### Binary Search

- splitting the elements into half to search
- assumption that input has already been sorted
- know when the element does not exist when high(index) becomes lesser than the low(index)

 

levels and nodes (elements) 

time complexity = O(log(n))



https://visualgo.net/en



#### Bubble Sort

- by always swapping the 2 elements in the array to sort the largest number to the end
- Best =  already sorted - O(n)
- average = purely random = O(n^2)
- worse = opposite 





#### Comparison sort

- bubble sort
- insertion sort
- selection sort
- heap sort
- merge sort (>30 elements) - O(nlogn)
  - divide array to a one element array then merge it back again
  - recursively sort = magically assume that they are already sorted 
  - not a stable sort 
- quick sort (>30 elements) - O(nlogn)



- why merge sort vs quick sort



#### Non-comparison sort

- counting sort - when there is alot of duplication in the numbers - O(n + k )
  - k is the number of duplicate elements
- radix sort



#### data types in javascript

- 7 type



#### data structures

- objects
- arrays



#### Abstract data structures

- stacks - push, pop, peek eg. pringle can 
  - LIFO - last in first out
- queue - dequeue, enqueue, peek
  - FIFO - first in first out
- linked list - class node and class linkedlist 
  - the class linked list is referencing another class node
  - inserting is on O(n) as it needs to traverse the length of the array so it depends on the length of the array
- hash map
- tree



#### Array sizing

- memory allocation of arrays
- always in the size of 2^n



- fixed length arrays