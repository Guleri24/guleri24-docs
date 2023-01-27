---
title: Visual Studio Tips
parent: A Linux User In Pain
has_children: false
nav_order: 5
---
Date: 21 Jan 2023

# Visual Studio and VS Code Tips

## What is the relationship between Visual Studio and Visual Studio Code?
It's kind of the same relationship that Java has to JavaScript, 
the Ham has to Hamster,
and the car has to carpet. 

Lines from Chris Heilmann [ What is the relationship between Visual Studio and Visual Studio Code?, One Dev Question ](https://youtu.be/qjAlmlHr-7E)

## Visual Studio

### Remove initial splash screen
1. Right Click on Visual Studio shortcut ->
2. Select "Property" 
3. In the Target field add "/nonsplash" argument in the end of Target value

    "C:\Program Files\Microsoft Visual Studio\2022\Community\Common7\IDE\devenv.exe" /nosplash

## VS Code

### Open files always in new tab
1. open command palette (Ctrl + Shift + P ) 
2. type Preferences: Open User Settings 
3. Search workbench.editor.enablePreview 
4. disable all of these

### Autosave
1. File 
2. Preferences 
3. Setting 
4. Search auto save 
5. In the Files: `Auto Save select after delay`