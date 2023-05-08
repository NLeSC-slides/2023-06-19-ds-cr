<!-- .slide: id="remotes_in_github" data-state="purple_overlay logo yellow_flag" data-background="./files/port-g38ab8a46f_1920.jpg" -->
<!-- Image by <a href="https://pixabay.com/users/pexels-2286921/?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=1845350">Pexels</a> from <a href="https://pixabay.com//?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=1845350">Pixabay</a> -->
# Remotes in GitHub

- How do I share my changes with others on the web?

---

<!-- .slide: data-state="purple_overlay logo yellow_flag" data-background="./files/port-g38ab8a46f_1920.jpg" -->
## HEAD in the Cloud ☁️

To _really_ collaborate with others, we need a shared repository. Let's create one on [github.com](https://github.com).

<ul>
  <li>Log in if you aren't already</li>
  <li>Click the ➕ on the top right</li>
  <li>Choose <b>New repository</b></li>
  <li>Name your project "planets"</li>
  <li>Pick an Owner, if necessary</li>
  <li>Set the visibility to <b>Public</b></li>
  <li>Do not add a README file, .gitignore or license</li>
  <li>Click <b>Create repository</b></li>
</ul>

---

<!-- .slide: data-state="purple_overlay logo yellow_flag" data-background="./files/port-g38ab8a46f_1920.jpg" -->
## Just Another Repository?

You effectively executed on the GitHub server:
<pre data-id="code-animation" style="width: max-content;"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers>
$ mkdir planets 
$ cd planets
$ git init
</code></pre>

---

<!-- .slide: data-state="purple_overlay logo yellow_flag" data-background="./files/port-g38ab8a46f_1920.jpg" -->
## The Holy Realms of Git - Extended

<ul>
  <li><b>workspace</b>&nbsp;&nbsp;📂</li>
  <ul>
    <li>Your filesystem</li>
  </ul>
  <li><b>index</b>&nbsp;&nbsp;🕒
    <ul>
      <li>Staging area</li>
      <li>Files wait patiently to be committed</li>
    </ul>
  </li>
  <li><b>local repository</b>&nbsp;&nbsp;🗂️
    <ul>
      <li>Contains branches, commits, history, etc.</li>
    </ul>
  </li>
  <li class="fragment"><b>remote repository</b>&nbsp;&nbsp;☁️
    <ul>
      <li>Cloud or self-hostet Git{Hub,Lab}</li>
      <li>Shared folder</li>
    </ul>
  </li>
<ul>

---

<!-- .slide: data-state="purple_overlay logo yellow_flag" data-background="./files/port-g38ab8a46f_1920.jpg" -->
## More Is Better

<div class="r-stack">
  <img class="fragment fade-out" data-fragment-index="0" src="https://swcarpentry.github.io/git-novice/fig/git-staging-area.svg">
  <img class="fragment fade-in" data-fragment-index="0" src="https://swcarpentry.github.io/git-novice/fig/git-freshly-made-github-repo.svg">
</div>

---

<!-- .slide: data-state="purple_overlay logo yellow_flag" data-background="./files/port-g38ab8a46f_1920.jpg" -->
## Connecting Worlds

Thankfully GitHub tells us how to proceed:
<pre data-id="code-animation"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers>
$ git remote add origin git@github.com:vlad/planets.git

# Confirm that it worked
$ git remote -v
origin   git@github.com:vlad/planets.git (fetch)
origin   git@github.com:vlad/planets.git (push)
</code></pre>

- **origin** is a local alias for the remote repository
- It could be anything, but **origin** is a strong convention

<footer>
A "remote" can also be a local folder or a network drive you share with someone
</footer>

---

<!-- .slide: data-state="purple_overlay logo yellow_flag" data-background="./files/port-g38ab8a46f_1920.jpg" -->
## Hi GitHub! 👋

<pre style="height: 300px;" data-id="code-animation"><code style="overflow: hidden; height: 300px;" data-trim class="bash" data-line-numbers="1-10|12-14|16-18">
$ ssh -T git@github.com  # Use your own URL here
The authenticity of host 'github.com (192.30.255.112)' can’t be
established. RSA key fingerprint is
SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])?
Please type 'yes', 'no' or the fingerprint: yes
Warning: Permanently added 'github.com' (RSA) to the list
of known hosts.
git@github.com: Permission denied (publickey).

# Oh right, GitHub does not know my SSH key yet!
$ cat ~/.ssh/id_ed25519.pub
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AA vlad@tran.sylvan.ia

# Try again (fingers crossed)
$ ssh -T git@github.com  # Use your own URL here
Hi vlad! You've successfully authenticated, but GitHub does not provide shell access.
</code></pre>

<ul class="fragment" data-fragment-index="2">
  <li>Click on your Profile Image, choose <b>Settings</b></li>
  <li>Choose <b>SSH and GPG keys</b></li>
  <li>Click on <b>New SSH key</b></li>
  <li>Paste the public(!) key from the terminal and give it a name</li>
  <li>Click on <b>Add SSH key</b></li>
</ul>

---

<!-- .slide: data-state="purple_overlay logo yellow_flag" data-background="./files/port-g38ab8a46f_1920.jpg" -->
## Spread Your Wings

<pre data-id="code-animation"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers>
$ git push -u origin main  # -u means "set upstream"
Enumerating objects: 16, done.
Counting objects: 100% (16/16), done.
Delta compression using up to 8 threads.
Compressing objects: 100% (11/11), done.
Writing objects: 100% (16/16), 1.45 KiB | 372.00 KiB/s, done.
Total 16 (delta 2), reused 0 (delta 0)
remote: Resolving deltas: 100% (2/2), done.
To https://github.com/vlad/planets.git
 * [new branch]      main -> main
</code></pre>

---

<!-- .slide: data-state="purple_overlay logo yellow_flag" data-background="./files/port-g38ab8a46f_1920.jpg" -->
## Password Managers

Windows will try to use a password manager to take care of SSH passwords. If you prefer typing it instead, you can disable it temporarily with
<pre data-id="code-animation" style="width: max-content;"><code style="overflow: hidden;" data-trim class="bash">
$ unset SSH_ASKPASS git push 
</code></pre>
or permanently through adding
<pre data-id="code-animation" style="width: max-content;"><code style="overflow: hidden;" data-trim class="bash">
&nbsp;unset SSH_ASKPASS 
</code></pre>
at the end of your **.bashrc** file.

---

<!-- .slide: data-state="purple_overlay logo yellow_flag" data-background="./files/port-g38ab8a46f_1920.jpg" -->
## Connected 🔌

<img src="https://swcarpentry.github.io/git-novice/fig/github-repo-after-first-push.svg">

---

<!-- .slide: data-state="purple_overlay logo yellow_flag" data-background="./files/port-g38ab8a46f_1920.jpg" -->
## Explore the GitHub UI 1/2

- Browse the **planets** repository on GitHub
- Click on **X Commits** above your files
- Click on the ellipsis **· · ·** next to a commit
- Click on a commit itself
- Click on **Browse files**

<p class="fragment">
How can you get the same information from the terminal?
</p>
<pre class="fragment" data-id="code-animation"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers>
git log
git diff ID1..ID2
git checkout ID  # don't forget to put back the repo in a good state!
</code></pre>
<p class="fragment">
Note the <b>relative</b> timestamp in the commit list. What is the <b>absolute</b> time of a commit?
</p>
<p class="fragment">
Hover over the timestamp.
</p>

---

<!-- .slide: data-state="purple_overlay logo yellow_flag" data-background="./files/port-g38ab8a46f_1920.jpg" -->
## Explore the GitHub UI 2/2

How can you ...
- download a file from GitHub?
- upload a file to GitHub?
- create a file on GitHub?
- edit a file from GitHub?

---

<!-- .slide: data-state="purple_overlay logo yellow_flag" data-background="./files/port-g38ab8a46f_1920.jpg" -->
## Quiz!

<ul>
  <li>What is the difference between <b>commit</b> and <b>push</b>?</li>
  <ul>
    <li class="fragment"><b>commit</b> writes staged changes to the local repository</li>
    <li class="fragment"><b>push</b> updates the remote repository with local changes</li>
  </ul>
</ul>

---

<!-- .slide: data-state="purple_overlay logo yellow_flag" data-background="./files/port-g38ab8a46f_1920.jpg" -->
## Remotes: Key Points

<ul style="font-size: smaller;">
  <li>A local Git repository can be connected to one or more remote repositories</li>
  <li>Use the SSH protocol to connect to remote repositories</li>
  <li><b>git push</b> copies changes from a local repository to a remote repository</li>
  <li><b>git pull</b> copies changes from a remote repository to a local repository</li>
</ul>
