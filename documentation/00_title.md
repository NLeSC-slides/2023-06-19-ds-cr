<!--
title: Documentation
description: Day 3 Code Refinery TUSAIL
author: Luisa Orozco
version: 4.3.1
plugins: RevealMarkdown, RevealChalkboard, RevealHighlight, RevealMath.KaTeX, RevealMenu, RevealNotes, RevealSearch, RevealZoom
-->

<!-- .slide: data-state="blue_overlay yellow_flag yellow_strip purple_half_circle_bottom purple_blob right_e_top" data-background-video="./files/Mood video Homepage 2.mp4" data-background-video-loop data-background-video-muted="true" -->

# Documentation

===

<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->

<img style="height: 350px;" src="./files/paint.png"/>

---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->

## Code documentation lesson

+ Why document software?
+ What makes good documentation:
  + In-code documentation
  + README files
+ API documentation with Sphinx
+ Deploying documentation to GitHub Pages

===

<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->

## Examples: good and bad documentation

+ Think of projects with good documentation. What do you like about them?
+ Think of projects with less good documentation. What don't you like about them? Are you missing anything?

<quotation>NB: You can choose a mature library with lots of users, but try to also think of less mature projects you had to collaborate on, or papers you had to reproduce.</quotation>

---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->

## What did we learn?

+ It is important to document code.
+ Documentation needs to meet different criteria, depending on the purpose and state of the project.
+ For example, a well thought out README file and useful in-code commenting may suffice on a research project.
+ Documentation should be tracked with corresponding code.

===

<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->

## In-code documentation

+ What can I do to make my code more easily understandable?
+ What information should go into comments?
+ What information should go into docstrings?

---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->

## Is commenting necessary for understandable code?

+ It can be...
+ ... but it should never replace readable code:

```python=
# convert from degrees celsius to fahrenheit
def convert(d):
    return d * 4 / 9 + 32
```
vs
```python=
def celsius_to_fahrenheit(degrees):
    return degrees * 4 / 9 + 32
```
---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->

## Commenting: why vs what

Let's take a look at two example comments:

**Comment A**

<pre data-id="code-animation"><code style="overflow: hidden;" data-trim class="python">
# Now we check if temperature is larger than -50:
if temperature > -50:
    print('do something')
</code></pre>

**Comment B**

<pre data-id="code-animation"><code style="overflow: hidden;" data-trim class="python">
# We regard temperatures below -50 degrees as measurement errors
if temperature > -50:
    print('do something')
</code></pre>

How are these different? Which one do you prefer?

---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->

Do not use comments for:

+ Keeping zombie 🧟 code
<pre data-id="code-animation"><code style="overflow: hidden;" data-trim class="python">
# Do not run this code!:
# if temperature > 0:
#     print('It is warm')
</code></pre>

<div class="fragment">
<ul>
  <li>Replacing git</li>
</ul>
<pre style="width: max-content;" data-id="code-animation"><code style="overflow: hidden;" data-trim class="python">
# removed on August 5
# if() ...
# Now it connects to the API with o-auth2, updated 05/05/2016
</code></pre>
</div>

---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->

## Docstrings: a special kind of comment

```python=
def celsius_to_fahrenheit(degrees):
  """Convert degrees Celsius to degrees Fahrenheit."""
  return degrees * 4 / 9 + 32
```

Why is this OK?

Note:
Docstrings can be used to generate user documentation.
They are accessible outside the code.
They follow a standardized syntax.

---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->

## In-code commenting: key points

+ Giving explicit, descriptive names to your code segments already provides important documentation.
+ Comments should describe the why for your code, not the what.
+ Writing docstrings is an easy way to write documentation while you code, as they are accessible outside the code itself.

===

<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->

## Writing a good README file

+ README file is first thing a user/collaborator sees
+ What should be included as a bare minimum in README files?

---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->

## What makes up a good README file?

+ A descriptive project title
+ Motivation (why the project exists) and basics
+ Installation / How to setup
+ Copy-pasteable quick start code example
+ Usage reference (if not elsewhere)
+ Recommended citation if someone uses it
+ Other related tools ("see also")

---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->

## User experience

Think about the user (which can be a future you) of your project.

+ What does this user need to know to use or contribute to the project?
+ How do you make your project attractive to use or contribute to?

===

<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->

## User/API documentation

+ What if a README file is not enough?
+ How do I easily create user documentation?

---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->

## Tools

+ **Sphinx** (documentation generator)
  - creates nicely-formatted HTML pages out of .md or .rst files
  - programming language independent
+ **Github pages** (deploy your documentation)
  - set up inside your GitHub repository
  - automatically deploys your Sphinx-generated documentation

===

<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->

## Take-home message

+ It is important to document code.
+ Documentation can take different shapes:
  + Readable code
  + In-code comments
  + Docstrings
  + README files
  + Tutorials/notebooks
+ Depending on the purpose and state of the project documentation needs to meet different criteria.
