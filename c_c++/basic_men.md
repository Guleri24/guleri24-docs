---
title: Basic Memory De/Allocation
parent: C/C++
has_children: false
nav_order: 1
---
Date: 21 Oct 2022

# Basic Memory De/Allocation

```c
    #include <stdio.h>
    #include <stdlib.h>
    
    // static
    int var = 80;
    
    int main() {
    
        // dynamic
        int *x = malloc(sizeof(int));           // give me space for one int
        int *arr = malloc(sizeof(int)*100);     // give me space for 100 int
    
        *x = 120;
    
        // OUT OF BOUNDS. This is bad arr[101] = 8;
    
    
        free(x);        // I don't want this memory anymore;
        free(arr);      // I don't want this memory anymore;
        x = NULL;
        arr = NULL;
    
        double *darr;
        darr = calloc(sizeof(double), 100);     // is the same as -- darr = malloc(sizeof(double)*100);
                                                // and also sets the bits to zero, which is helpful in
                                                // debugging
    
        darr = realloc(darr, sizeof(double)*500);       // increase the size of darr to include more data
                                                        // initial : 100
                                                        // now : 500
                                                        // realloc can be used to make blocks bigger or smaller
        darr = realloc(darr, sizeof(double)*100);       // Just remember that the address that realloc return
                                                        // could be different from the original pointer from the
                                                        // pointer to the original block and this means is there
                                                        // wasn't room for the new block and so it had to move it
                                                        // and of course it will copy the old contents to the new
                                                        // location so keep this in mind if you ever have pointers
                                                        // pointing to that original block and then you reallocate
                                                        // accessing those old copires could crash your program.
                                                        // So, we careful make sure that copies will get updated
                                                        // when you can realloc.
    
        return 0;
    }
```