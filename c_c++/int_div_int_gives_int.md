---
title: Dividing by same uint8_t value gives 1 but required float
parent: C/C++
has_children: false
nav_order: 4
---
Date: 13 Feb 2023

Coverity issue related study:
Problem: Dividing by same uint8_t value gives 1 but required float 
Description : Dividing by same uint8_t value gives 1 but required float as the variable it is going
to be is of type float

https://stackoverflow.com/questions/16221776/why-dividing-two-integers-doesnt-get-a-float
https://stackoverflow.com/questions/34978843/most-efficient-way-to-convert-uint8-to-float-of-range-0-1
https://stackoverflow.com/questions/25767705/how-can-i-convert-uint8-t-and-uint16-t-into-floats-in-c


Note: 
the std::cout printed 5, even though we typed in 5.0. By default, std::cout will not print the fractional
part of a number if the fractional part is 0.https://www.learncpp.com/cpp-tutorial/floating-point-numbers/

```cpp
#include<iostream>
#include<stdint.h>
#include <typeinfo>
using std::cout;
using std::endl;

int main() {
	uint8_t i = 15;
	uint8_t j = 15;

	cout 
	<< "i                                             = " << unsigned(i) << ";\n" 
	<< "j                                             = " << unsigned(j) << ";\n" 
    << "static_cast<int>(i)                           = " << static_cast<int>(i)  << ";\n" 
    << "static_cast<int>(j)                           = " << static_cast<int>(j)  << ";\n" 
	<< "j                                             = " << unsigned(j) << ";\n" 
	<< "i / j                                         = " << i / j << ";\n" 
	<< "float(i) / j                                  = " << float(i) / j << ";\n" 
	<< "i / float(j)                                  = " << i / float(j) << ";\n" 
	<< "float(i) / float(j)                           = " << float(i) / float(j) << ";\n" 
	<< "static_cast<float>(i / j)                     = " << static_cast<float>(i / j) << ";\n" 
	<< "static_cast<float>(i) / static_cast<float>(j) = " << static_cast<float>(i) / static_cast<float>(j) << ";\n" 
	<< "static_cast<float>(i) / j                     = " << static_cast<float>(i) / j << ";\n" 
	<< "i / static_cast<float>(j)                     = " << i / static_cast<float>(j) << ";" << endl;


    float x = static_cast<float>(i) / static_cast<float>(j);
	cout << x << endl;
	x = i / j;
    cout << x << endl;
	x = static_cast<int>(i) / static_cast<int>(j);
	cout << x << endl;
	x = (float)(i /j);
	cout << x << endl;
	x = (float)(i) / (float)(j);
	cout << x << endl;

	float a = static_cast<int>(j) * 1.0f;
	cout << a << endl;

	x = (float)(i) / j;
	cout << x << endl;
	float h = x + 1.00f;
	cout << h << endl;

	cout << i / (float)j << endl;
	if (x == 1) x = 5.01f;
	cout << x << endl;

	cout << typeid(i).name() << endl;
}
```

```
g++ test.cpp && ./a.out 
i                                             = 15;
j                                             = 15;
static_cast<int>(i)                           = 15;
static_cast<int>(j)                           = 15;
j                                             = 15;
i / j                                         = 1;
float(i) / j                                  = 1;
i / float(j)                                  = 1;
float(i) / float(j)                           = 1;
static_cast<float>(i / j)                     = 1;
static_cast<float>(i) / static_cast<float>(j) = 1;
static_cast<float>(i) / j                     = 1;
i / static_cast<float>(j)                     = 1;
1
1
1
1
1
15
1
2
1
5.01
h
```