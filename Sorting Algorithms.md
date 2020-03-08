## Sorting Algorithms

https://medium.com/basecs/sorting-out-the-basics-behind-sorting-algorithms-b0a032873add

#### Different ways to classify a sorting algorithm

1. ##### Time complexity (Big O)

   - how much time a sorting algorithm takes with respect to the size of the data/ input

2. ##### Space complexity/ memory usage

   - how much extra space/ memory will this algorithm need to sort its input?

     - ###### in-place algorithms

       - operates directly on the input dataset and changes it
       - original input is destroyed when it is modified by the algorithm
       - more space efficient

     - ###### out-of-place algorithms

       - copies the input data, and sorts/ changes on the copied version
       - safer, but memory usage grows with input size

3. ##### Stability

   - ###### stable sorting

     - the output preserves the original order of 2 same elements, basing on their original index

   - ###### unstable sorting

     - no guarantee on the order of 2 same elements

4. ##### Internal vs external

   - ###### internal 

     - if all the items that need to be sorted are in main memory/ RAM

   - ###### external

     - if the records to be sorted cannot be stored in main memory and the sorted data occurs outside of main memory

5. ##### Recursive vs non-recursive

   - ###### recursive

     - splits the large data input into smaller inputs, recursively sorts those, and then combines the result to produce one large, sorted collection

   - ###### non-recursive

     - do not recursively call upon themselves 
     - input data is not split into a smaller subset

6. ##### Comparison vs non-comparison sort 

   - any sorting algorithm that compares 2 items at a time is a comparison sort



