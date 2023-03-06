# Applying the Sphinx Theme to Old Lessons

This repo will describe how to apply the new Sphinx theme to lessons which were originally developed with the Software Carpentry Template.
In order to maintain author contributions, I recommend directly overriding the existing lesson markdown files.

I have included a (not very robust) script which uses regex to make a first pass at converting lessons. 
Notably it does not get call outs or exercises, those will have to be converted by hand (unless someone wants to contribute more to the regex!)

You can run

```
python convert.py 00_lesson_name.md
```

You will get `out.txt` containing partially reformatted text. You can put this into the MD file and build with Sphinx to see what else needs to be changed.

## Building the Lessons

You can build the lessons using the following command in the `_episodes` folder.

```
make html
```

## Custom Admonitions

This template includes several custom admonitions that are accounted for in the CSS. 

Each lesson should start with an overview having the following format (the script should take care of this)

`````
````{admonition} Overview
:class: overview

Questions:

- Question 1
- Question 2

Objectives:

- Objective 1
- Objective 2

````

`````

Each lesson should end with key points having the following format:

``````
```{admonition} Key Points
:class: key

- Key Point 1
- Key Point 2

```
``````

Exercises have the following format:

```````

## Exercise Name - so it will show up in navigation

``````{admonition} Exercise
:class: exercise

Exercise prompt here

`````{admonition} Solution

Solution here. If you have code, you should use the tab-set-code directive, 
explained below.

`````
``````
```````

All code should be in `tab-set-code` directive:

``````

````{tab-set-code}

```{code-block} LANGUAGE_NAME
code here
```
````

``````

The script should take care of most of these. However, when indicating a file should be edited, I am using the file name instead of the language name. I wrote a patch for Sphinx highlighting where a file extension can be used to determine the language. 

## Table of Contents
You will want to group the lessons into themes for the top menu bar. 
This is different than the other lessons. 
I am using `00-section-name.rst` files. Those files also contain TOC to fill out the sections.

