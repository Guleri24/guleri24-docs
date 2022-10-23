---
title: IntroSort
parent: C/C++
has_children: false
nav_order: 3
---
Date: 21 Oct 2022

# In-built sort in C++ : IntroSort
It's a hybrid sorting algorithm, which means that it uses more than one sorting algorithms as
routine.
Uses three sorting algorithm to minimise the running time:
    Quick Sort
    Heap Sort
    Insertion Sort

## How does it work?
Introsort begins with quicksort and if the recursion depth goes more than a particular
limit it switches to Heapsort to avoid Quicksort’s worse case O(N^2) time complexity.
It also uses insertion sort when the number of elements to sort is quite less. So first
it creates a partition.
Three cases arises from here.
1. If the partition size is such that there is a possibility to exceed the maximum depth
limit then the Introsort switches to Heapsort. We define the maximum depth limit as 2*log(N)
2. If the partition size is too small then Quicksort decays to Insertion Sort. We define
this cutoff as 16 (due to research). So if the partition size is less than 16 then we will
do insertion sort.
3. If the partition size is under the limit and not too small (i.e - between 16 and 2*log(N)),
then it performs a simple quicksort.

## Is Introsort stable ?
Since Quicksort is also not stable so Introsort is also not stable.

## Time Complexity:
    Best Case – O(N log N)
    Average Case - O(N log N)
    Worse Case - O(N log N) where, N = number of elements to be sorted.
Auxiliary Space Just like quicksort, it may use O(log N) auxiliary recursion stack space.
```cpp

    #include <bits/stdc++.h>
    using namespace std;
    
    
    /*
    * Cpp has inbuild sort function which uses IntroSort (Introspective Sort) which is a
    * hybrid sorting algorithm that provides both fast average performance and
    * (asymptotically) optimal worst-case performance.
    *
    * Worst-case perfromance: O(n log n)
    *
    * Use: sort(address_of_start, address_of__end_+_next);
    *      sort(a, a+n);
    */
    
    bool isSwapNeeded(int x, int y) {
        return x > y ? true : false;
        }
    
    bool isSwapNeeded(pair<int, int> x, pair<int, int> y) {
        if (x.first != y.first) {
            return x.first > y.first ? true : false;
        } else {
            return x.second < y.second ? true : false;
        }
    }
    
    int main() {
        int n;
        cout << "Enter number of elements, n = ";
        cin >> n;
    
        int a[n];
        cout << "Enter n elements for array a " << endl;
        for (int i = 0; i < n; ++i) {
            cin >> a[i];
        }
    
        sort(a, a + n);
        for (int i = 0; i < n; ++i) {
            cout << a[i] << " ";
        }
        cout << endl;
    
    
        // Change starting address
        int b[n];
        cout << "Enter n elements for array b " << endl;
        for (int i = 0; i < n; ++i) {
            cin >> b[i];
        }
    
        sort(b+2, b+n);
        cout << "only elements in range 3 -> n are sorted in b" << endl;
        for (int i = 0; i < n; ++i) {
            cout << b[i] << " ";
        }
        cout << endl;
    
        // Vector
        vector<int> v(n);
        cout << "Enter n elements for vector v " << endl;
        for (int i = 0; i < n; ++i) {
            cin >> v[i];
        }
    
        sort(v.begin(), v.end());
        for (int i = 0; i < n; ++i) {
            cout << v[i] << " ";
        }
        cout <<  endl;
    
        // Without Comparator Function
        int arr[n] = {5, 4, 3, 2, 1};
        cout << "Enter n elements for array arr " << endl;
        for (int i = 0; i < n; ++i) {
            cin >> v[i];
        }
    
        for (int i = 0; i < n; ++i) {
            for (int j = 0; j < n; ++j) {
                if (isSwapNeeded(arr[i], arr[j])) {
                    swap(arr[i], arr[j]);
                }
            }
        }
    
        vector<pair<int, int> > vp(n);
        cout << "Enter n element pairs for vector vp (e.g. 1 2) " << endl;
        for (int i = 0; i < n; ++i) {
            cin >> vp[i].first >> vp[i].second;
        }
    
        for (int i = 0; i < n; ++i) {
            for (int j = 0; j < n; ++j) {
                if (isSwapNeeded(vp[i], vp[j])) {
                    swap(vp[i], vp[j]);
                }
            }
        }
        for (int i = 0; i < n; ++i) {
            cout << vp[i].first << " " << vp[i].second << endl;
        }
        return 0;
    }
```