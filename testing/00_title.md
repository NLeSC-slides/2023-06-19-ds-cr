<!--
title: Testing
description: Getting more professional
author: Ole Mussmann
version: 4.3.1
plugins: RevealMarkdown, RevealChalkboard, RevealHighlight, RevealMath.KaTeX, RevealMenu, RevealNotes, RevealSearch, RevealZoom
-->

<!-- .slide: data-state="blue_overlay yellow_flag yellow_strip purple_half_circle_bottom purple_blob right_e_top" data-background-video="./files/606762245.mp4" data-background-video-loop data-background-video-muted="true" -->
<!-- https://pixabay.com/videos/engine-motor-mechanic-technology-5497/ -->

# Testing

---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png" -->

## Why Test?

<ul>
  <li>Preserve functionality
  <ul>
    <li>Detect new errors early</li>
    <li>Facilitate reproducibility for research software</li>
  </ul></li>
  <li class="fragment">Help users
  <ul>
    <li>Verify correct installation</li>
    <li>Improve correctness for research output</li>
  </ul></li>
  <li class="fragment">Enable developers
  <ul>
    <li>Make refactoring easier</li>
    <li>Simplify external contributions</li>
  </ul></li>
</ul>

<h3 style="margin-top: 1em;" class="fragment">🧮 Manage Complexity 🧩</h3>

---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png" -->

## Test Types

<ul>
  <li>Unit test
  <ul class="fragment fade-up" data-fragment-index="1">
    <li>Smallest possible unit</li>
    <li>No dependency on outside code...</li>
    <li>(... replace them with mocks, stubs, etc.)</li>
  </ul></li>
</ul>
<ul class="fragment fade-up" data-fragment-index="2">
  <li>Integration test
  <ul class="fragment fade-up" data-fragment-index="3">
    <li>Test unit interaction</li>
    <li>Can be on small scales, or system wide</li>
  </ul></li>
</ul>

<div class="fragment fade-up" data-fragment-index="4" style='position:relative; padding: 0 0 calc(55.00% + 44px) 0; margin: -9em auto 0 auto;'><iframe src='https://gfycat.com/ifr/BriefUniformHornet' frameborder='0' scrolling='no' width='100%' height='100%' style='position:absolute;top:0;left:0;' allowfullscreen></iframe></div><p style="font-size: large; margin: 0; padding: 0;"> <a href="https://gfycat.com/briefuniformhornet">via Gfycat</a></p>

---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png" -->


## How much testing is enough?

Test metrics:

- lines of code : lines of tests (target: 1:3)
- test coverage [example](https://sonarcloud.io/component_measures?id=eWaterCycle_ewatercycle&metric=coverage&view=treemap&selected=eWaterCycle_ewatercycle%3Aewatercycle)


---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png" -->

# PyTest

- recommended python testing framework
- [docs.pytest.org](https://docs.pytest.org/en/7.3.x/)

![](.files/pytest_logo.svg)

---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png" -->

## Write Code

<pre><code class="bash" style="overflow: hidden;" data-trim class="bash" data-line-numbers>
$ mkdir pytest-example
$ cd pytest-example
</code></pre>

<div class="fragment">
Creating a file <code>example.py</code> containing
<pre><code class="python" style="overflow: hidden;" data-trim class="bash" data-line-numbers>
def add(a, b):
    return a + b
&nbsp;
&nbsp;
def test_add():  # Special name!
    assert add(2, 3) == 5  # What's `assert`? 🤔
    assert add('space', 'ship') == 'spaceship'
</code></pre>
</div>

<div class="fragment">
Chat with the python shell about <code>assert</code> ...
</div>
<div class="fragment">
<pre><code class="python" style="overflow: hidden;" data-trim class="bash" data-line-numbers>
>>> assert 1==1  # passes
>>> assert 1==2  # throws error
Traceback (most recent call last):
  File "&lt;stdin&gt;", line 1, in &lt;module&gt;
AssertionError
</code></pre>

</div>

---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png" -->

## Test!

<pre><code style="overflow: hidden;" data-trim class="bash" data-line-numbers="1|1-9">
$ pytest example.py
======================== test session starts ========================
platform linux -- Python 3.6.9, pytest-7.0.1, pluggy-1.0.0
rootdir: /home/ole/Desktop/pytest-texample
collected 1 item

example.py .                                                  [100%]

========================= 1 passed in 0.00s =========================
</code></pre>

---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png" -->

## Breaking Things

<pre><code class="python" style="overflow: hidden;" data-trim class="bash" data-line-numbers>
def add(a, b):
    return a - b  # Uh oh, mistake! 😱


def test_add():
    assert add(2, 3) == 5
    assert add('space', 'ship') == 'spaceship'
</code></pre>

---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png" -->

## Testing Again

<pre><code style="overflow: hidden;" data-trim class="bash" data-line-numbers="1|2-8|9-17|18-20">
$ pytest example.py
======================== test session starts =========================
platform linux -- Python 3.6.9, pytest-7.0.1, pluggy-1.0.0
rootdir: /home/ole/Desktop/pytest-texample
collected 1 item

example.py F                                                   [100%]

============================== FAILURES ==============================
______________________________ test_add ______________________________

    def test_add():
>       assert add(2, 3) == 5
E       assert -1 == 5
E        +  where -1 = add(2, 3)

example.py:6: AssertionError
====================== short test summary info =======================
FAILED example.py::test_add - assert -1 == 5
========================= 1 failed in 0.05s ==========================
</code></pre>

<ul>
  <li class="fragment">🚀❓<span class="fragment">Functions fail on first error</span></li>
  <li class="fragment">But all test functions are executed</li>
</ul>

---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png" -->

## Take-away

- pytest collects and runs all test functions starting with <code>test_</code>
- The tests pass when they do not throw (assertion) errors

<pre style="width: max-content;"><code style="overflow: hidden;" class="python" data-trim class="bash" data-line-numbers>
def steal_sheep():
    ...
def paint_cows():
    ...

# optionally in another file:

def test_steal_sheep():
    ...
def test_paint_cows():
    ...
</code></pre>


---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png" -->

# Recap: pure functions

<div style="width: 59%; float: left;">
<ul style="margin-top: 1ex;">
  <li>Are deterministic</li>
  <li>Have a return value</li>
  <li>Have no side effects<sup>[1]</sup></li>
  <li>Have referential transparency<sup>[2]</sup></li>
<ul>
</div>

<div style="width: 39%; float: right;">
<pre class="fragment" style="width: max-content;" data-id="code-animation"><code class="python" style="overflow: hidden; padding-left: 1em; padding-right: 1em;" data-trim data-noescape class="bash" data-line-numbers="1-2|1-6|4-8">
def last(my_array):
    return my_array[-1]
&nbsp;
def add(a, b):
    return a + b
&nbsp;
print(add(1, 2))
print(3)
</code></pre>
</div>

<h4 class="fragment" style="width: 100%; float: left; margin-top: 1em;">Pure functions are easy to understand and test!</h4>

<footer>
[1] Side effects: interactions of a function with its surroundings
<br>
[2] Replacing a function call with the return of that function should not change anything
</footer>

---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png" -->

## Impure Functions

<div style="width: 46%; float: left;">
intuitive...
<pre style="width: max-content;" data-id="code-animation"><code class="python" style="overflow: hidden;" data-trim data-noescape class="bash" data-line-numbers="1-4|7-8|11-12">
my_list = []
&nbsp;
def append_to_my_list(item):
    my_list.append(item)
&nbsp;
&nbsp;
def read_data(file_name):
    return pd.read_csv(file_name)
&nbsp;
&nbsp;
def get_random_number(number):
    return random.random()
&nbsp;
</code></pre>
</div>

<div class="fragment" style="width: 53%; float: right;">
... and not so intuitive
<pre style="width: max-content;" data-id="code-animation"><code class="python" style="overflow: hidden;" data-trim data-noescape class="bash" data-line-numbers="1-2|5-9|5-13">
def hello(name):
    print("Hello", name)
&nbsp;
&nbsp;
nums = [1, 2]
&nbsp;
def append(a_list, item):
    a_list += [item]
    return a_list
&nbsp;
print(nums)            # [1, 2]
print(append(nums, 3)) # [1, 2, 3]
print(nums)            # [1, 2, 3] 😬</span>
</code></pre>
</div>

<ul class="fragment">
  <li>Side effects are sometimes necessary</li>
  <li>Some side effects are hard to spot</li>
</ul>


---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png" -->

## Take-away

- Use pure functions when possible 👌
- Testing does not have to be hard 👏
  - You test anyways, but then throw the test away 🧐
- You don't have to strive for 💯% test coverage
- Aim for a balance between unit- and integration tests ⚖️
- Testing removes the dread of refactoring 🔁
- Your future you will thank you 🙏

---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png" -->

## Test-Driven Development: FizzBuzz Function

<div class="r-stack">
  <img src="./files/fizz_buzz_1.svg">
  <img class="fragment" data-fragment-index="1" src="./files/fizz_buzz_2.svg">
  <img class="fragment" data-fragment-index="2" src="./files/fizz_buzz_3.svg">
  <img class="fragment" data-fragment-index="3" src="./files/fizz_buzz_4.svg">
  <img class="fragment" data-fragment-index="4" src="./files/fizz_buzz_5.svg">
  <img class="fragment" data-fragment-index="5" src="./files/fizz_buzz_6.svg">
</div>

<ul>
  <li>fizz_buzz() takes an integer argument and returns it, BUT</li>
  <ul>
    <li class="fragment" data-fragment-index="1">fails on zero or negative numbers</li>
    <li class="fragment" data-fragment-index="2">instead returns "Fizz" on multiples of 3</li>
    <li class="fragment" data-fragment-index="3">instead returns "Buzz" on multiples of 5</li>
    <li class="fragment" data-fragment-index="5">instead returns "FizzBuzz" on multiples of 3 and 5</li>
  </ul>
</ul>

---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png" -->

## FizzBuzz Function

<ul>
  <li>fizz_buzz() takes an integer argument and returns it, BUT</li>
  <ul>
    <li>fails on zero or negative numbers</li>
    <li>instead returns "Fizz" on multiples of 3</li>
    <li>instead returns "Buzz" on multiples of 5</li>
    <li>instead returns "FizzBuzz" on multiples of 3 and 5</li>
  </ul>
  <li class="fragment">Create an empty function fizz_buzz()</li>
  <li class="fragment">Write the tests</li>
  <li class="fragment">Paste your tests in the collab document, and discuss</li>
  <li class="fragment">Now write a function code to make your tests pass</li>
</ul>

---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png" -->

## Take-away

- What did you think of this style of development?
- Was it easier or harder than just writing code?
- Would your code look different without the tests? <!-- .element class="fragment" -->
- For what kind of projects would it be useful? <!-- .element class="fragment" -->

<div class="fragment" style="width: 20vw; margin: 1em auto;">Test-Driven Development (TDD) is an optional tool in your toolbox 🛠️</div>
