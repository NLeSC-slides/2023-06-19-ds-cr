<!--
title: Code Modularization
description: Code Modularization
author: Barbara Vreede, Ole Mussmann
version: 4.3.1
plugins: RevealMarkdown, RevealHighlight, RevealMath.KaTeX, RevealMenu, RevealNotes, RevealSearch, RevealZoom
-->

<!-- .slide: data-state="blue_overlay yellow_flag yellow_strip purple_half_circle_bottom purple_blob right_e_top" data-background-video="./files/Mood video Homepage 2.mp4" data-background-video-loop data-background-video-muted="true" -->

# Developing Modular Code

[Barbara Vreede](mailto:b.vreede@esciencecenter.nl) |  [Ole Mussmann](mailto:o.mussmann@esciencecenter.nl)

===

<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->

## What is modularity?

- Software is 'built up' from smaller elements
<!-- .element: class="fragment" data-fragment-index="3" -->
- Elements are self-contained and independent
<!-- .element: class="fragment" data-fragment-index="4" -->
- Each element handles a specific (set of) task(s)
<!-- .element: class="fragment" data-fragment-index="5" -->


**Simple components** build **complex behavior**.
<!-- .element: class="fragment" data-fragment-index="6" -->

---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png" -->

## Modular code

<img width="900" alt="think in building blocks" src="https://user-images.githubusercontent.com/5747405/207459058-59c88b4c-1401-428f-b28a-0ac3e72bd964.png">

---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png" -->

## What are these blocks/elements?

- functions
- functions
- classes
- modules
- libraries/packages
- programs


===

<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->

## Why write modular code?

- Maintenance
<!-- .element: class="fragment" data-fragment-index="2" -->
- Reusability
<!-- .element: class="fragment" data-fragment-index="3" -->
- Robustness
<!-- .element: class="fragment" data-fragment-index="4" -->
- Scalability
<!-- .element: class="fragment" data-fragment-index="5" -->
- Innovation
<!-- .element: class="fragment" data-fragment-index="6" -->
- Flexibility
<!-- .element: class="fragment" data-fragment-index="7" -->
- ...
<!-- .element: class="fragment" data-fragment-index="8" -->


Note:
- Maintenance
  - Modular code is easier to read, understand, and therefore to maintain.
  - An independent module can be debugged, changed, or optimized, without it being necessary to understanding the rest of the codebase.
- Reusability
  - An independent module can live outside the context it was written for.
  - It can be reused by another project, and serve a purpose in a different environment.
- Robustness
  - Modules are prime targets for tests.
  - A well defined module is easier to test, and therefore easier to debug or keep bug-free.
- Scalability
  - Modular code keeps the complexity of a project low by design.
  - This makes it easier to scale up without creating huge issues.
- Innovation
  - Modules increase the capabilities and power of a project, without increasing the complexity on a maintenance level.
  - Rearranging old modules can lead to powerful new applications.
- Flexibility
  - With code existing of independent modules, with low or absent interdependency, the codebase becomes flexible and amenable to change.
  - Modifications can be made in a targeted way, without unexpected (disastrous) consequences.


---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->

<img width="800" alt="development speed" src="./files/development-speed.svg">

===

<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->

## A good module...

- has a clear interface

---


<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->

<img height="500" alt="Modules with bad interaction" src="./files/modules-bad-connection.png">
<!-- .element: class="fragment" data-fragment-index="2" -->
<img width="100" src="./files/whitebg.png">

<img height="500" alt="Modules with clear connecting interfaces" src="./files/modules-good-connection.png">
<!-- .element: class="fragment" data-fragment-index="3" -->

---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->

## A good module...

- has a clear interface
- performs limited and clearly defined tasks
- has a good name
<!-- .element: class="fragment" data-fragment-index="2" -->
- is readable
<!-- .element: class="fragment" data-fragment-index="3" -->

---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->

## Readability =/= shorter code

Shorter:
```python=
indexATG = [n for n,i in enumerate(myList) if i == 'ATG']
indexAAG = [n for n,i in enumerate(myList) if i == 'AAG']
```

More modular:
```python=
def getIndex(inputList,z):
    zIndex = [n for n,i in enumerate(li) if i == z]
    return zIndex

indexATG = getIndex(myList,'ATG')
indexAAG = getIndex(myList,'AAG')
```

---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->

## A good module...

- has a clear interface
- performs limited and clearly defined tasks
- has a good name
- is readable
- is pure/does not have a 'state'

---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->

## A pure function

has no side-effects:

```python=
def fahrenheit_to_celsius(temp_f):
    temp_c = (temp_f - 32.0) * (5.0/9.0)
    return temp_c

>>> temp_c = fahrenheit_to_celsius(temp_f=77.0)
>>> print(temp_c)
25.0
```

---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->

## A stateful function

changes their environment:

```python=
f_to_c_offset = 32.0
f_to_c_factor = 0.555555555
temp_c = 0.0

def fahrenheit_to_celsius(temp_f):
    global temp_c
    temp_c = (temp_f - f_to_c_offset) * f_to_c_factor

>>> print(temp_c)
0.0
>>> fahrenheit_to_celsius(temp_f=77.0)
>>> print(temp_c)
25.0
```

===


<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->


===



<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->


## How do we make code more modular?

- Identify areas for improvement


---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->

## Identify processes and functions

- Readability: a "code smell"
- Nestedness


---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->

### Create modules
Create functions, classes, or even full packages for processes and functions identified in step 1. Move existing code into this structure.

---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->

### Refactor
Refactor the code in each module to make it as self-contained as possible. For example, remove dependencies on external code or data where possible.
Clearly define the task that a module should do, and edit away any other functionality.

---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->

### Test
Test each module individually to ensure no errors or bugs are creeping in.
Use tests also to again look critically at the function that should be performed by a module.

===

<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->

## Do One Thing (and do it well)
- One _function_ for one purpose
- One _class_ for one purpose
- One _package_ for one purpose

===

<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->

## Don't Repeat Yourself

- Write routines (i.e. code that gets reused) into functions
- Identify potential functions by _action_: functions perform tasks (e.g. sorting, plotting, saving a file, transform data...)


---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->

## Functions are...
- Functions are smaller code units reponsible of one task.
- Functions are meant to be reused
- Functions accept arguments (though they may also be empty!)
- Functions generate output

---


---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->


## When to make functions?

Always.

---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->

## When to make more functions?
- if you have too many levels of indentation
- if a function gets too long
- if a function does more than one thing
- if you find it hard to name a function

---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->



---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->

## Pure functions are easier to

- Test
- Understand
- Reuse
- Parallelize
- Simplify
- Optimize
- Compose

---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->

## Divide and conquer

- Split the code up
- Construct your program from parts:
  - functions
  - modules
  - packages (Python) or libraries (C or or C++ or Fortran)

---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->

## Keep it simple

- Avoid using complex data structures or algorithms
- Instead, try to use simple, built-in data types and functions whenever possible.
- Use clear and consistent indentation and naming conventions
- Use descriptive and meaningful names for your variables, functions, and other code elements.
- Avoid using global variables whenever possible
- Instead, use local variables and functions to isolate and manage your data.
- Avoid using complex or nested control flow statements
- Instead, try to break your code down into smaller, simpler pieces that can be handled separately.


