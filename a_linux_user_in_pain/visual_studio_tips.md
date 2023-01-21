---
title: Visual Studio Tips
parent: A Linux User In Pain
has_children: false
nav_order: 5
---
Date: 21 Jan 2023

# Visual Studio Tips

## What is the relationship between Visual Studio and Visual Studio Code?
It's kind of the same relationship that Java has to JavaScript, 
the Ham has to Hamster,
and the car has to carpet. 

Lines from Chris Heilmann [ What is the relationship between Visual Studio and Visual Studio Code?, One Dev Question ](https://youtu.be/qjAlmlHr-7E)

## Remove initial splash screen
1. Right Click on Visual Studio shortcut ->
2. Select "Property" 
3. In the Target field add "/nonsplash" argument in the end of Target value

    "C:\Program Files\Microsoft Visual Studio\2022\Community\Common7\IDE\devenv.exe" /nosplash