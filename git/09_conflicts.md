<!-- .slide: id="conflicts" data-state="standard 7" data-background="./files/seagull-ga3abb7684_1920.jpg" -->
<!-- Image by <a href="https://pixabay.com/users/smuldur-5589717/?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=4034308">Şinasi Müldür</a> from <a href="https://pixabay.com//?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=4034308">Pixabay</a> -->
# Conflicts

- What do I do when my changes conflict with someone else’s?

---

<!-- .slide: data-state="standard 7" data-background="./files/seagull-ga3abb7684_1920.jpg" -->
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

<!-- .slide: data-state="standard 7" data-background="./files/seagull-ga3abb7684_1920.jpg" data-auto-animate -->
## Making of a Conflict

<pre data-id="code-animation"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers="1-12|14-16|18-23|25-32">
$ git pull
$ cat mars.txt
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity

$ code mars.txt
cat mars.txt
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity
This line is new

$ git add .
$ git commit -m "add line"
$ git push

$ code mars.txt
cat mars.txt
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity
This line is edited locally my Wolfman

[Edit the same file with the GitHub Web IDE]

Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity
This line is edited on remote by Dracula

[Only for this hands-on: commit to 'main' branch]

$ cat mars.txt
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity
&lt;&lt;&lt;&lt;&lt;&lt;&lt; HEAD
This line is edited locally by Wolfman
||||||| c500f36
This line is new
=======
This line is edited on remote by Dracula
&gt;&gt;&gt;&gt;&gt;&gt;&gt; e7c6d3cb58004414f4800c26d82b629259a9b6b4
</code></pre>

---

<!-- .slide: data-state="standard 7" data-background="./files/seagull-ga3abb7684_1920.jpg" data-auto-animate -->
## Making of a Conflict

<pre data-id="code-animation"><code style="overflow: hidden;" data-trim class="tap" data-line-numbers="34-50">
$ git pull
$ cat mars.txt
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity

$ code mars.txt
cat mars.txt
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity
This line is new

$ git add .
$ git commit -m "add line"
$ git push

$ code mars.txt
cat mars.txt
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity
This line is edited locally my Wolfman

[Edit the same file with the GitHub Web IDE]

Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity
This line is edited on remote by Dracula

[Only for this hands-on: commit to 'main' branch]

$ cat mars.txt
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity
&lt;&lt;&lt;&lt;&lt;&lt;&lt; HEAD
This line is edited locally by Wolfman
||||||| c500f36
This line is new
=======
This line is edited on remote by Dracula
&gt;&gt;&gt;&gt;&gt;&gt;&gt; e7c6d3cb58004414
</code></pre>

---

<!-- .slide: data-state="standard 7" data-background="./files/seagull-ga3abb7684_1920.jpg" data-auto-animate -->
## Making of a Conflict

<pre data-id="code-animation"><code style="overflow: hidden;" data-trim class="tap" data-line-numbers="34-50">
$ git pull
$ cat mars.txt
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity

$ code mars.txt
cat mars.txt
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity
This line is new

$ git add .
$ git commit -m "add line"
$ git push

$ code mars.txt
cat mars.txt
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity
This line is edited locally my Wolfman

[Edit the same file with the GitHub Web IDE]

Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity
This line is edited on remote by Dracula

[Only for this hands-on: commit to 'main' branch]

$ cat mars.txt
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity
&lt;&lt;&lt;&lt;&lt;&lt;&lt; HEAD              # << local separator, local commit ID
This line is edited locally by Wolfman
||||||| c500f36
This line is new
=======
This line is edited on remote by Dracula
&gt;&gt;&gt;&gt;&gt;&gt;&gt; e7c6d3cb58004414
</code></pre>

---

<!-- .slide: data-state="standard 7" data-background="./files/seagull-ga3abb7684_1920.jpg" data-auto-animate -->
## Making of a Conflict

<pre data-id="code-animation"><code style="overflow: hidden;" data-trim class="tap" data-line-numbers="34-50">
$ git pull
$ cat mars.txt
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity

$ code mars.txt
cat mars.txt
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity
This line is new

$ git add .
$ git commit -m "add line"
$ git push

$ code mars.txt
cat mars.txt
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity
This line is edited locally my Wolfman

[Edit the same file with the GitHub Web IDE]

Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity
This line is edited on remote by Dracula

[Only for this hands-on: commit to 'main' branch]

$ cat mars.txt
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity
&lt;&lt;&lt;&lt;&lt;&lt;&lt; HEAD              # << local separator, local commit ID
This line is edited locally by Wolfman
||||||| c500f36           # || base separator, base commit ID
This line is new
=======
This line is edited on remote by Dracula
&gt;&gt;&gt;&gt;&gt;&gt;&gt; e7c6d3cb58004414
</code></pre>

---

<!-- .slide: data-state="standard 7" data-background="./files/seagull-ga3abb7684_1920.jpg" data-auto-animate -->
## Making of a Conflict

<pre data-id="code-animation"><code style="overflow: hidden;" data-trim class="tap" data-line-numbers="34-50">
$ git pull
$ cat mars.txt
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity

$ code mars.txt
cat mars.txt
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity
This line is new

$ git add .
$ git commit -m "add line"
$ git push

$ code mars.txt
cat mars.txt
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity
This line is edited locally my Wolfman

[Edit the same file with the GitHub Web IDE]

Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity
This line is edited on remote by Dracula

[Only for this hands-on: commit to 'main' branch]

$ cat mars.txt
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity
&lt;&lt;&lt;&lt;&lt;&lt;&lt; HEAD              # << local separator, local commit ID
This line is edited locally by Wolfman
||||||| c500f36           # || base separator, base commit ID
This line is new
=======                   # == remote separator
This line is edited on remote by Dracula
&gt;&gt;&gt;&gt;&gt;&gt;&gt; e7c6d3cb58004414
</code></pre>

---

<!-- .slide: data-state="standard 7" data-background="./files/seagull-ga3abb7684_1920.jpg" data-auto-animate -->
## Making of a Conflict

<pre data-id="code-animation"><code style="overflow: hidden;" data-trim class="tap" data-line-numbers="34-50">
$ git pull
$ cat mars.txt
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity

$ code mars.txt
cat mars.txt
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity
This line is new

$ git add .
$ git commit -m "add line"
$ git push

$ code mars.txt
cat mars.txt
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity
This line is edited locally my Wolfman

[Edit the same file with the GitHub Web IDE]

Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity
This line is edited on remote by Dracula

[Only for this hands-on: commit to 'main' branch]

$ cat mars.txt
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity
&lt;&lt;&lt;&lt;&lt;&lt;&lt; HEAD              # << local separator, local commit ID
This line is edited locally by Wolfman
||||||| c500f36           # || base separator, base commit ID
This line is new
=======                   # == remote separator
This line is edited on remote by Dracula
&gt;&gt;&gt;&gt;&gt;&gt;&gt; e7c6d3cb58004414  # >> end separator, remote commit ID
</code></pre>

---

<!-- .slide: data-state="standard 7" data-background="./files/seagull-ga3abb7684_1920.jpg" -->

## Which Reality?

<img src="https://swcarpentry.github.io/git-novice/fig/conflict.svg">

---

<!-- .slide: data-state="standard 7" data-background="./files/seagull-ga3abb7684_1920.jpg" -->
## Resolving a Conflict

<pre data-id="code-animation"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers>
$ code mars.txt
$ cat mars.txt
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity
Choose which lines to keep  # new ⬇️
Remove separators
You don’t even have to keep any of the suggested lines :-o
</code></pre>

---

<!-- .slide: data-state="standard 7" data-background="./files/seagull-ga3abb7684_1920.jpg" -->
## Binary files

<blockquote data-fragment-index="1" style="text-align: left;">
<span style="font-style: normal;">🧛</span> That is actually pretty straightforward. But how would that work for binary files like images?
</blockquote>
<blockquote class="fragment" data-fragment-index="2" style="text-align: right;">
Uhm. I do not know. Let's try it out. <span style="font-style: normal;">🐺</span>
</blockquote>

---

<!-- .slide: data-state="standard 7" data-background="./files/seagull-ga3abb7684_1920.jpg" -->
## Exercise!

<ol style="font-size: smaller;">
  <li>Download your two favorite images of Mars</li>
  <li>Name one mars.jpg and upload it on GitHub</li>
  <li>Name the other one also mars.jpg, move it into your <b>planets</b> folder</li>
  <li>Add and commit the image</li>
  <li><b>git pull</b> and read the error message<br>
<pre class="fragment" data-fragment-index="1" style="width: max-content;" data-id="code-animation"><code style="overflow: hidden;" data-trim class="bash">
&nbsp;warning: Cannot merge binary files: mars.jpg (HEAD vs. 012) 
&nbsp;# Oh no! What now?!
</code></pre>
</li>
  <li class="fragment" data-fragment-index="2">Checkout the <b>HEAD</b> version of mars.jpg</li>
  <li class="fragment" data-fragment-index="2">Rename the file
<pre data-id="code-animation" style="width: max-content;"><code style="overflow: hidden;" data-trim class="bash">
&nbsp;$ mv mars.jpg mars_1.jpg 
</code></pre>
  </li>
  <li class="fragment" data-fragment-index="2">Checkout the <b>012</b> version of mars.jpg</li>
  <li class="fragment" data-fragment-index="2">Rename that file with a different name</li>
  <li class="fragment" data-fragment-index="2">Add both files and commit</li>
<ol>

---

<!-- .slide: data-state="standard 7" data-background="./files/seagull-ga3abb7684_1920.jpg" -->
## A Typical Work Session

- Put the actions in the correct order
- What commands are necessary to achieve them?

<table style="font-size: smaller; width: 100%; margin-top: 1em;">
 <tr>
   <th></th>
   <th>action</th>
   <th>command</th>
 </tr>
 <tr>
   <td>1</td>
   <td contenteditable="true">Make changes to a file</td>
   <td style="color: blue;" contenteditable="true"></td>
 </tr>
 <tr>
   <td>2</td>
   <td contenteditable="true">Update remote to match local repo</td>
   <td style="color: blue;">echo 100 >> numbers.txt</td>
 </tr>
 <tr>
   <td>3</td>
   <td contenteditable="true">Update local to match remote repo</td>
   <td style="color: blue;" contenteditable="true"></td>
 </tr>
 <tr>
   <td>4</td>
   <td contenteditable="true">Stage changes to be committed</td>
   <td style="color: blue;" contenteditable="true"></td>
 </tr>
 <tr>
   <td>5</td>
   <td contenteditable="true">Commit changes to local repo</td>
   <td style="color: blue;" contenteditable="true"></td>
 </tr>
 <tr>
   <td>6</td>
   <td><b style="color: blue;">Celebrate!</b></td>
   <td><b style="color: blue;">AFK</b></td>
 </tr>
</table>

---

<!-- .slide: data-state="standard 7" data-background="./files/seagull-ga3abb7684_1920.jpg" -->
## Remotes: Key Points

- Conflicts occur when two or more people change the same lines of the same file.
- Git does not allow people to overwrite each other’s changes blindly, but highlights conflicts so that they can be resolved.

