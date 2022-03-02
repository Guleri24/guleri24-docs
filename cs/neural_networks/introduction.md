---
title: Introduction
parent: Neural Networks
has_children: true
nav_order: 2
---
Date: 10 Oct 2021
# Deep Learning
Subset of Machine Learning used for NLP, computer vision, speech recognication.

- computational power
- data available
- algorithms


# Logistics Regression
goal: Find cats in images {A -> presence of a cat  
                          {O -> absence of a cat
3D image : 64 x 64 x 3 

                      3 (r, g, b) 
             64       /     
        -------------/    (  x1 ) ----\     
        |           |     |  x2 | ----\ (Wx+b | sigma fn) --> y_cap = sigma(O^T x) = sigma(Wx + b)    
   64   |           | =   |  :  | ----/
        |   \"^"/   |     |  :  | ----/
        |           |     (  xn )
        -------------   
                        flatening 
                        the image

w - weights
b - baises

Steps:
1. Initalize w, b
2. Find the optimal w, b means defininy your loss function
3. Use them to predict 

```Eq 1: Neuron = Linear + Activation```
```Eq 2: Model = Architecture + Parameters```

