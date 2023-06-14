<!--
title: Git and GitHub
description: Version control with Git and collaboration on GitHub
author: Ole Mussmann
version: 4.3.1
plugins: RevealMarkdown, RevealChalkboard, RevealHighlight, RevealMath.KaTeX, RevealMenu, RevealNotes, RevealSearch, RevealZoom
-->

<!-- .slide: data-state="blue_overlay yellow_flag yellow_strip purple_half_circle_bottom purple_blob right_e_top" data-background-video="./files/Mood video Homepage 2.mp4" data-background-video-loop data-background-video-muted="true" -->

# Automated Version Control

What is version control and why should I use it?

Note:
- Git all set up?
- SSH working?
- Otherwise: breakout room

---

<!-- .slide: data-state="black_overlay logo yellow_flag" data-background="./files/book-wall-g2e1ec5a05_1920.jpg" -->
<img style="height: 35vh;" src="https://swcarpentry.github.io/git-novice/fig/phd101212s.png"/>

<span style="font-size: small;">“Piled Higher and Deeper” by Jorge Cham, http://www.phdcomics.com </span>

---

<!-- .slide: data-state="black_overlay logo yellow_flag" data-background="./files/book-wall-g2e1ec5a05_1920.jpg" -->
## Documents are...
<div class="fragment">
  a series of changes
  <img style="height: 30vh; margin: 0; padding: 0;" src="https://swcarpentry.github.io/git-novice/fig/play-changes.svg"/>
</div>

---

<!-- .slide: data-state="black_overlay logo yellow_flag" data-background="./files/book-wall-g2e1ec5a05_1920.jpg" -->
## Collaboration
<div style="float: left; width: 49%;">
  independent changes
  <img style="height: 350px;" src="./files/versions.svg"/>
</div>
<div class="fragment" style="float: right; width: 49%;">
  can be merged
  <img style="height: 350px;" src="./files/merge.svg"/>
</div>

---

<!-- .slide: data-state="black_overlay logo yellow_flag" data-background="./files/book-wall-g2e1ec5a05_1920.jpg" -->
## Version Control: Key Points

- Version control is track changes on steroids.
- Version control is like an unlimited **undo**.
- Version control also allows many people to work in parallel.

---

<!-- .slide: data-state="standard" data-background="./files/footprint-g55586a507_1920.jpg" -->
## The Holy Realms of Git

<img src="https://swcarpentry.github.io/git-novice/fig/git-staging-area.svg">

<ul>
  <li><b>workspace</b>&nbsp;&nbsp;📂</li>
  <ul>
    <li>Your filesystem</li>
  </ul>
  <li class="fragment"><b>index</b>&nbsp;&nbsp;🕒
    <ul>
      <li>Staging area</li>
      <li>Files wait patiently to be committed</li>
    </ul>
  </li>
  <li class="fragment"><b>local repository</b>&nbsp;&nbsp;🗂️
    <ul>
      <li>Contains branches, commits, history, etc.</li>
    </ul>
  </li>
<ul>

---

<!-- .slide: data-state="standard" data-background="./files/footprint-g55586a507_1920.jpg" -->
## Crowded Staging Area / Index

<img src="https://swcarpentry.github.io/git-novice/fig/git-committing.svg">

The Staging Area / Index can hold many files and folders.

---

<!-- .slide: data-state="standard" data-background="./files/footprint-g55586a507_1920.jpg" -->
## Quiz 1/2

<blockquote style="text-align: left;">
Which commit message should I choose?
<ol>
  <li>“Changes”</li>
  <li>“Added line ‘This project started as a joke’ to myfile.txt”</li>
  <li>“Discuss origin of the project”</li>
</ol>
</code></pre>
</blockquote>
<blockquote class="fragment" style="text-align: right;">
Make it short, descriptive, and imperative <span style="font-style: normal;">🐺</span>
</blockquote>
<blockquote class="fragment" style="text-align: right;">
So yeah, the last one is good! <span style="font-style: normal;">🐺</span>
</blockquote>

---

<!-- .slide: data-state="standard" data-background="./files/footprint-g55586a507_1920.jpg" -->
## Quiz 2/2

<blockquote style="text-align: left;">
Which command saves <b>myfile.txt</b> to my Git repo?<br>
<ol>
  <li>
    <pre style="width: 100%; font-style: normal;" data-id="code-animation"><code data-trim class="bash">
    $ git commit -m "my recent changes"
    </code></pre>
  </li>
  <li>
    <pre style="width: 100%; font-style: normal;" data-id="code-animation"><code data-trim class="bash">
    $ git init myfile.txt
    $ git commit -m "my recent changes"
    </code></pre>
  </li>
  <li>
    <pre style="width: 100%; font-style: normal;" data-id="code-animation"><code data-trim class="bash">
    $ git add myfile.txt
    $ git commit -m "my recent changes"
    </code></pre>
  </li>
  <li>
    <pre style="width: 100%; font-style: normal;" data-id="code-animation"><code data-trim class="bash">
    $ git commit -m myfile.txt "my recent changes"
    </code></pre>
  </li>
</ol>
</code></pre>
</blockquote>
<blockquote class="fragment" style="text-align: right;">
3. adds your file to the index, and then commits it. That's the one.
<span style="font-style: normal;">🐺</span>
</blockquote>


---

<!-- .slide: data-state="standard" data-background="./files/footprint-g55586a507_1920.jpg" -->
## Tracking Changes: Key Points

- Files can be stored in
  - **working directory**: the files you can see
  - **staging area / index**: files about to be committed
  - **local repository**: the permanent record
- **git status**&nbsp; shows the status of a repository
- **git add**&nbsp; puts files in the staging area
- **git commit**&nbsp; saves the staged content as a new commit in the local repository
- Write short, descriptive, and imperative commit messages
