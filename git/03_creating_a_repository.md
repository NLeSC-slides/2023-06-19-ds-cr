<!-- .slide: id="creating_a_repository" data-state="purple_overlay logo yellow_flag" data-background="./files/adan-creation-g5381c6989_1920.jpg" -->
<!-- Image by <a href="https://pixabay.com/users/anassar-421921/?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=436007">Andres Nassar</a> from <a href="https://pixabay.com//?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=436007">Pixabay</a> -->
# Creating a Repository
Where does Git store information?

---

<!-- .slide: data-state="purple_overlay logo yellow_flag" data-background="./files/adan-creation-g5381c6989_1920.jpg" -->
## The Mission

<blockquote>
"Wolfman <span style="font-style: normal;">🐺</span> and Dracula <span style="font-style: normal;">🧛</span> investigate sending a planetary lander to Mars."
</blockquote>

<img style="height: 25vh;" src=https://swcarpentry.github.io/git-novice/fig/motivatingexample.png>

<p style="font-size: small;">
<a href="https://www.deviantart.com/b-maze/art/Werewolf-vs-Dracula-124893530">Werewolf vs dracula</a>
by <a href="https://www.deviantart.com/b-maze">b-maze</a> / <a href="https://www.deviantart.com/">Deviant Art</a>.
<a href="https://en.wikipedia.org/wiki/File:OSIRIS_Mars_true_color.jpg">Mars</a> by European Space Agency /
<a href="https://creativecommons.org/licenses/by/3.0/deed.en">CC-BY-SA 3.0 IGO</a>.
<a href="https://commons.wikimedia.org/wiki/File:PIA19873-Pluto-NewHorizons-FlyingPastImage-20150714-transparent.png">Pluto</a> /
Courtesy NASA/JPL-Caltech.
<a href="https://commons.wikimedia.org/wiki/File:Mummy_icon_-_Noun_Project_4070.svg">Mummy</a>
© Gilad Fried / <a href="https://thenounproject.com/">The Noun Project</a> /
<a href="https://creativecommons.org/licenses/by/3.0/deed.en">CC BY 3.0</a>.
<a href="https://commons.wikimedia.org/wiki/File:Lune_ico.png">Moon</a>
© Luc Viatour / <a href="https://lucnix.be/">https://lucnix.be</a> /
<a href="https://creativecommons.org/licenses/by-sa/3.0/deed.en">CC BY-SA 3.0</a>.</p>

---

<!-- .slide: data-state="purple_overlay logo yellow_flag" data-background="./files/adan-creation-g5381c6989_1920.jpg" -->
## Create a Working Directory

<pre data-id="code-animation"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers="1-4|6-7|9-10">
# cd     change directory
# ~      short for "home" directory
# /      directory separator in Linux
$ cd ~/Desktop 

# mkdir  make directory
$ mkdir planets

# cd     change directory
$ cd planets
</code></pre>

---

<!-- .slide: data-state="purple_overlay logo yellow_flag" data-background="./files/adan-creation-g5381c6989_1920.jpg" -->
## Hello ~~World~~ Git

<pre data-id="code-animation"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers="1|3-4|6-10">
$ git init  # create empty git repository

$ ls        # list directory contents
# Nothing happens?!

$ ls -a     # list _all_ directory content, including hidden
.  ..  .git
# .     is the current directory
# ..    is the parent directory
# .git  is a new folder named '.git'
</code></pre>

---

<!-- .slide: data-state="purple_overlay logo yellow_flag" data-background="./files/adan-creation-g5381c6989_1920.jpg" -->
## Branches

<pre data-id="code-animation"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers="1-2|4-9">
$ git checkout -b main  # 'checkout -b' create branch
Switched to a new branch 'main'

$ git status
On branch main

No commits yet

nothing to commit (create/copy files and use "git add" to track)
</code></pre>

<footer>
N.B.: git checkout -b [branch] ➡️ git switch [branch]<br>
see <a href="https://www.infoq.com/news/2019/08/git-2-23-switch-restore/">infoq.com/news/2019/08/git-2-23-switch-restore</a>
</footer>

---

<!-- .slide: data-state="purple_overlay logo yellow_flag" data-background="./files/adan-creation-g5381c6989_1920.jpg" -->
## Quiz!

<blockquote style="text-align: left;">
<span style="font-style: normal;">🧛</span> How about landing on moons instead?
</blockquote>
<blockquote style="text-align: right;">
Well, I'm not sure if we should... <span style="font-style: normal;">🐺</span>
</blockquote>
<div class="fragment">
... but Dracula already types
<pre data-id="code-animation"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers="1-4|5-9">
$ cd ~/Desktop   # return to Desktop directory
$ cd planets     # go to planets directory (still a Git repository)
$ ls -a          # ensure the .git subdirectory is still there
.  ..  .git
$ mkdir moons    # make a subdirectory planets/moons
$ cd moons       # go into moons subdirectory
$ git init       # make the moons subdirectory a Git repository
$ ls -a          # confirm that we have created a new Git repository
.  ..  .git
</code></pre>
</div>

<p class="fragment">Is it necessary to create a repository in the moon directory to track files?</p>

---

<!-- .slide: data-state="purple_overlay logo yellow_flag" data-background="./files/adan-creation-g5381c6989_1920.jpg" -->
## Un-init?

<blockquote style="text-align: right;">
Look, nested repositories are not necessary. They might even interfere with each other. <span style="font-style: normal;">🐺</span>
</blockquote>
<blockquote style="text-align: left;">
<span style="font-style: normal;">🧛</span> Oh, sorry. How can I remove it again?
</blockquote>

<div class="fragment">
Wolfman takes over:
<pre data-id="code-animation"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers="1-2|4-7">
$ pwd  # print working directory
/home/vlad/Desktop/moons
&nbsp; 
&#35; rm   # remove file or directory
&#35; -r   # recursive (necessary for directories)
&#35; -f   # force (.git resists accidental removal)
$ rm -rf .git
</code></pre>
</div>

<footer>
<b>rm -rf</b>&nbsp; is destructive, make sure you are in the correct directory
</footer>

---

<!-- .slide: data-state="purple_overlay logo yellow_flag" data-background="./files/adan-creation-g5381c6989_1920.jpg" -->
## Repository: Key Points

- **git init** initializes a repository
- Git stores all of its repository data in the **.git** directory
