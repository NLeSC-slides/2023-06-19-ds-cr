<!-- .slide: data-state="standard 7" data-background="./files/barber-shop-5212059_1280.jpg" id="everyday"-->
<!-- https://pixabay.com/photos/barber-shop-iran-cosmetology-5212059/ -->

# Everyday git

---

<!-- .slide: data-state="standard" data-background="./files/barber-shop-5212059_1280.jpg" id="status"-->
<!-- https://pixabay.com/photos/barber-shop-iran-cosmetology-5212059/ -->

## Status

<pre data-id="code-animation" style="font-size: large; width: 70%;"><code data-trim class="bash">
$: git status         
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged &lt;file&gt;..." to unstage)
	modified:   00_title.md

Changes not staged for commit:
  (use "git add/rm &lt;file&gt;..." to update what will be committed)
  (use "git restore &lt;file&gt;..." to discard changes in working directory)
	modified:   index.html
	deleted:    slides/environments/reveal.js

Untracked files:
  (use "git add &lt;file&gt;..." to include in what will be committed)
	slides/advanced_git/
</code></pre>

- Which files are staged (to be commited)?
- Which files are changed, but not staged?
- Which files are not tracked?
- You will use this very often!

---

<!-- .slide: data-state="standard" data-background="./files/barber-shop-5212059_1280.jpg" id="rm"-->
<!-- https://pixabay.com/photos/barber-shop-iran-cosmetology-5212059/ -->

## (Re)move Stuff


<pre data-id="code-animation"><code data-trim class="bash">
    rm file.txt                    # delete files from your WORKSPACE
    mv file_2.txt file_3.txt       # move or rename files in your WORKSPACE
</code></pre>


<pre data-id="code-animation"><code data-trim class="bash">
    rm file.txt                    # delete files from your WORKSPACE
    mv file_2.txt file_3.txt       # move files in your WORKSPACE
    git add file.txt               # ... and your INDEX
    git add file_2.txt file_3.txt  # ... and your INDEX
</code></pre>

<pre data-id="code-animation"><code data-trim class="bash">
    git rm file.txt                # Shorthand for rm X & git add X
    git mv file_2.txt file_3.txt   # Shorthand for mv X & git add X
</code></pre>


- "git add" does not add files to the **index**, but _changes_
- The _change_ of removing a file from the **workspace** must be _added_ to the **index**

---

<!-- .slide: data-state="standard" data-background="./files/barber-shop-5212059_1280.jpg" id="gitignore"-->
<!-- https://pixabay.com/photos/barber-shop-iran-cosmetology-5212059/ -->

## Ignore stuff
.gitignore is a file in the root of your project
<pre data-id="code-animation"><code data-trim class="bash">
$: cat .gitignore
  # don't track passwords.txt
  passwords.txt
  # ignore *.tmp files, notice that wildcards '*' work
  *.tmp
  # but _do_ keep track of important.tmp
  !important.tmp
  # ignore 'logs' directories _anywhere_
  **/logs
  # ignore debug-a.log ... debug-z.log
  debug-[a-z].log
</code></pre>

- Hide certain files from git
- They stay in your **workspace** ...
  - but out of **index**, **local repository**, **upstream repository**
- Examples: Passwords or API tokens, log files or temporary files

---

<!-- .slide: data-state="standard" data-background="./files/barber-shop-5212059_1280.jpg" id="external"-->
<!-- https://pixabay.com/photos/barber-shop-iran-cosmetology-5212059/ -->

### External Repos

<pre data-id="code-animation"><code data-trim class="bash">
    # Add an UPSTREAM REPOSITORY to your LOCAL REPOSITORY
    git remote add origin git@gitlab.com:OleMussmann/my_project.git

    # Get repo from an UPSTREAM REPOSITORY, creating a LOCAL REPOSITORY
    git clone https://gitlab.com:OleMussmann/my_project.git  # or...
    git clone git@gitlab.com:OleMussmann/my_project.git

    # Get latest updates from the UPSTREAM REPOSITORY, and merge them
    git pull git@gitlab.com:OleMussmann/my_project.git
    # Which is shorthand for:
    # Get latest updates from the UPSTREAM REPOSITORY
    git fetch git@gitlab.com:OleMussmann/my_project.git
    # Merge the remote changes to your local branch
    git merge &lt;current_branch&gt; &lt;origin/current_branch&gt;

    # Push changes from your LOCAL REPOSITORY to the UPSTREAM REPOSITORY
    git push git@gitlab.com:OleMussmann/my_project.git
</code></pre>


- Always "git pull" before working on a shared repo!
  - Changes in both **local repository** and **upstream repository** introduces _merge conflicts_

---

<!-- .slide: data-state="standard" data-background="./files/barber-shop-5212059_1280.jpg" data-transition="none"-->
<!-- https://pixabay.com/photos/barber-shop-iran-cosmetology-5212059/ -->

## Branches 1/2

![Branches](./files/branches_1.svg)

---

<!-- .slide: data-state="standard" data-background="./files/barber-shop-5212059_1280.jpg" data-transition="none"-->
<!-- https://pixabay.com/photos/barber-shop-iran-cosmetology-5212059/ -->

## Branches 1/2

![Branches](./files/branches_2.svg)

---

<!-- .slide: data-state="standard" data-background="./files/barber-shop-5212059_1280.jpg" data-transition="none"-->
<!-- https://pixabay.com/photos/barber-shop-iran-cosmetology-5212059/ -->

## Branches 1/2

![Branches](./files/branches_3.svg)

---

<!-- .slide: data-state="standard" data-background="./files/barber-shop-5212059_1280.jpg" data-transition="none"-->
<!-- https://pixabay.com/photos/barber-shop-iran-cosmetology-5212059/ -->

## Branches 1/2

![Branches](./files/branches_4.svg)

---

<!-- .slide: data-state="standard" data-background="./files/barber-shop-5212059_1280.jpg" id="branch_1"  data-transition="none"-->
<!-- https://pixabay.com/photos/barber-shop-iran-cosmetology-5212059/ -->

## Branches 1/2

![Branches](./files/branches_5.svg)

---

<!-- .slide: data-state="standard" data-background="./files/barber-shop-5212059_1280.jpg" id="branch_2"-->
<!-- https://pixabay.com/photos/barber-shop-iran-cosmetology-5212059/ -->

## Branches 2/2

<pre data-id="code-animation"><code data-trim class="bash" data-line-numbers="1-4|6-10|12-17|19-23|25-26">
$: git branch                         # list existing branches
    existing_branch
  * main
    old_branch
&nbsp;
$: git switch existing_branch         # switch to an existing branch
$: git branch
  * existing_branch
    main
    old_branch
&nbsp;
$: git switch -c new_feature_branch # c_reate (and switch to) branch
$: git branch
    existing_branch
    main
  * new_feature_branch
    old_branch
&nbsp;
$: git branch -d old_branch           # d_elete a branch
$: git branch
    existing_branch
    main
  * new_feature_branch
&nbsp;
# new branches have to be explicitly pushed to a remote:
$: git push -u origin new_feature_branch  # u_pstream: origin
</code></pre>

<ul class="fragment">
  <li>origin is an alias for the UPSTREAM REPOSITORY URL</li>
</ul>

---

<!-- .slide: data-state="standard" data-background="./files/barber-shop-5212059_1280.jpg" id="branch_style"-->
<!-- https://pixabay.com/photos/barber-shop-iran-cosmetology-5212059/ -->

## Branch Style

- Use "main" instead of "master" for your main branch
- Don't commit directly to "main"
  - "main" will be what users will clone and should be stable
- Use a "development" branch for daily work
  - Merge to "main", once stable
- Use feature branches for developing features
  - Merge to "development"
- Use descriptive branch names

---

<!-- .slide: data-state="standard" data-background="./files/barber-shop-5212059_1280.jpg" data-auto-animate -->
<!-- https://pixabay.com/photos/barber-shop-iran-cosmetology-5212059/ -->

## Detached HEAD 🤕

<pre data-id="code-animation-1"><code data-trim class="bash" data-line-numbers="1">
$: 
&nbsp;
&nbsp;
&nbsp;
</code></pre>

<pre data-id="code-animation-2"><code data-trim class="bash">
          "v1.0"
            |
main (m1)--(m2)--(m3)
                  |
                 HEAD # default, HEAD points to the tip of "main"
&nbsp;
&nbsp;
</code></pre>

- Usually HEAD is a pointer to the tip of a branch

<div>
<br>
<br>
<br>
<br>
</div>

---

<!-- .slide: data-state="standard" data-background="./files/barber-shop-5212059_1280.jpg" data-auto-animate -->
<!-- https://pixabay.com/photos/barber-shop-iran-cosmetology-5212059/ -->

## Detached HEAD 🤕

<pre data-id="code-animation-1"><code data-trim class="bash" data-line-numbers="1">
$: git switch --detach v1.0  # notice the mandatory --detach flag
&nbsp;
&nbsp;
&nbsp;
</code></pre>

<pre data-id="code-animation-2"><code data-trim class="bash">
          "v1.0"
            |
main (m1)--(m2)--(m3)
            |
           HEAD (detached)  # sounds worse than it is
&nbsp;
&nbsp;
</code></pre>

- Usually HEAD is a pointer to the tip of a branch
- But when switching to commit hashes or tags,<br>the HEAD is "detached" 

<div>
<br>
<br>
</div>

---

<!-- .slide: data-state="standard" data-background="./files/barber-shop-5212059_1280.jpg" data-auto-animate -->
<!-- https://pixabay.com/photos/barber-shop-iran-cosmetology-5212059/ -->

## Detached HEAD 🤕

<pre data-id="code-animation-1"><code data-trim class="bash" data-line-numbers="2">
$: git switch --detach v1.0  # notice the mandatory --detach flag
$: edit files; git add .; git commit -m "edited stuff";
&nbsp;
&nbsp;
</code></pre>

<pre data-id="code-animation-2"><code data-trim class="bash">
          "v1.0"
            |
main (m1)--(m2)--(m3)
             \
             (x1)  # ephemeral, "virtual" branch
              |
             HEAD (detached)
</code></pre>

- Usually HEAD is a pointer to the tip of a branch
- But when switching to commit hashes or tags,<br>the HEAD is "detached" 
- Edits that you make now would be lost

<div>
<br>
</div>

---

<!-- .slide: data-state="standard" data-background="./files/barber-shop-5212059_1280.jpg" data-auto-animate -->
<!-- https://pixabay.com/photos/barber-shop-iran-cosmetology-5212059/ -->

## Detached HEAD 🤕

<pre data-id="code-animation-1"><code data-trim class="bash" data-line-numbers="3">
$: git switch --detach v1.0  # notice the mandatory --detach flag
$: edit files; git add .; git commit -m "edited stuff";
$: edit more; git add .; git commit -m "edited more";
&nbsp;
</code></pre>

<pre data-id="code-animation-2"><code data-trim class="bash">
          "v1.0"
            |
main (m1)--(m2)--(m3)
             \
             (x1)--(x2)  # ephemeral, "virtual" branch
                    |
                   HEAD (detached)
</code></pre>

- Usually HEAD is a pointer to the tip of a branch
- But when switching to commit hashes or tags,<br>the HEAD is "detached" 
- Edits that you make now would be lost

<div>
<br>
</div>

---

<!-- .slide: data-state="standard" data-background="./files/barber-shop-5212059_1280.jpg" id="detached" data-auto-animate -->
<!-- https://pixabay.com/photos/barber-shop-iran-cosmetology-5212059/ -->

## Detached HEAD 🤕

<pre data-id="code-animation-1"><code data-trim class="bash" data-line-numbers="4">
$: git switch --detach v1.0  # notice the mandatory --detach flag
$: edit files; git add .; git commit -m "edited stuff";
$: edit more; git add .; git commit -m "edited more";
$: git switch -c "new_branch"
</code></pre>

<pre data-id="code-animation-2"><code data-trim class="bash">
          "v1.0"
            |
main (m1)--(m2)--(m3)
             \
new_branch   (n1)--(n2)  # proper branch, will go down in history
                    |
                   HEAD
</code></pre>

- Usually HEAD is a pointer to the tip of a branch
- But when switching to commit hashes or tags,<br>the HEAD is "detached" 
- Edits that you make now would be lost
- Creating a new branch re-attaches the HEAD


---

<!-- .slide: data-state="standard" data-background="./files/barber-shop-5212059_1280.jpg" id="merge"-->
<!-- https://pixabay.com/photos/barber-shop-iran-cosmetology-5212059/ -->

## Merge
<pre data-id="code-animation"><code data-trim class="bash">
    git switch -c new_feature_branch   # c_reate (and switch to) new branch
    # do things on new_branch, like adding and committing
    git switch main                    # switch to target branch
    git merge new_feature_branch       # merge new_feature_branch into main
</code></pre>

- git v2.23 instroduces 'git switch' and 'git restore'
  - They replace 'git checkout'

<footer><a href="https://stackoverflow.com/questions/1838873/visualizing-branch-topology-in-git">Visualizing branch topology in Git</a></footer>

---

<!-- .slide: data-state="standard" data-background="./files/barber-shop-5212059_1280.jpg" data-transition="none"-->
<!-- https://pixabay.com/photos/barber-shop-iran-cosmetology-5212059/ -->

## Tags 1/2
#### Label your commits 🏷️

![Branches](./files/branches_5.svg)

---

<!-- .slide: data-state="standard" data-background="./files/barber-shop-5212059_1280.jpg" id="tag" data-transition="none"-->
<!-- https://pixabay.com/photos/barber-shop-iran-cosmetology-5212059/ -->

## Tags 1/2
#### Label your commits 🏷️

![Branches](./files/branches_all.svg)

---

<!-- .slide: data-state="standard" data-background="./files/barber-shop-5212059_1280.jpg" id="tag_2"-->
<!-- https://pixabay.com/photos/barber-shop-iran-cosmetology-5212059/ -->

## Tags 2/2

<pre><code data-trim class="bash">
$: git tag                           # show all tags
  v1.0
  v1.1
$: git tag -a v1.2 -m "new gui"      # a_nnotated tag with a m_essage
$: git tag found_bug_in_this_commit  # lightweight tag: bookmarks
$: git push origin v1.2              # push a single tag
$: git push --tags                   # or push all tags
</code></pre>

<pre><code data-trim class="bash">
$: git switch --detach v1.0          # detach head and switch to a tag
</code></pre>

- Annotated tags contain lots of metadata<br>
  Use them for actual tagging
- Lightweight tags are bookmarks<br>
  Use them as personal bookmarks
- You can switch to tags, [detaching the HEAD](#/detached)
