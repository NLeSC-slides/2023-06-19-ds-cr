<!-- .slide: id="ignoring_things" data-state="blue_overlay logo yellow_flag" data-background="./files/boy-g17e8683be_1920.jpg" -->
# Ignoring Things

- How can I tell Git to ignore files I don’t want to track?

---

<!-- .slide: data-state="blue_overlay logo yellow_flag" data-background="./files/boy-g17e8683be_1920.jpg" -->
## A New Beginning

<pre data-id="code-animation"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers>
$ cd ..          # exit the 'planets' directory
$ mkdir project  # create a new directory 'project'
$ cd project     # change into directory 'project'
$ git init       # create a new git repository
</code></pre>

---

<!-- .slide: data-state="blue_overlay logo yellow_flag" data-background="./files/boy-g17e8683be_1920.jpg" -->
## .gitignore 🙈

<pre data-id="code-animation"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers="1-2|4-17|19-22|24-32|34-38|40-46|48-58">
$ mkdir results
$ touch a.dat b.dat c.dat results/a.out results/b.out

$ git status
On branch main

No commits yet

Untracked files:
  (use "git add &lt;file&gt;..." to include in what will be committed)
	a.dat
	b.dat
	c.dat
	results/

nothing added to commit but untracked files present (use "git add"
to track)

$ code .gitignore
$ cat .gitignore
*.dat
results/  # Note the slash, this means it's a directory!

$ git status
On branch main
Untracked files:
  (use "git add &lt;file&gt;..." to include in what will be committed)

	.gitignore

nothing added to commit but untracked files present (use "git add"
to track)

$ git add .gitignore
$ git commit -m "Ignore data files and the results folder."
$ git status
On branch main
nothing to commit, working directory clean

$ git add a.dat
The following paths are ignored by one of your .gitignore files:
a.dat
hint: Use -f if you really want to add them.
hint: Turn this message off by running
hint: "git config advice.addIgnoredFile false"
# Thank you, Git! 🙏

$ git status --ignored
On branch main
Ignored files:
 (use "git add -f &lt;file&gt;..." to include in what will be committed)

        a.dat
        b.dat
        c.dat
        results/

nothing to commit, working directory clean
</code></pre>

---

<!-- .slide: data-state="blue_overlay logo yellow_flag" data-background="./files/boy-g17e8683be_1920.jpg" -->
## Quiz: Ignoring Nested Directories 

Imagine having the following directory structure:
<pre data-id="code-animation" style="width: max-content;"><code style="overflow: hidden;" data-trim class="bash">
&nbsp;results/data
&nbsp;results/plots 
</code></pre>

How can you ignore only one sub-directory?

<pre class="fragment" style="width: max-content;" data-id="code-animation"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers>
$ cat .gitignore 
results/plots/
</code></pre>

---

<!-- .slide: data-state="blue_overlay logo yellow_flag" data-background="./files/boy-g17e8683be_1920.jpg" -->
## .gitignore Syntax 

<pre data-id="code-animation"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers>
file.txt              # the file "file.txt"
directory/            # the directory "directory" and content
*.log                 # all files ending with ".log"
error_?.log           # "error_1.log", "error_A.log", ...
error_[a-z].log       # "error_a.log", "error_b.log", ...
!error_important.log  # do _not_ ignore "error_important.log"
**/secret             # _all_ "secret" folders and content, everywhere
/home/ole/**/secret   # as above, but only within /home/ole/
</code></pre>

---

<!-- .slide: data-state="blue_overlay logo yellow_flag" data-background="./files/boy-g17e8683be_1920.jpg" -->
## Quiz: Perfecting Ignoring 1/2

<ul>
  <li>How to ignore all <b>.dat</b> files, except <b>final.dat</b>?
<pre class="fragment" data-id="code-animation"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers>
*.dat           # ignore all data files
!final.dat      # except final.data
</code></pre>
  </li>

  <li class="fragment">How to ignore everything in <b>results/</b>, except <b>results/data</b>?
<pre class="fragment" data-id="code-animation"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers>
results/*               # ignore everything in results folder
!results/data/          # do not ignore results/data/ contents
</code></pre>
  </li>
</ul>

---

<!-- .slide: data-state="blue_overlay logo yellow_flag" data-background="./files/boy-g17e8683be_1920.jpg" -->
## Quiz: Perfecting Ignoring 2/2

<ul>
  <li class="fragment">What's the shortest <b>.gitignore</b> to exclude all <b>.dat</b> files in <b>result/data/position/gps</b>? Do not ignore the <b>info.txt</b>.
<pre data-id="code-animation"><code style="overflow: hidden;" data-trim class="bash">
results/data/position/gps/a.dat
results/data/position/gps/b.dat
results/data/position/gps/info.txt
results/plots
</code></pre>

<pre class="fragment" data-id="code-animation"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers>
results/data/position/gps/*.dat
</code></pre>
  </li>
  <li class="fragment">You have many scattered <b>.dat</b> files. How can you ignore all of them?
<pre data-id="code-animation"><code style="overflow: hidden;" data-trim class="bash">
results/a.dat
data/experiment_1/a.dat
data/experiment_2/b.dat
data/experiment_2/variation_1/d.dat
# [and many more...]
</code></pre>

<pre class="fragment" data-id="code-animation"><code style="overflow: hidden;" data-trim class="bash" data-line-numbers>
**/*.dat
</code></pre>
  </li>
</ul>

---

<!-- .slide: data-state="blue_overlay logo yellow_flag" data-background="./files/boy-g17e8683be_1920.jpg" -->
## Contradictions

What does the following **.gitignore** file achieve?
<pre data-id="code-animation" style="width: max-content;"><code style="overflow: hidden;" data-trim class="bash">
&nbsp;*.dat
&nbsp;!*.dat 
</code></pre>

<span class="fragment">Nothing. Lines always overrule previous lines.</span>

---

<!-- .slide: data-state="blue_overlay logo yellow_flag" data-background="./files/boy-g17e8683be_1920.jpg" -->
## Hands-On

<div style="font-size: smaller;">
You generated many log files of the form <b>log_01</b>, <b>log_02</b>, ... You want to keep them, but not track them with Git.<br>
<ol>
  <li>Write <b>one .gitignore</b> to exclude them.</li>
  <li>Test your "ignore pattern" by creating dummy files of the form <b>log_01</b>, <b>log_02</b>, ...
<pre class="fragment" data-id="code-animation" style="width: max-content;"><code style="overflow: hidden;" data-trim class="bash">
&nbsp;log_* 
</code></pre>
  </li>
  <li class="fragment">You find that <b>log_01</b> is very important after all! Add it to the tracked files without changing your <b>.gitignore</b><br>
<pre class="fragment" data-id="code-animation" style="width: max-content;"><code style="overflow: hidden;" data-trim class="bash">
$ git add -f log_01 
</code></pre>
  </li>
  <li class="fragment">Discuss with your neighbor what other types of files could reside in your directory that you do not want to track and thus would exclude via <b>.gitignore</b></li>
</ol>
</div>

---

<!-- .slide: data-state="blue_overlay logo yellow_flag" data-background="./files/boy-g17e8683be_1920.jpg" -->
## Tracking Changes: Key Points

- The **.gitignore** file tells Git which files and folders _not_ to track
