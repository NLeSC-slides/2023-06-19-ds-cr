<!-- .slide: data-state="standard 7" data-background="./files/clock-1527693_1280.jpg" id="undo"-->
<!-- https://pixabay.com/illustrations/clock-clock-face-waves-present-1527693/ -->

# Turn Back Time

---

<!-- .slide: data-state="standard 9" data-background="./files/clock-1527693_1280.jpg" id="undo_1"-->
<!-- https://pixabay.com/illustrations/clock-clock-face-waves-present-1527693/ -->

## Undo 1/4: Commit One More
<pre><code data-trim class="bash" data-line-numbers="1-2|3|4">
# No need to commit yet again! Make amends instead.
git commit -m "this should be all files"
git add dang_i_forgot_this_one.txt
git commit --amend -m "this should be all files"  # same commit!
</code></pre>

---

<!-- .slide: data-state="standard 9" data-background="./files/clock-1527693_1280.jpg" id="undo_2"-->
<!-- https://pixabay.com/illustrations/clock-clock-face-waves-present-1527693/ -->

## Undo 2/4: Restore to WORKSPACE

<pre style="font-size: x-large;"><code data-trim class="bash" data-line-numbers="1-3|4-5|6-8|9|10-15|16-17|18-19">
$: ls
  EDIT.txt
  DELETE.txt
$: git add .
$: git commit -m "add files"
$: rm DELETE.txt  # remove from WORKSPACE but not INDEX!
$: ls
  EDIT.txt
# edit EDIT.txt
$: git status
  Changes not staged for commit:
    (use "git add/rm &lt;file&gt;..." to update what will be committed)
    (use "git restore &lt;file&gt;..." to discard changes in working directory)
          deleted:  DELETE.txt
          modified: EDIT.txt
$: git restore EDIT.txt 
$: git restore DELETE.txt
$: ls
  DELETE.txt  EDIT.txt
</code></pre>

You can even "restore" files from another branch or the stash

<pre style="font-size: x-large;"><code data-trim class="bash">
$: git restore --source stash_name/branch_name filename
</code></pre>

---

<!-- .slide: data-state="standard 9" data-background="./files/clock-1527693_1280.jpg" id="undo_3"-->
<!-- https://pixabay.com/illustrations/clock-clock-face-waves-present-1527693/ -->

## Undo 3/4: Un-stage from INDEX

<pre style="font-size: x-large;"><code data-trim class="bash" data-line-numbers="1-6|7-8|9-17">
$: git status
  [...]
  Changes to be committed:
    (use "git rm --cached &lt;file&gt;..." to unstage)
  	new file:   SENSITIVE_PASSWORDS.txt  # Uh oh!
  	new file:   README.md
$: git rm --cached SENSITIVE_PASSWORDS.txt
  rm 'PASSWORDS.txt'
$: git status                   
  [...]
  Changes to be committed:
    (use "git rm --cached &lt;file&gt;..." to unstage)
  	new file:   README.md
  &nbsp;
  Untracked files:
    (use "git add &lt;file&gt;..." to include in what will be committed)
  	SENSITIVE_PASSWORDS.txt
</code></pre>

- <code style="font-size: smaller;">git rm --cached &lt;file&gt;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</code>remove from INDEX
- <code style="font-size: smaller;">git restore --staged &lt;file&gt;&nbsp;</code>copy from HEAD to INDEX

---

<!-- .slide: data-state="standard 9" data-background="./files/clock-1527693_1280.jpg" id="undo_4"-->
<!-- https://pixabay.com/illustrations/clock-clock-face-waves-present-1527693/ -->

## Undo 4/4: Rewriting history 📜

**⚠️ WARNING! ⚠️** You are playing with fire 🔥

- This is especially dangerous if other people based their work on your commits.
- It's possible to do it with only git commands ...
- ... but it's safer to use third-party tools, like git-filter-repo
  - https://github.com/newren/git-filter-repo/
- Use it to remove accidentally pushed passwords or API keys
