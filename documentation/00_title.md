<!--
title: Documentation
description: Day 3 Code Refinery TUSAIL
author: Luisa Orozco
version: 4.3.1
plugins: RevealMarkdown, RevealChalkboard, RevealHighlight, RevealMath.KaTeX, RevealMenu, RevealNotes, RevealSearch, RevealZoom
-->

<!-- .slide: data-state="blue_overlay yellow_flag yellow_strip purple_half_circle_bottom purple_blob right_e_top" data-background-video="./files/Mood video Homepage 2.mp4" data-background-video-loop data-background-video-muted="true" -->

# Documentation

[Luisa Orozco](mailto:l.orozco@esciencecenter.nl)

===

<!-- .slide: data-state="standard" -->

# 05. Code Documentation

<img style="height: 350px;" src="./files/paint.png"/>

---

<!-- .slide: data-state="standard" -->

<img style="height: 350px;" src="./files/development_speed_vs_time.png"/>

---

<!-- .slide: data-state="standard" -->

## Code documentation lesson

+ Why would you document software?
+ What makes good documentation?
+ How do I write good in-code documentation?
+ How do I write good README files?
+ Demo creating documentation with Sphinx and deploying to Github pages.
+ **Independent of programming languages**

===

<!-- .slide: data-state="standard" -->

## Episode 1: Motivation and wishlist

+ Why documenting code?
+ What is our wishlist on a suitably good documentation?
+ Is project documentation important? Why? Take a few moments to think about it.

---

<!-- .slide: data-state="standard" -->

## Exercise 1: Think of good and bad examples

Write down your thoughts in the collaborative documents.
Respond with emojis 👍 🙀 to your colleagues' answers.

+ Think of projects of which you like the documentation. What do you like about them?
+ Think of projects for which you don't like the documentation. What don't you like about them? Are you missing anything?

> NB: You can choose a mature library with lots of users for this exercise, but try to also think of less mature projects you had to collaborate on, or papers you had to reproduce.

---

<!-- .slide: data-state="standard" -->

## What did we learn?

+ It is important to document code.
+ Depending on the purpose and state of the project documentation needs to meet different criteria. 
+ For most scientific projects, in-code documentation and a well thought out README file is enough.
+ Documentation should be tracked with corresponding code.

===

<!-- .slide: data-state="standard" -->

## Episode 2: in-code documentation

+ What can I do to make my code more easily understandable?
+ What information should go into comments?
+ What information should go into docstrings?

---

<!-- .slide: data-state="standard" -->

## Exercise 2: Writing good comments

Let's take a look at two example comments (comments in python start with #):

**Comment A**

<pre data-id="code-animation"><code style="overflow: hidden;" data-trim class="python">
# Now we check if temperature is larger then -50:
if temperature > -50:
    print('do something')
</code></pre>

**Comment B**

<pre data-id="code-animation"><code style="overflow: hidden;" data-trim class="python">
# We regard temperatures below -50 degrees as measurement errors
if temperature > -50:
    print('do something')
</code></pre>

Which of these comments is best? Can you explain why?

---

<!-- .slide: data-state="standard" -->

Do not use comments for:

+ Keeping zombie 🧟 code
<pre data-id="code-animation"><code style="overflow: hidden;" data-trim class="python">
# Do not run this code!:
# if temperature > 0:
#     print('It is warm')
</code></pre>

---

<!-- .slide: data-state="standard" -->

Do not use comments for:

+ Replacing git
<pre data-id="code-animation"><code style="overflow: hidden;" data-trim class="python">
# removed on August 5
# if() ...
# Now it connects to the API with o-auth2, updated 05/05/2016
</code></pre>

---

<!-- .slide: data-state="standard" -->

_Let's write some docstrings in python_

>Code along

---

<!-- .slide: data-state="standard" -->

## Exercise 3: Adding in-code documentation

Add this code to your project and update this code snippet so it is well-documented:

<pre data-id="code-animation"><code style="overflow: hidden;" data-trim class="python">
import pandas as pd

def x(a, print_columns=False):
   b = pd.read_excel(a)
   column_headers = list(b.columns.values)
   if print_columns:
       print("\n".join(column_headers))
   return column_headers
</code></pre>

---

<!-- .slide: data-state="standard" -->

## Keypoints Episode 2

> Giving explicit, descriptive names to your code segments (functions, classes, variables) already provides very useful and important documentation. In practice you will find that for simple functions it is unnecessary to add a docstring when the function name and variable names already give enough information.

+ Comments should describe the why for your code not the what.
+ Writing docstrings is an easy way to write documentation while you type code.

===

<!-- .slide: data-state="standard" -->

## Episode 3: Writing a good README file

+ README file is first thing a user/collaborator sees
+ What should be included as a bare minimum in README files?

---

<!-- .slide: data-state="standard" -->

## Exercise 4: Write a README file

📝 Try to draft a brief README or review a README which you have written for one of your projects.

---

<!-- .slide: data-state="standard" -->

## What makes up a good README file?

+ A descriptive project title
+ Motivation (why the project exists) and basics
+ Installation / How to setup
+ Copy-pastable quick start code example
+ Usage reference (if not elsewhere)
+ Recommended citation if someone uses it
+ Other related tools ("see also")

---

<!-- .slide: data-state="standard" -->

## User experience

Think about the user (which can be a future you) of your project.

+ What does this user need to know to use or contribute to the project?
+ How do you make your project attractive to use or contribute to?

===

<!-- .slide: data-state="standard" -->

## Episode 4: Sphinx documentation

+ What if a README file is not enough?
+ How do I easily create user documentation?

---

<!-- .slide: data-state="standard" -->

## Tools

+ **Sphinx** (documentation generator) lets you create nicely-formatted HTML pages out of simple markdown files. It is programming language-independent.
+ **Github pages** (deploy your documentation) easily connects to your github repository and automatically deploys your Sphinx documentation for free!

_Let's create documentation four our projects with Sphinx_

>Code along

===

<!-- .slide: data-state="standard" -->

## Recap documentation

+ What questions do you still have?
+ Whether there are any incremental improvements that can benefit your projects?
+What is nice that we learnt but is overkill for your current work?

---

<!-- .slide: data-state="standard" -->

## Take-home message

+ It is important to document code.
+ Depending on the purpose and state of the project documentation needs to meet different criteria.
