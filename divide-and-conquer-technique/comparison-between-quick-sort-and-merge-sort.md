---
description: When to use What??
---

# Comparison Between Quick Sort & Merge sort

Merge Sort requires an auxiliary array to support the sorting process. The sorted sub-arrays are merged using a temporary array which is then used to replace the elements in the original array at the end of the merge operation. At the same time, it produces T\(n\) = $$\theta(nlogn)$$ irrespective of the input instance.

Merge sort is **stable, \(i.e\)** relative ordering of equal valued elements are maintained after the sorting process. Merge procedure can be applied for **external sorting** \(Wherein the array does not fit in the main memory completely\)

Quick Sort does not require auxiliary space and its worst case scenario can be avoided using randomized Quick sort . Hence, it is preferred more than merge sort in many applications. Quick sort is **not stable** as the ordering of equal elements are not preserved. Since, Quick sort is a tail recursive procedure, tail level optimizations are carried out making it much faster than the merge sort.

C++ STL \(Standard Template library\) offers sort\(\) method which adopts **introsort, \(hybrid sorting algorithm\); combination of both Quick Sort and Heap Sort.** It applies Quick sort and when the recursion depth exceeds a certain value, it switches to heap sort.

**Test Your Understanding:**

1. You have to sort 1 GB of data with only 100 MB of available main memory. Which sorting technique will be most appropriate? \[Merge procedure can be applied on sorted sub-arrays which produces final sorted array in O\(n\)\]
2. In a modified merge sort, the input array is splitted at a position one-third of the length\(N\) of the array. Provide the tightest upper bound on time complexity of this modified Merge Sort.\[ recurrence relation is given by  $$T(n) = T(n/3) + T(2n/3) + \theta(n) $$ Hence, T\(n\) = $$O(nlogn)$$ \]
3. A list of n string, each of length n, is sorted into lexicographic order using the merge-sort algorithm. What will be the worst case running time of this computation? \[ $$O(n^{2} logn)$$ \]
4. What is the best sorting algorithm to use for the elements in array are more than 1 million in general? \[Quick Sort\]

