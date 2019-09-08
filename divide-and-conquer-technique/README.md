---
description: Multi-Branched Recursion
---

# Divide and Conquer Technique

A divide-and-conquer algorithm works by **recursively breaking down a problem** into two or more sub-problems of the same or related type, until these become **simple enough to be solved directly.** The solutions to the sub-problems are then combined to give a solution to the original problem.

To adopt a divide and conquer based algorithm, first thing is to find the base case. Base case denotes the simplest sub-problem that can be solved directly. Next is the implementation of the recursive case. Recursive case deals with  dividing the problem into sub-problems and merging the solutions of the sub-problems. 

Any D&C procedure uses the following template

```text
D&C (input){
    if (base case)
        return solution
    else  /* Recursive case */
        D&C(reduced input)
        ..... /* number of recursive calls depends on the number of subproblems */
        return solution = function(solutions obtained for sub-problems)
    }
```

In the case of finding the $$n^{th}$$ Fibonacci number, the base case is when n is either 0 or 1. So, two base cases are included. In the recursive case, two sub-problems are created for \(n-1\) and \(n-2\). Addition is the function used to merge \(or\) combine the solutions.

**Intuition:** _The first number of Fibonacci series is 0  and the second number in the series is 1. All the remaining elements are obtained by finding the sum of the previous two terms in the series_

{% code-tabs %}
{% code-tabs-item title="Finding nth Fibonacci Number" %}
```text
int Fibonacci (int n)
    //The method accepts the n and prints nTH FIBONACCI number
    if(n==0)        
        return 0;
    else if(n==1)
        return 1;
    else
        return Fibonacci(n-1) + Fibonacci(n-2);
```
{% endcode-tabs-item %}
{% endcode-tabs %}

The problem with D&C are the inherent drawbacks with recursion. Recursion usually takes lot of memory space to keep track of the recursive calls \(recursion call stack\).

**Test your Understanding**

Identify the maximum depth of recursion call stack created by Fibonacci\(5\)? Here, depth refers to number of stack frames or activation records in the call stack at any point in time.

Refer to the following link to understand the call stack and its activation frame [here](https://www.cs.toronto.edu/~david/courses/csc148_f15/content/recursion/more_recursion.html)

_Also Check the Fibonacci.mp4_ 

