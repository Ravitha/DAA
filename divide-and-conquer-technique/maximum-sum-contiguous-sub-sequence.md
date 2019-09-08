---
description: Identify the positive contiguous sub-sequence with maximum sum
---

# Maximum Sum Contiguous Subsequence

#### Problem Statement:

Given an array of positive and negative integers, identify the sub-sequence \(set of contiguous elements\) with maximum sum**.** 

**Assumptions:** 

1. A sub-sequence contains one \(or\) more elements.
2. There will always be one positive sub-sequence in the array

**Approach 1: Naive Searching**

At every index position, check for all possible sub-sequences starting with that index position. Finally, output the sub-sequence with maximum value. 

{% code-tabs %}
{% code-tabs-item title="Maximum Sum Subarray \(Brute Force Approach\)" %}
```text
int MaxSum1(int A[], int n){
	int result=0;
	int sum;
	for(int i=0;i<n;i++){
		sum=A[i];
		for(int j=i+1;j<n;j++){
			sum=sum+A[j];
			if(result<sum){
				result = sum;
			}
		}
	}
	return result;
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Time Complexity Analysis : Number of sub-sequences considered = $$O(n^{2})$$ 

#### Approach 2: Using Divide and Conquer

**Base case :** When the array contains only one element, the maximum sum is the element itself

**Recursive case:** Sub-problems find the maximum sum recorded in a sub-array. To find the solution to the problem, \(i.e\) To Find the maximum sum sub-sequence for the entire array

1. It may be the sub-sequence with maximum value in the  left sub-array \( $$Sum_{left}$$\)
2. It may be the sub-sequence with maximum value in the  right sub-array \( $$Sum_{right}$$ \)
3. It may be a sub-sequence which starts in the left sub-array and ends in the right sub-array. To find this , use O\(n\) search adding up elements one after other starting from midpoint to the first element in the left sub-array and record the maximum obtained value . Repeat the same from position mid+1 to the last element in the left sub-array

Maximum sum across the mid-point for the array $$Sum_{midpoint}$$   = Maximum sum obtained from mid-point to first element in left sub-array + Maximum sum obtained from position mid-point + 1 to the last element in the right sub-array.

Thus, the recursive case finds the maximum sum using the solutions $$Sum_{left}, Sum_{right}, Sum_{midpoint}$$ 

Maximum Sum = $$max(Sum_{left},Sum_{right},Sum_{midpoint})$$ 

{% code-tabs %}
{% code-tabs-item title="Divide and Conquer Approach" %}
```text
int Maximum(int val1, int val2, int val3){
	return ((val1>val2)&&(val1>val3))?val1:((val2>val1)&&(val2>val3))?val2:val3;
}

int MaxSum2(int A[], int low, int high){

	if(low==high){
		return A[low];
	}
	else{
		int mid = (low+high)/2;
		int val1 = MaxSum2(A,low,mid);
		int val2 = MaxSum2(A,mid+1,high);
		int val3 = midpointSum(A,low,mid,high); // Merge Operation
		int m =Maximum(val1,val2,val3);
		printf("low:%d mid:%d high:%d m:%d\n", low,mid,high,m);
		return m;
	}
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="Merge procedure for D& C" %}
```text

int midpointSum(int A[], int low, int mid, int high){
	int MaxLeft = 0, MaxRight=0;
	int lsum=0, rsum=0;
	int i;
	for(i=mid;i>=low;i--){
		lsum = lsum + A[i];
		if(MaxLeft<lsum){MaxLeft=lsum;}
	}
	for(i=mid+1;i<=high;i++){
		rsum = rsum+A[i];
		if(MaxRight<rsum){MaxRight = rsum;}
	}

	return MaxLeft+MaxRight;
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Time Complexity analysis : T\(n\) = 2T\(n/2\) + O\(n\). By using master's theorem, T\(n\)= $$\theta(nlogn)$$ 

**Approach 3: Iterative method**

**Intuition :** negative sub-sequences affect the sum

Maintain sum variable and Iteratively add elements to the sum. Also keep track of the maximum sum recorded. Whenever the sum reaches a negative value, restart the procedure by initializing sum to zero

{% code-tabs %}
{% code-tabs-item title="Kadane\'s algorithm for finding maximum sub array" %}
```text
int MaxSum3(int A[], int low, int high){

	int max_so_far = 0;
	int max_ending_here = 0;

	for(int i=low;i<=high;i++){
		max_ending_here = max_ending_here + A[i];
		if(max_ending_here < 0)
			max_ending_here = 0;
		if(max_so_far < max_ending_here)
			max_so_far = max_ending_here;
	}

	return max_so_far;
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Time Complexity analysis : Array is scanned only once. Hence records a T\(n\) = O\(n\)

