---
title: Strucutre Malloc
parent: C/C++
has_children: false
nav_order: 2
---
Date: 21 Oct 2022

# Structure Malloc: Make use of void declared memory

```C
#include <stdio.h>
#include <stdlib.h>
#include <strings.h>

typedef struct person {
    int age;
    int height;
    int name[10];
} person_t;


int main() {
    void *ptr = malloc(100);        // Pointer to a 100 bytes of memory
                                    // Now if I want to use this memory
                                    // I can cast the whole memory to a byte array
                                    // eg.
                                    // char *p = (char*) malloc(100);
                                    // uint8_t *p = (uint8_t) malloc(100);
                                    // If I want to modify, I can access that byte
                                    // eg.
                                    // p[6] = 0xFA;
                                    //
                                    // struct person* guleri = (struct person*) p;
                                    // guleri->age = 21;

    bzero(ptr, 100);
    person_t *guleri = (person_t*) ptr;

    guleri->age = 21;
    guleri->height = 245;
    strncpy(guleri->name, "Guleri", sizeof(guleri->name) - 1);

    int *iptr = (int*) (guleri + 1);        // stick the int after the struct
    *iptr = 0xAA;

    printf("Done!\n");
    return 0;
}
```