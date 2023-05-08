<!-- .slide: id="setting_up_git" data-state="blue_overlay logo yellow_flag" data-background="./files/hd-wallpaper-g72e534791_1920.jpg" -->
<!-- Image by <a href="https://pixabay.com/users/yuri_b-2216431/?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=3292932">Yuri</a> from <a href="https://pixabay.com//?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=3292932">Pixabay</a> -->
# Setting Up Git
How do I set up Git?

---

## Do What I Say!
<!-- .slide: data-state="blue_overlay logo yellow_flag" data-background="./files/hd-wallpaper-g72e534791_1920.jpg" -->
Git commands follow the grammar of

<pre style="width: max-content;" data-id="code-animation"><code style="overflow: hidden;" data-trim class="bash">
&nbsp;git verb options&nbsp;
</code></pre>

---

<!-- .slide: data-state="blue_overlay logo yellow_flag" data-background="./files/hd-wallpaper-g72e534791_1920.jpg" -->
## Configuration

<pre style="height: 23vh;" data-id="code-animation"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers="1-3|5-7|9-12|14-15|17-22|24-25">
# A '$' sign is your empty command prompt
# and _not_ part of the commands you are typing.
$

# Mandatory (for anything more than clone)
$ git config --global user.name "Vlad Dracula"
$ git config --global user.email "vlad@tran.sylvan.ia"

# Recommended
$ git config --global init.defaultBranch main
$ git config --global core.autocrlf input   # if on MacOS/Linux [1]
$ git config --global core.autocrlf true    # if on Windows [1]

# Optional
$ git config --global core.editor "code --wait"     # see [2] for options

# If necessary
$ git config --global http.proxy proxy-url  # set proxy
$ git config --global https.proxy proxy-url # set proxy

$ git config --global --unset http.proxy    # unset proxy
$ git config --global --unset https.proxy   # unset proxy

# List all set options
$ git config --list --show-origin
</code></pre>

<footer>
<span style="font-size: smaller;"><b>[1]</b> fixes line feeds, you don't have to fully understand this</span><br>
<span style="font-size: smaller;"><b>[2]</b> <a href="https://git-scm.com/book/en/v2/Appendix-C:-Git-Commands-Setup-and-Config#ch_core_editor">git-scm.com/book/en/v2/Appendix-C:-Git-Commands-Setup-and-Config#ch_core_editor</a></span>
</footer>

---

<!-- .slide: data-state="blue_overlay logo yellow_flag" data-background="./files/hd-wallpaper-g72e534791_1920.jpg" -->
## About VIM...
<div class="r-stack">
  <img class="fragment current-visible" src="https://preview.redd.it/m9eh2jw08qm61.jpg?width=583&format=pjpg&auto=webp&s=17994593b2b748b5087cc8ce786c7d161dd91747" height="300">
  <img class="fragment current-visible" src="https://preview.redd.it/af7fmnv08qm61.jpg?width=564&format=pjpg&auto=webp&s=6c1704acf6f02a8cc3b3f644216fe1fcb9645e7c" height="500">
  <img class="fragment fade-in" src="https://preview.redd.it/b5bt8nv08qm61.jpg?width=776&format=pjpg&auto=webp&s=0d592f97999f3f5d2cc4fd115fb5029831b53d2d" height="380">
</div>

<pre class="fragment" style="width: max-content;" data-id="code-animation"><code style="overflow: hidden;" data-trim class="bash">
[ESC] :wq [ENTER]  # Save and quit
[ESC] :q! [ENTER]  # Quit without saving
</code></pre>

---

<!-- .slide: data-state="blue_overlay logo yellow_flag" data-background="./files/hd-wallpaper-g72e534791_1920.jpg" -->
## Help!

<pre style="width: max-content;" data-id="code-animation"><code style="overflow: hidden;" style="padding: .5em 1em;" data-trim class="bash">
$ git help           # all git commands

$ git config -h      # short help on config
$ git config --help  # long help on config
</code></pre>

---

<!-- .slide: data-state="blue_overlay logo yellow_flag" data-background="./files/hd-wallpaper-g72e534791_1920.jpg" -->
## Setup: Key Points
Use git config with the **--global** option to configure a user name, email address, editor, and other preferences once per machine.

