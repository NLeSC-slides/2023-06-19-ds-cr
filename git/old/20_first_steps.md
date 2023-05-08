<!-- .slide: data-state="standard 7" data-background="./files/cat-727266_1280.jpg" id="first_steps"-->
<!-- https://pixabay.com/photos/cat-family-pet-love-happy-animal-727266/ -->

# First Steps

---

<!-- .slide: data-state="standard" data-background="./files/cat-727266_1280.jpg" id="config"-->
<!-- https://pixabay.com/photos/cat-family-pet-love-happy-animal-727266/ -->

## Config

<pre data-id="code-animation"><code data-trim class="bash">
# Mandatory (for anything more than clone)
git config --global user.name "Your Full Name"
git config --global user.email your@email.com

# Recommended
git config --global init.defaultBranch main

# Optional
git config --global merge.tool "meld"  # see [1] for options
git config --global core.editor "vim"  # see [2] for options

# List all set options
git config --list --show-origin
</code></pre>

Extensive config options:<br>
https://git-scm.com/book/en/v2/Customizing-Git-Git-Configuration#_git_config

<footer>
[1] git mergetool --tool-help
<br>
[2] <a href="https://git-scm.com/book/en/v2/Appendix-C:-Git-Commands-Setup-and-Config#ch_core_editor">https://git-scm.com/book/en/v2/Appendix-C:-Git-Commands-Setup-and-Config#ch_core_editor</a>
</footer>

---

<!-- .slide: data-state="standard" data-background="./files/cat-727266_1280.jpg" id="init"-->
<!-- https://pixabay.com/photos/cat-family-pet-love-happy-animal-727266/ -->

## New Repo

<pre data-id="code-animation"><code data-trim class="bash">
    git init                        # or ...
    git init --initial-branch=main  # if init.defaultBranch is not set
</code></pre>

- Creates a hidden `.git` folder
- The current folder is now your **workspace**

---

<!-- .slide: data-state="standard" data-background="./files/cat-727266_1280.jpg" id="add"-->
<!-- https://pixabay.com/photos/cat-family-pet-love-happy-animal-727266/ -->

## Add Stuff

<pre data-id="code-animation"><code data-trim class="bash">
    git add file
    git add folder
    git add *.txt
    git add .
</code></pre>

- Add files and directories to a mysterious **index**
  - a.k.a. **staging area**
- Empty folders will be ignored
  - Prevent this by adding an empty, hidden file, e.g. ".gitkeep"

Technically, you add _changes_, like the change of adding a file. Or editing a file. Even the change of removing a file.

---

<!-- .slide: data-state="standard" data-background="./files/cat-727266_1280.jpg" id="commit"-->
<!-- https://pixabay.com/photos/cat-family-pet-love-happy-animal-727266/ -->

## Committing

Commit: a set of previously added, related changes

<div class="fragment">
  <pre data-id="code-animation"><code data-trim class="bash">
      git commit -m "fix server crash, resolve #5"  # shortcut, only header
      git commit  # extended version, editor opens, enter header and message
  </code></pre>

  <ul>
    <li>Commit changes to the <b>local repository</b></li>
    <li>Referenced bugs will be closed on Git{Hub,Lab}, if pushed to the <b>upstream repository</b>!</li>
    <ul>
      <li>Use any of <b>close #5, closes #5, closed #5, fix #5, fixes #5, fixed #5, resolve #5, resolves #5, resolved #5</b></li>
    </ul>
  </ul>
</div>

---

<!-- .slide: data-state="standard" data-background="./files/cat-727266_1280.jpg" id="commit_style"-->
<!-- https://pixabay.com/photos/cat-family-pet-love-happy-animal-727266/ -->

### Commit Style

- Write meaningful commit messages
- Use imperative: change config, remove file, add tests
- Header should be 50 chars or less, message can be longer
- Make atomic commits!<sup>[1]</sup>
  - Commits can span multiple files, but should have _one_ function, like
    - Add tests to module xyz
    - Use new house-style
    - Introduce logging

<footer>[1] atomic: a single irreducible unit or component in a larger system</footer>

---

<!-- .slide: data-state="standard" data-background="./files/cat-727266_1280.jpg" id="push"-->
<!-- https://pixabay.com/photos/cat-family-pet-love-happy-animal-727266/ -->

## Pushing

<pre><code data-trim class="bash">
# Push changes in your LOCAL REPOSITORY to a REMOTE REPOSITORY
$: git push

# New branches have to be pushed explicitly
$: git push -u origin branch_name

# Tags as well
$: git push tagname  # single tag
$: git push --tags  # all tag
</code></pre>

- Origin is an alias for your UPSTREAM REPOSITORY URL
- See [External Repos](#/external) for how to set up an UPSTREAM REPOSITORY
- Learn more about [Branches](#/branch_1) and [Tags](#/tag)

---

<!-- .slide: data-state="standard" data-background="./files/cat-727266_1280.jpg" id="realms"-->
<!-- https://pixabay.com/photos/cat-family-pet-love-happy-animal-727266/ -->

## The 5 Holy Realms of git

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
  <li class="fragment"><b>upstream repository</b>&nbsp;&nbsp;☁️
    <ul>
      <li>Cloud or self-hostet Git{Hub,Lab}</li>
      <li>Shared folder</li>
    </ul>
  </li>
  <div class="fragment">
  <hr>
  <li><b>stash</b>&nbsp;&nbsp;📦
    <ul>
      <li>Temporary storage area</li>
    </ul>
  </li>
  </div>
<ul>

Notes:
Most important slide of today

Upstream Repo in a minute
