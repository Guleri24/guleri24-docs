---
layout: default
title: Max SubArray Sum 
parent: Problems
grand_parent: Computer Science
has_children: false
nav_order: 1
permalink: /cs/problems/max_sub_array_sum/
---
Date: 28 Aug 2022

# Max SubArray Sum
Given an array of n numbers, our task is to calculate the maximum subarray sum, i.e., the largest 
possible sum of a sequence of consecutive values in the array . The problem is interesting when 
there may be negative values in the array.

Example: 

`> int[] arr = {-4, 5, 7, -6, 10, -15, 3}`

`> 16 // {5, 7, -6, 10}`

```java
int MaxSubArrSum(int[] arr) {
    int best = arr[0];
    int sum = arr[0];

    for (int i = 0; i < arr.length; i++) {
        for (int j = i; i < arr.length; j++) {
            sum = Math.max(arr[j], sum + arr[j]);
            best = Math.max(best, sum);
        }
    }
    return best;
}
```
Complexity: O(n^2)


