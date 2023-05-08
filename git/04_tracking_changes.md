<!-- .slide: id="tracking_changes" data-state="standard" data-background="./files/footprint-g55586a507_1920.jpg" -->
<!-- Image by <a href="https://pixabay.com/users/tbit-715211/?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=946189">Thomas Breher</a> from <a href="https://pixabay.com//?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=946189">Pixabay</a> -->
# Tracking Changes

- How do I record changes in Git?
- How do I check the status of my version control repository?
- How do I record notes about what changes I made and why?

---

<!-- .slide: data-state="standard" data-background="./files/footprint-g55586a507_1920.jpg" -->
## The Holy Realms of Git

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
## Create Files 🧛

<pre data-id="code-animation"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers="1-5|7-8|10-11|13-24">
$ cd ~/Desktop/planets  
$ code mars.txt  # use your favorite editor here
# type "Cold and dry, but everything is my favorite color"
# [CTRL]+S  save file
# [CTRL]+Q  exit editor

$ ls             # list directory
mars.txt

$ cat mars.txt   # cat: print file content
Cold and dry, but everything is my favorite color

$ git status
On branch main

No commits yet

Untracked files:
   (use "git add &lt;file&gt;..." to include in what will be committed)

	mars.txt

nothing added to commit but untracked files present
(use "git add" to track)
</code></pre>

---

<!-- .slide: data-state="standard" data-background="./files/footprint-g55586a507_1920.jpg" -->
## Add to Index 🧛

<pre data-id="code-animation"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers="1-2|3-11">
$ git add mars.txt  # add file to INDEX

$ git status
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached &lt;file&gt;..." to unstage)

	new file:   mars.txt
</code></pre>

---

<!-- .slide: data-state="standard" data-background="./files/footprint-g55586a507_1920.jpg" -->
## Commit to Local Repository 🧛

<pre data-id="code-animation"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers="1-6|8-10|12-17">
# -m  include a commit message,
# if omitted an editor will open for you to enter one
$ git commit -m "Start notes on Mars as a base"
[main (root-commit) f22b25e] Start notes on Mars as a base
 1 file changed, 1 insertion(+)
 create mode 100644 mars.txt

$ git status
On branch main
nothing to commit, working directory clean

$ git log
commit f22b25e3233b4645dabd0d81e651fe074bd8e73b
Author: Vlad Dracula &lt;vlad@tran.sylvan.ia&gt;
Date:   Thu Aug 22 09:51:46 2013 -0400

    Start notes on Mars as a base
</code></pre>

---

<!-- .slide: data-state="standard" data-background="./files/footprint-g55586a507_1920.jpg" -->
## We All Have Our Differences 🧛

<pre data-id="code-animation"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers="1-4|6-15|17-24|26-35|37-41">
$ code mars.txt  # Add a line
$ cat mars.txt
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman

$ git status
On branch main
Changes not staged for commit:
  (use "git add &lt;file&gt;..." to update what will be committed)
  (use "git checkout -- &lt;file&gt;..." to discard changes
   in working directory)

	modified:   mars.txt

no changes added to commit (use "git add" and/or "git commit -a")

$ git diff
diff --git a/mars.txt b/mars.txt  # output similar to `diff`
index df0654a..315bf3a 100644     # diff between which versions?
--- a/mars.txt                    # version a of 'mars.txt'
+++ b/mars.txt                    # version b of 'mars.txt'
@@ -1 +1,2 @@                     # ±&lt;start line&gt;, &lt;number of lines&gt;
 Cold and dry, but everything is my favorite color  # file context
+The two moons may be a problem for Wolfman         # +add -subtract

$ git commit -m "Add concerns about effects of Mars’ moons on Wolfman"
On branch main
Changes not staged for commit:
  (use "git add &lt;file&gt;..." to update what will be committed)
  (use "git checkout -- &lt;file&gt;..." to discard changes
   in working directory)

	modified:   mars.txt

no changes added to commit (use "git add" and/or "git commit -a")

$ git add mars.txt
$ git commit -m "Add concerns about effects of Mars’ moons on Wolfman"
[main 34961b1] Add concerns about effects of Mars’ moons on Wolfman
 1 file changed, 1 insertion(+)
</code></pre>

---

<!-- .slide: data-state="standard" data-background="./files/footprint-g55586a507_1920.jpg" -->
## Recap: Git Realms

<img src="https://swcarpentry.github.io/git-novice/fig/git-staging-area.svg">

- **workspace**
  - your filesystem
- **staging area / index**
  - one or more files, waiting to be committed
- **local repository**
  - writing history

---

<!-- .slide: data-state="standard" data-background="./files/footprint-g55586a507_1920.jpg" -->
## Getting the Hang of It 🧛

<pre style="height: 457px;" data-id="code-animation"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers="1-5|7-15|17-19|21-29|31-36|38-40|42-59">
$ code mars.txt  # Add another line
$ cat mars.txt
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity

$ git diff
diff --git a/mars.txt b/mars.txt
index 315bf3a..b36abfd 100644
--- a/mars.txt
+++ b/mars.txt
@@ -1,2 +1,3 @@
 Cold and dry, but everything is my favorite color
 The two moons may be a problem for Wolfman
+But the Mummy will appreciate the lack of humidity

$ git add mars.txt
$ git diff
# *crickets* 🦗🦗

$ git diff --staged
diff --git a/mars.txt b/mars.txt
index 315bf3a..b36abfd 100644
--- a/mars.txt
+++ b/mars.txt
@@ -1,2 +1,3 @@
 Cold and dry, but everything is my favorite color
 The two moons may be a problem for Wolfman
+But the Mummy will appreciate the lack of humidity

$ git commit  # omit "-m message" and see what happens
# type: Discuss appreciation about Mars’ climate for Mummy
# also write a message for future you
# save and exit the editor
[main 005937f] Discuss appreciation about Mars’ climate for Mummy
 1 file changed, 1 insertion(+)

$ git status
On branch main
nothing to commit, working directory clean

$ git log
commit 005937fbe2a98fb83f0ade869025dc2636b4dad5 (HEAD -&gt; main)
Author: Vlad Dracula &lt;vlad@tran.sylvan.ia&gt;
Date:   Thu Aug 22 10:14:07 2013 -0400

    Discuss appreciation about Mars’ climate for Mummy

commit 34961b159c27df3b475cfe4415d94a6d1fcd064d
Author: Vlad Dracula &lt;vlad@tran.sylvan.ia&gt;
Date:   Thu Aug 22 10:07:21 2013 -0400

    Add concerns about effects of Mars’ moons on Wolfman

commit f22b25e3233b4645dabd0d81e651fe074bd8e73b
Author: Vlad Dracula &lt;vlad@tran.sylvan.ia&gt;
Date:   Thu Aug 22 09:51:46 2013 -0400

    Start notes on Mars as a base
</code></pre>

---

<!-- .slide: data-state="standard" data-background="./files/footprint-g55586a507_1920.jpg" -->

## Tips: Pager

<pre data-id="code-animation"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers>
$ git log
commit 005937fbe2a98fb83f0ade869025dc2636b4dad5 (HEAD -&gt; main)
Author: Vlad Dracula &lt;vlad@tran.sylvan.ia&gt;
Date:   Thu Aug 22 10:14:07 2013 -0400

    Discuss appreciation about Mars’ climate for Mummy

commit 34961b159c27df3b475cfe4415d94a6d1fcd064d
Author: Vlad Dracula &lt;vlad@tran.sylvan.ia&gt;
:  # When the screen can't fit the whole log, the output is _paged_
</code></pre>



<pre data-id="code-animation"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers>
# Navigate the content with:
Q             # exit pager
SPACEBAR      # next page
↑↓            # up or down
/word[ENTER]  # search for word
N             # find the next match
</code></pre>

---

<!-- .slide: data-state="standard" data-background="./files/footprint-g55586a507_1920.jpg" -->
## Tips: Word-Based Diffing

<pre style="width: max-content;" data-id="code-animation"><code style="overflow: hidden;" data-trim class="bash">
&nbsp;$ git diff --color-words&nbsp;
</code></pre>

---

<!-- .slide: data-state="standard" data-background="./files/footprint-g55586a507_1920.jpg" -->

## Tips: Formatting Logs

<pre data-id="code-animation"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers="1-6|8-12|14-18">
$ git log -1
commit 005937fbe2a98fb83f0ade869025dc2636b4dad5 (HEAD -&gt; main)
Author: Vlad Dracula &lt;vlad@tran.sylvan.ia&gt;
Date:   Thu Aug 22 10:14:07 2013 -0400

   Discuss concerns about Mars’ climate for Mummy

$ git log --oneline

005937f (HEAD -&gt; main) Discuss appreciation about Mars’ climate for Mummy
34961b1 Add concerns about effects of Mars’ moons on Wolfman
f22b25e Start notes on Mars as a base

$ git log --oneline --graph

* 005937f (HEAD -&gt; main) Discuss appreciation about Mars’ climate for Mummy
* 34961b1 Add concerns about effects of Mars’ moons on Wolfman
* f22b25e Start notes on Mars as a base
</code></pre>

---

<!-- .slide: data-state="standard" data-background="./files/footprint-g55586a507_1920.jpg" -->

## Directories 🧛

<pre style="height: 330px;" data-id="code-animation"><code style="height: 330px; overflow: hidden;" data-trim class="bash" data-line-numbers="1-11|13-21|23-31">
$ mkdir spaceships
$ git status
On branch main
nothing to commit, working tree clean
# ?

$ git add spaceships
$ git status
On branch main
nothing to commit, working tree clean
# ??

# touch  create an empty file
$ touch spaceships/apollo-11 spaceships/sputnik-1
$ git status
On branch main
Untracked files:
  (use "git add &lt;file&gt;..." to include in what will be committed)
	spaceships/

nothing added to commit but untracked files present (use "git add" to track)

$ git add spaceships
$ git status
On branch main
Changes to be committed:
  (use "git restore --staged &lt;file&gt;..." to unstage)
	new file:   spaceships/apollo-11
	new file:   spaceships/sputnik-1

$ git commit -m "Add some initial thoughts on spaceships"
</code></pre>

<blockquote class="fragment" data-fragment-index="1" style="text-align: left;">
<span style="font-style: normal;">🧛</span> WTF?
</blockquote>
<blockquote class="fragment" data-fragment-index="2" style="text-align: right;">
Git does not track empty directories <span style="font-style: normal;">🐺</span>
</blockquote>

<footer>
use an empty hidden file if you want to commit an "empty" folder
</footer>

---

<!-- .slide: data-state="standard" data-background="./files/footprint-g55586a507_1920.jpg" -->
## Crowded Staging Area / Index

<img src="https://swcarpentry.github.io/git-novice/fig/git-committing.svg">

The Staging Area / Index can hold many files and folders.

---

<!-- .slide: data-state="standard" data-background="./files/footprint-g55586a507_1920.jpg" -->
## Quiz 1/2

<blockquote style="text-align: left;">
<span style="font-style: normal;">🧛</span> Which commit message should I choose?
<ol>
  <li>“Changes”</li>
  <li>“Added line ‘But the Mummy will appreciate the lack of humidity’ to mars.txt”</li>
  <li>“Discuss effects of Mars’ climate on the Mummy”</li>
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
<span style="font-style: normal;">🧛</span> Which command saves <b>myfile.txt</b> to my Git repo?<br>
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
## Exercise 1/2

<ol style="font-size: x-large;">
  <li>Edit <b>mars.txt</b> noting your decision to consider Venus as a base</li>
  <li>Create a file <b>venus.txt</b> with your thoughts about Venus as a base for you and your friends</li>
  <li>Add changes from both files to the staging area, and commit those changes</li>
</ol>

<pre class="fragment" style="width: 100%; font-style: normal;" data-id="code-animation"><code data-trim class="bash" data-line-numbers="1-4|6-9|11-15|17-22">
$ code mars.txt
$ cat mars.txt

Maybe I should start with a base on Venus.

$ code venus.txt
$ cat venus.txt

Venus is a nice planet and I definitely should consider it as a base.

$ git add mars.txt venus.txt

# Or with multiple commands:
# git add mars.txt
# git add venus.txt

$ git commit -m "Write plans to start a base on Venus"

[main cc127c2]
 Write plans to start a base on Venus
 2 files changed, 2 insertions(+)
 create mode 100644 venus.txt
</code></pre>

---

<!-- .slide: data-state="standard" data-background="./files/footprint-g55586a507_1920.jpg" -->
## Exercise 2/2

<ol style="font-size: x-large;">
  <li>Create a new Git repository on your computer in a directory called <b>bio</b>.</li>
  <li>Write a three-line biography for yourself in a file called <b>me.txt</b>, commit your changes</li>
  <li>Modify one line, add a fourth line</li>
  <li>Display the differences between its updated state and its original state</li>
</ol>

<pre class="fragment" style="width: 100%; font-style: normal;" data-id="code-animation"><code data-trim class="bash" data-line-numbers="1-4|6|8-12|14-22|24-34">
$ cd ..  # if needed

$ mkdir bio
$ cd bio

$ git init

$ code me.txt
$ cat me.txt
In the beginning there was light.
Then I closed my eyes for a brief second.
And now I’m in my forties...

$ git add me.txt
$ git commit -m "Add biography file" 

$ code me.txt
$ cat me.txt
In the beginning there was light.
Then I lived a wonderful life.
And now I’m in my forties...
Teaching Git! :D

$ git diff me.txt
diff --git a/me.txt b/me.txt
index 4660238..d9450bd 100644
--- a/me.txt
+++ b/me.txt
@@ -1,3 +1,4 @@
 In the beginning there was light.
-Then I closed my eyes for a brief second.
+Then I lived a wonderful life.
 And now I’m in my forties...
+Teaching Git! :D
</code></pre>

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
