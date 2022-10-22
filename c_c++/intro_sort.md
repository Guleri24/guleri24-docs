---
title: IntroSort
parent: C/C++
has_children: false
nav_order: 3
---
Date: 21 Oct 2022

# In-built sort in C++ : IntroSort

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