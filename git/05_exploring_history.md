<!-- .slide: id="exploring_history" data-state="black_overlay logo yellow_flag" data-background="./files/lamp-g95a0e35a2_1920.jpg" -->
<!-- Image by <a href="https://pixabay.com/users/laura_o-25271417/?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=6997864">Laura Otýpková</a> from <a href="https://pixabay.com//?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=6997864">Pixabay</a> -->
# Exploring History

- How can I identify old versions of files?
- How do I review my changes?
- How can I recover old versions of files?

---

<!-- .slide: data-state="black_overlay logo yellow_flag" data-background="./files/lamp-g95a0e35a2_1920.jpg" -->
## Looking Back in Time 🧛

<pre data-id="code-animation"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers="1-6|8-18|20-30|32-42|44-58| 60-70|72-82">
$ code mars.txt  # Don't commit yet!
$ cat mars.txt
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity
An ill-considered change

# diff to the previous commit
$ git diff HEAD mars.txt
diff --git a/mars.txt b/mars.txt
index b36abfd..93a3e13 100644
--- a/mars.txt
+++ b/mars.txt
@@ -1,3 +1,4 @@
 Cold and dry, but everything is my favorite color
 The two moons may be a problem for Wolfman
 But the Mummy will appreciate the lack of humidity
+An ill-considered change

# diff to the commit _before that_
$ git diff HEAD~1 mars.txt
diff --git a/mars.txt b/mars.txt
index 315bf3a..93a3e13 100644
--- a/mars.txt
+++ b/mars.txt
@@ -1,2 +1,4 @@
 Cold and dry, but everything is my favorite color
 The two moons may be a problem for Wolfman
+But the Mummy will appreciate the lack of humidity
+An ill-considered change

# diff to _any_ previous commit
$ git diff HEAD~2 mars.txt
diff --git a/mars.txt b/mars.txt
index df0654a..93a3e13 100644
--- a/mars.txt
+++ b/mars.txt
@@ -1 +1,4 @@
 Cold and dry, but everything is my favorite color
+The two moons may be a problem for Wolfman
+But the Mummy will appreciate the lack of humidity
+An ill-considered change

# show _any_ previous commit
$ git show HEAD~2 mars.txt
commit 825524b73bd00643261494eab739a16af9af75cd
Author: Vlad Dracula &lt;vlad@tran.sylvan.ia&gt;
Date:   Thu Nov 24 10:02:46 2022 +0100

    Start notes on Mars as a base

diff --git a/mars.txt b/mars.txt
new file mode 100644
index 0000000..df0654a
--- /dev/null
+++ b/mars.txt
@@ -0,0 +1 @@
+Cold and dry, but everything is my favorite color

# diff to a specific commit hash
$ git diff 825524b73bd00643261494eab739a16af9af75cd mars.txt
diff --git a/mars.txt b/mars.txt
index df0654a..93a3e13 100644
--- a/mars.txt
+++ b/mars.txt
@@ -1 +1,4 @@
 Cold and dry, but everything is my favorite color
+The two moons may be a problem for Wolfman
+But the Mummy will appreciate the lack of humidity
+An ill-considered change

# diff to a specific commit hash, but lazy
$ git diff 825524b mars.txt
diff --git a/mars.txt b/mars.txt
index df0654a..93a3e13 100644
--- a/mars.txt
+++ b/mars.txt
@@ -1 +1,4 @@
 Cold and dry, but everything is my favorite color
+The two moons may be a problem for Wolfman
+But the Mummy will appreciate the lack of humidity
+An ill-considered change
</code></pre>

<ul class="fragment" data-fragment-index="1">
  <li><b>HEAD</b> identifies the most recent commit</li>
  <li><b>HEAD~1</b> identifies the commit before that</li>
  <li><b>HEAD~X</b> identifies the commit X steps back</li>
</ul>

---

<!-- .slide: data-state="black_overlay logo yellow_flag" data-background="./files/lamp-g95a0e35a2_1920.jpg" -->
## Time Travel 🧛

<pre data-id="code-animation"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers="1-11|13-17|19-21|23-28|30-31|33-36">
$ git status

On branch main
Changes not staged for commit:
  (use "git add &lt;file&gt;..." to update what will be committed)
  (use "git checkout -- &lt;file&gt;..." to discard changes
   in working directory)

    modified:   mars.txt

no changes added to commit (use "git add" and/or "git commit -a")

$ git checkout HEAD mars.txt
$ cat mars.txt
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity

$ git checkout 825524b mars.txt
$ cat mars.txt
Cold and dry, but everything is my favorite color

$ git status
On branch main
Changes to be committed:
  (use "git reset HEAD &lt;file&gt;..." to unstage)

    modified:   mars.txt

$ git checkout HEAD mars.txt
Updated 1 path from 6573bcb

$ cat mars.txt
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity
</code></pre>

<blockquote class="fragment" data-fragment-index="1" style="text-align: left;">
<span style="font-style: normal;">🧛</span> My last change was ill-considered. <span style="font-style: normal;">😕</span> How can I roll it back?
</blockquote>
<blockquote class="fragment" data-fragment-index="2" style="text-align: right;">
"checkout" what you did before. <span style="font-style: normal;">🐺</span>
</blockquote>

---

<!-- .slide: data-state="black_overlay logo yellow_flag" data-background="./files/lamp-g95a0e35a2_1920.jpg" -->
## Git Workflow

<img src="https://swcarpentry.github.io/git-novice/fig/git_staging.svg">

---

<!-- .slide: data-state="black_overlay logo yellow_flag" data-background="./files/lamp-g95a0e35a2_1920.jpg" data-auto-animate -->
## Dracula Makes a Typo 🧛

<blockquote style="text-align: left;">
<span style="font-style: normal;">🧛</span> Let's check out <b>mars.txt</b> from this previous commit.
</blockquote>

<pre style="font-size: x-large;" data-id="code-animation"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers="1|2-13">
$ git checkout 825524b  # Uh oh. Dracula forgot `mars.txt`.
Ɲote: switching to '825524b'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command. Example:

  git checkout -b &lt;new-branch-name&gt;

HEAD is now at 825524b Start notes on Mars as a base
</code></pre>

<blockquote class="fragment" style="text-align: left;">
<span style="font-style: normal;">🧛 😱</span>
</blockquote>

---

<!-- .slide: data-state="black_overlay logo yellow_flag" data-background="./files/lamp-g95a0e35a2_1920.jpg" data-auto-animate -->

## Detached HEAD 🤕

<pre data-id="code-animation-1"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers="1">
$: git checkout --detach 825524b  # notice the mandatory --detach flag
&nbsp;
&nbsp;
&nbsp;
</code></pre>

<pre data-id="code-animation-2"><code data-trim class="bash">
        "825524b"
            |
main (m1)--(m2)--(m3)
            |
           HEAD (detached)  # sounds worse than it is
&nbsp;
&nbsp;
</code></pre>

- Usually HEAD is a pointer to the tip of a branch
- But when checking out commit hashes or tags,<br>the HEAD is "detached" 

<div>
<br>
<br>
</div>

---

<!-- .slide: data-state="black_overlay logo yellow_flag" data-background="./files/lamp-g95a0e35a2_1920.jpg" data-auto-animate -->

## Detached HEAD 🤕

<pre data-id="code-animation-1"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers="2">
$: git checkout --detach 825524b  # notice the mandatory --detach flag
$: edit files; git add .; git commit -m "edited stuff";
&nbsp;
&nbsp;
</code></pre>

<pre data-id="code-animation-2"><code data-trim class="bash">
        "825524b"
            |
main (m1)--(m2)--(m3)
             \
             (x1)  # ephemeral, "virtual" branch
              |
             HEAD (detached)
</code></pre>

- Usually HEAD is a pointer to the tip of a branch
- But when checking out commit hashes or tags,<br>the HEAD is "detached" 
- Edits that you make now would be lost

<div>
<br>
</div>

---

<!-- .slide: data-state="black_overlay logo yellow_flag" data-background="./files/lamp-g95a0e35a2_1920.jpg" data-auto-animate -->

## Detached HEAD 🤕

<pre data-id="code-animation-1"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers="3">
$: git checkout --detach 825524b  # notice the mandatory --detach flag
$: edit files; git add .; git commit -m "edited stuff";
$: edit more; git add .; git commit -m "edited more";
&nbsp;
</code></pre>

<pre data-id="code-animation-2"><code data-trim class="bash">
        "825524b"
            |
main (m1)--(m2)--(m3)
             \
             (x1)--(x2)  # ephemeral, "virtual" branch
                    |
                   HEAD (detached)
</code></pre>

- Usually HEAD is a pointer to the tip of a branch
- But when checking out commit hashes or tags,<br>the HEAD is "detached" 
- Edits that you make now would be lost

<div>
<br>
</div>

---

<!-- .slide: data-state="black_overlay logo yellow_flag" data-background="./files/lamp-g95a0e35a2_1920.jpg" data-auto-animate -->

## Detached HEAD 🤕

<pre data-id="code-animation-1"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers="4">
$: git checkout --detach 825524b  # notice the mandatory --detach flag
$: edit files; git add .; git commit -m "edited stuff";
$: edit more; git add .; git commit -m "edited more";
$: git checkout -b "new_branch"
</code></pre>

<pre data-id="code-animation-2"><code data-trim class="bash">
        "825524b"
            |
main (m1)--(m2)--(m3)
             \
new_branch   (n1)--(n2)  # proper branch, will go down in history
                    |
                   HEAD
</code></pre>

- Usually HEAD is a pointer to the tip of a branch
- But when checking out commit hashes or tags,<br>the HEAD is "detached" 
- Edits that you make now would be lost
- Creating a new branch re-attaches HEAD

---

<!-- .slide: data-state="black_overlay logo yellow_flag" data-background="./files/lamp-g95a0e35a2_1920.jpg" -->
## Let Git Help You 💝

<pre data-id="code-animation"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers="1-9|11-16|18-26|28-31">
$ code mars.txt
$ git status
On branch main
Changes not staged for commit:
  (use "git add &lt;file&gt;..." to update what will be committed)
  (use "git restore &lt;file&gt;..." to discard changes in working directory)
	modified:   mars.txt

no changes added to commit (use "git add" and/or "git commit -a")

$ git add mars.txt
$ git status
On branch main
Changes to be committed:
  (use "git restore --staged &lt;file&gt;..." to unstage)
	modified:   mars.txt

$ git restore --staged mars.txt
$ git status
On branch main
Changes not staged for commit:
  (use "git add &lt;file&gt;..." to update what will be committed)
  (use "git restore &lt;file&gt;..." to discard changes in working directory)
	modified:   mars.txt

no changes added to commit (use "git add" and/or "git commit -a")

$ git restore mars.txt 
$ git status          
On branch main
nothing to commit, working tree clean
</code></pre>

Git gives you helpful suggestions on how to proceed<br>or how to undo.

---

<!-- .slide: data-state="black_overlay logo yellow_flag" data-background="./files/lamp-g95a0e35a2_1920.jpg" -->
## Quiz 1/3

<blockquote style="text-align: left;">
<span style="font-style: normal;">🧛</span> I deleted a line in mars.txt! How can I go back to the last committed version?<br>
<pre style="width: 100%;"><code style="overflow: hidden; font-style: normal;" data-trim class="bash" data-line-numbers>
  $ git checkout HEAD
  $ git checkout HEAD mars.txt
  $ git checkout HEAD~1 mars.txt
  $ git checkout &lt;ID of last commit&gt; mars.txt
</code></pre>
</blockquote>

<blockquote class="fragment" style="text-align: right;">
<ol>
  <li>restores <b>all</b> files, erasing <b>all</b> changes, and detaches HEAD ⚠️</li>
  <li>reverts only mars.txt by one commit</li>
  <li>reverts mars.txt to an earlier version ⚠️</li>
  <li>is equivalent to 2.</li>
</ol><span style="font-style: normal;">🐺</span>
</blockquote>

---

<!-- .slide: data-state="black_overlay logo yellow_flag" data-background="./files/lamp-g95a0e35a2_1920.jpg" data-auto-animate -->
## Quiz 2/3

<blockquote data-id="vlad1" style="text-align: left;">
<span style="font-style: normal;">🧛</span> I committed a file with an error! How can I revert a commit?<br>
</blockquote>
<blockquote style="text-align: right; font-style: normal;">
<pre data-id="code-animation" style="width: 100%;"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers>
# Find the commit ID where you want to revert to.
$ ???
# Copy the first 7 characters of that ID, e.g. 825524b
$ git revert [commit ID]
# Type commit message
# Save and close editor
</code></pre>
<span data-id="wolf1" style="font-style: normal;">🐺</span>
</blockquote>

---

<!-- .slide: data-state="black_overlay logo yellow_flag" data-background="./files/lamp-g95a0e35a2_1920.jpg" data-auto-animate -->
## Quiz 2/3

<blockquote data-id="vlad1" style="text-align: left;">
<span style="font-style: normal;">🧛</span> I committed a file with an error! How can I revert a commit?<br>
</blockquote>
<blockquote style="text-align: right; font-style: normal;">
<pre data-id="code-animation" style="width: 100%;"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers>
# Find the commit ID where you want to revert to.
$ git log
# Copy the first 7 characters of that ID, e.g. 825524b
$ git revert [commit ID]
# Type commit message
# Save and close editor
</code></pre>
<span data-id="wolf1" style="font-style: normal;">🐺</span>
</blockquote>

---

<!-- .slide: data-state="black_overlay logo yellow_flag" data-background="./files/lamp-g95a0e35a2_1920.jpg" data-auto-animate -->
## Quiz 2/3

<blockquote data-id="vlad1" style="text-align: left;">
<span style="font-style: normal;">🧛</span> I committed a file with an error! How can I revert a commit?<br>
</blockquote>
<blockquote style="text-align: right; font-style: normal;">
<pre data-id="code-animation" style="width: 100%;"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers>
# Find the commit ID where you want to revert to.
$ git show HEAD
# Copy the first 7 characters of that ID, e.g. 825524b
$ git revert [commit ID]
# Type commit message
# Save and close editor
</code></pre>
<span data-id="wolf1" style="font-style: normal;">🐺</span>
</blockquote>

---

<!-- .slide: data-state="black_overlay logo yellow_flag" data-background="./files/lamp-g95a0e35a2_1920.jpg" -->
## Quiz 3/3

<blockquote style="text-align: left;">
<span style="font-style: normal;">🧛</span> What would happen if I do...<br>
<pre data-id="code-animation" style="width: 100%; font-style: normal;"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers>
$ cd planets
$ echo "Venus is beautiful" > venus.txt
$ git add venus.txt
$ echo "Venus is too hot for a base" >> venus.txt
$ git commit -m "Comment on Venus as a base"
$ git checkout HEAD venus.txt
$ cat venus.txt
</code></pre>
</blockquote>

<blockquote class="fragment" style="text-align: right; font-style: normal;">
<pre data-id="code-animation" style="width: 100%; font-style: normal;"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers>
# Change into directory 'planets'
# Add "Venus is beatiful" to venus.txt
# Add venus.txt to staging area / index
# Append "Venus is too hot for a base" to venus.txt
# Commit the _previously staged_ venus.txt
# Revert local changes of venus.txt, and finally print
Venus is beautiful
</code></pre>
</code></pre>
<span data-id="wolf1" style="font-style: normal;">🐺</span>
</blockquote>

---

<!-- .slide: data-state="black_overlay logo yellow_flag" data-background="./files/lamp-g95a0e35a2_1920.jpg" -->
## Quiz 4/4
### Diff, What If... 🤔

<pre data-id="code-animation" style="width: max-content;"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers>
$ git diff HEAD~100 mars.txt
$ git diff [ID] mars.txt  # ID of most recent commit
</code></pre>

---

<!-- .slide: data-state="black_overlay logo yellow_flag" data-background="./files/lamp-g95a0e35a2_1920.jpg" -->
## Exercise 1/2
**git checkout** can be used to restore a previous commit when unstaged changes have been made, but will it also work for changes that have been staged but not committed?

Make a change to **mars.txt**, add that change, and use **git&nbsp;checkout** to see if you can remove your change.

---

<!-- .slide: data-state="black_overlay logo yellow_flag" data-background="./files/lamp-g95a0e35a2_1920.jpg" -->
## Exercise 2/2
Exploring history is an important part of Git. How can you find a commit ID from waaaaay back?

<ol>
  <li>Find a previous <b>commit message</b>
    <ul>
    <li><pre data-id="code-animation" style="padding: 0; margin: 0;"><code style="overflow: hidden;" data-trim class="bash">
    $ git log mars.txt 
    </code></pre></li>
    <li>Search the list</li>
    </ul>
  </li>
  <li>Find a previous <b>change in file content</b> with
    <ul>
    <li><pre data-id="code-animation" style="padding: 0; margin: 0;"><code style="overflow: hidden;" data-trim class="bash">
    $ git log --patch mars.txt 
    </code></pre></li>
    <li>Search the list</li>
    </ul>
  </li>
</ol>

---

<!-- .slide: data-state="black_overlay logo yellow_flag" data-background="./files/lamp-g95a0e35a2_1920.jpg" -->
## Tracking Changes: Key Points

- **git diff** displays differences between commits
- **git checkout** recovers old versions of files
