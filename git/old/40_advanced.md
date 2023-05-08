<!-- .slide: data-state="standard 5" data-background="./files/religion-3491357_1280.jpg" id="advanced"-->
<!-- https://pixabay.com/photos/religion-meditation-faith-light-3491357/ -->

# Advanced git

---

<!-- .slide: data-state="standard 7" data-background="./files/religion-3491357_1280.jpg" id="status_2"-->
<!-- https://pixabay.com/photos/religion-meditation-faith-light-3491357/ -->

## Advanced Status 1/2

<h4>Differences</h4>

<pre style="font-size: x-large;"><code data-trim class="bash">
git diff file.txt                   # WORKSPACE - INDEX
git diff &lt;commit&gt; file.txt          # WORKSPACE - COMMIT HASH
git diff HEAD file.txt              # WORKSPACE - LOCAL REPO (COMMIT H. = HEAD)
git diff --staged file.txt          # INDEX - LOCAL REPO (HEAD)
git diff --staged &lt;commit&gt; file.txt # INDEX - COMMIT HASH
</code></pre>

<pre style="font-size: x-large;"><code data-trim class="bash">
$: git diff      # Omit filename to show _all_ changed files
diff --git a/file.txt b/file.txt
index 00dedf6..02ef113 100644
--- a/file.txt   # old version
+++ b/file.txt   # new version
@@ -1 +1 @@      # one line changed
-abcde           # removed lines
+new line here!  # added lines
</code></pre>

---

<!-- .slide: data-state="standard 7" data-background="./files/religion-3491357_1280.jpg" id="status_3"-->
<!-- https://pixabay.com/photos/religion-meditation-faith-light-3491357/ -->

## Advanced Status 2/2

<div style="width: 53%; float: left;">
<h4>Commit history</h4>

<pre style="font-size: medium"><code data-trim class="bash">
    # try tab completion, a file name or a commit hash!
    $: git log
    # HEAD points to the latest commit in the LOCAL REPOSITORY
    commit 0fb599d96521bd27b05b0a6f963ba6ab903d349c (HEAD -&gt; main)
    Author: ole &lt;gitlab+account@ole.mn&gt;
    Date:   Mon Jun 13 11:07:30 2022 +0200
    
        add content to README
    
    commit 89d8a1b57f2440693aff2f7b5003201836aa24d4
    Author: ole &lt;gitlab+account@ole.mn&gt;
    Date:   Mon Jun 13 11:06:51 2022 +0200
    
        create README.md
    &nbsp;
    &nbsp;
</code></pre>
</div>

<div style="width: 46%; float: right;">
<h4>Show commits</h4>

<pre style="font-size: medium;"><code data-trim class="bash">
    # try tab completion, a branch, tag or a commit hash!
    $: git show 0fb5  # four hash characters are enough
    commit 0fb599d96521bd27b05b0a6f963[...] (HEAD -> main)
    Author: ole &lt;gitlab+account@ole.mn&gt;
    Date:   Mon Jun 13 11:07:30 2022 +0200
    
        add content to README
    
    diff --git a/README.md b/README.md
    index e69de29..8824ebc 100644
    --- a/README.md
    +++ b/README.md
    @@ -0,0 +1,3 @@
    +Hi! I am a README file.
    +
    +I have content.
</code></pre>
</div>

<h4>Blaming!<br>
(... or "who changed a file"?)</h4>
<pre style="font-size: medium; width: 50%;"><code data-trim class="bash">
# try tab completion or a file name!
$: git blame file.txt
e546a240 (ole 2022-06-10 11:12:27 +0200 1) new line here!
682bc7ca (ole 2022-06-10 11:19:20 +0200 2) and another one
a9a390b3 (ole 2022-06-10 11:20:05 +0200 3) many
a9a390b3 (ole 2022-06-10 11:20:05 +0200 4) more lines
</code></pre>


---

<!-- .slide: data-state="standard 7" data-background="./files/religion-3491357_1280.jpg" id="stash"-->
<!-- https://pixabay.com/photos/religion-meditation-faith-light-3491357/ -->

## Stash 1/2
#### Putting things away temporarily

<pre><code data-trim class="bash">
$: git status         
  On branch main
  Changes to be committed:
    (use "git restore --staged &lt;file&gt;..." to unstage)
  	new file:   staged_file
&nbsp;
  Untracked files:
    (use "git add &lt;file&gt;..." to include in what will be committed)
  	workspace_file
  &nbsp;
$: git stash -u  # Optional -u to include u_ntracked files
  Saved working directory and index state WIP on main: [...]
&nbsp;
$: git status
  On branch main
  nothing to commit, working tree clean
</code></pre>

---

<!-- .slide: data-state="standard 7" data-background="./files/religion-3491357_1280.jpg" id="stash_2"-->
<!-- https://pixabay.com/photos/religion-meditation-faith-light-3491357/ -->

## Stash 2/2
#### Retrieving things

<pre><code style="height: 14em;" data-trim class="bash" data-line-numbers="1-3|5-6|5-6,8|5-6,9|5-6,10|10-18">
$: git status
  On branch main
  nothing to commit, working tree clean
&nbsp;
$: git stash list
  stash@{0}: WIP on main: 50f8199 add committed_file  # only one item
&nbsp;
$: git stash apply stash@\{0\} # Omit stash name for latest
$: git stash apply             # Use latest stash
$: git stash apply --index     # Optional --index to also apply INDEX
  On branch main
  Changes to be committed:
    (use "git restore --staged &lt;file&gt;..." to unstage)
  	new file:   staged_file
&nbsp;
  Untracked files:
    (use "git add &lt;file&gt;..." to include in what will be committed)
  	workspace_file
</code></pre>

Too many changes since the stashing might might create [merge conflicts](#/conflicts). You can make a branch instead and work from there:

<pre><code data-trim class="bash" data-line-numbers="">
# Omit stash name for latest
$: git stash branch new_stash_branch stash@\{0\}
</code></pre>

---

<!-- .slide: data-state="standard 7" data-background="./files/religion-3491357_1280.jpg" id="conflicts"-->
<!-- https://pixabay.com/photos/religion-meditation-faith-light-3491357/ -->

## Merge Conflicts

- Merge conflicts occur when you try to merge a branch/stash that conflicts with your local version, e.g.
  - Overlapping edits in the same file (obvious)
  - Win vs Linux file endings, tabs to spaces (invisible)

<br>
<br>

1. Don't panic! You can always abort the merge
1. Git gives you helpful error messages and the tools to resolve the conflicts
1. You are not the first one to encounter that specific error, google and stackoverflow are your friend

---

<!-- .slide: data-state="standard 7" data-background="./files/religion-3491357_1280.jpg" id="redneck"-->
<!-- https://pixabay.com/photos/religion-meditation-faith-light-3491357/ -->

## Redneck Style

Don't tell anyone you've got this from me... 🙊 But this is a totally viable strategy. Here we go.

<ul class="fragment">
  <li>Do a fresh git clone into a <b>separate folder</b></li>
  <li>Work in your changes</li>
  <li>Push your changes</li>
  <li>Delete your original folder (optional)</li>
<ul>

---

<!-- .slide: data-state="standard 7" data-background="./files/religion-3491357_1280.jpg" id="by_hand" data-auto-animate -->
<!-- https://pixabay.com/photos/religion-meditation-faith-light-3491357/ -->

## By Hand

<pre><code style="font-size: large; height: 30em;" data-trim class="r" data-line-numbers="1-7|9-23|25-39|41-50|52-60">
$: git pull  # Oh no, a merge conflict! (Don't panic, I've got this.)
  [...]
  From https://renkulab.io/gitlab/renkuaccount/git
     c297618..09f2cc8  main       -&gt; origin/main
  Auto-merging file.txt
  CONFLICT (content): Merge conflict in file.txt
  Automatic merge failed; fix conflicts and then commit the result.
&nbsp;
$: git status  # git status shows me what's wrong
  On branch main
  Your branch and 'origin/main' have diverged,
  and have 1 and 1 different commits each, respectively.
    (use "git pull" to merge the remote branch into yours)  # Not so helpful, it failed
&nbsp;
  You have unmerged paths.
    (fix conflicts and run "git commit")  # Helpful!
    (use "git merge --abort" to abort the merge)  # Panic button, good to know
&nbsp;
  Unmerged paths:
    (use "git add &lt;file&gt;..." to mark resolution)  # git assumes i'm happy after 'add'
          both modified:   file.txt
&nbsp;
  no changes added to commit (use "git add" and/or "git commit -a")
&nbsp;
$: git diff  # git diff shows me affected lines (phew, does not look too bad 😅)
  diff --cc file.txt
  index 2054524,f15ccdf..0000000
  --- a/file.txt
  +++ b/file.txt
  @@@ -1,5 -1,5 +1,9 @@@  # merged lines 1-5 ("file a"), 1-5 ("file b") to lines 1-9 ("file c") ?!
    text text
    all the same everywhere
  ++&lt;&lt;&lt;&lt;&lt;&lt;&lt; HEAD               # Diff start
   +line edited locally        # Part from HEAD ("file a")
  ++=======                    # Separator
  + line edited on remote      # Part from remote ("file b") (commit hash 09f2c[...])
  ++&gt;&gt;&gt;&gt;&gt;&gt;&gt; 09f2cc8e449905494d3ca61d78c5b071d62db1cf  # Diff end
    more same lines
    no conflicts down here
&nbsp;
$: cat file.txt  # Looking at the file.txt content. Aha! This is "file c"
  text text
  all the same everywhere
  &lt;&lt;&lt;&lt;&lt;&lt;&lt; HEAD              # I should remove these control lines
  line edited locally       # I can keep this line ...
  =======                   # (remove)
  line edited on remote     # ... or this line. In fact, I can edit the file however I want!
  &gt;&gt;&gt;&gt;&gt;&gt;&gt; 09f2cc8e449905494d3ca61d78c5b071d62db1cf  # (remove)
  more same lines
  no conflicts down here
&nbsp;
$: [edit file.txt, fix conflicting lines, remove control lines]
&nbsp;
$: git add file.txt
&nbsp;
$: git commit -m "resolve merge conflict"
  [main 0835b22] resolve merge conflict
&nbsp;
$: git push  # All clear! 😃
  [...]
</code></pre>

---

<!-- .slide: data-state="standard 7" data-background="./files/religion-3491357_1280.jpg" id="mergetool_1" -->
<!-- https://pixabay.com/photos/religion-meditation-faith-light-3491357/ -->

## With a mergetool: vimdiff

<pre style="width: max-content;"><code data-trim class="bash">
    git mergetool --tool=vimdiff
</code></pre>

<img style="height: 22vh;" src="./files/vimdiff.png">

- Also show LOCAL, BASE (best common ancestor), REMOTE
- vim is about everywhere
- Difficult to learn, hard to master, worth knowing the basics!

---

<!-- .slide: data-state="standard 7" data-background="./files/religion-3491357_1280.jpg" id="mergetool_2" -->
<!-- https://pixabay.com/photos/religion-meditation-faith-light-3491357/ -->

## With a mergetool: meld

<pre style="width: max-content;"><code data-trim class="bash">
    git mergetool --tool=meld
</code></pre>

<img style="height: 22vh;" src="./files/meld.png">

- Merge to "best common ancestor" (middle)
- GUI tools like meld are more intuitive
- Not available in CLI environments
