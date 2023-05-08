<!-- .slide: data-state="logo yellow_flag black_overlay 6" data-background="./files/man-2264825_1920.jpg" id="exercise"-->
<!-- https://pixabay.com/photos/man-woman-push-ups-wellness-2264825/ -->

# Exercise

---

<!-- .slide: data-state="logo yellow_flag black_overlay 6" data-background="./files/man-2264825_1920.jpg" -->
<!-- https://pixabay.com/photos/man-woman-push-ups-wellness-2264825/ -->

### Nano, Command Line Editor 🤏

<img style="height: 30vh;" src="./files/nano.png"/>

- CTRL+O, ENTER to write to file
- CTRL+X to exit

---

<!-- .slide: data-state="logo yellow_flag black_overlay 6" data-background="./files/man-2264825_1920.jpg" -->
<!-- https://pixabay.com/photos/man-woman-push-ups-wellness-2264825/ -->

### Zero to git: Local 👈


<div style="font-size: x-large;">

**Play with git on mybinder 🏑**

- <a href="https://mybinder.org/v2/gh/OleMussmann/git/HEAD"><img style="padding: 0; margin:0;" src="https://mybinder.org/badge_logo.svg"/></a> and wait for it to start
- Click on "Terminal"
- Configure git to your liking, set at least `user.name` and `user.email`
  - And set `pull.rebase false`
- Create a folder **git** and change into it: &nbsp; `mkdir git; cd git`
- Initialize a repo with trunk (main branch) _main_
- Create a file **README.md** and fill it with some markdown, this is in your WORKSPACE
- Add the file to your INDEX
- Commit the file to your LOCAL REPOSITORY
  - Name the commit "Initial Commit"

</div>

---

<!-- .slide: data-state="logo yellow_flag black_overlay 6" data-background="./files/man-2264825_1920.jpg" -->
<!-- https://pixabay.com/photos/man-woman-push-ups-wellness-2264825/ -->

### Zero to git: Remote 🖩


<div style="font-size: x-large;">

**Connect with the World 🌍**

- Create an _empty_ repository on GitHub or GitLab
- Create SSH keys in your binder environment
  - Feel free to omit the password _for this exercise only_
- Upload the SSH keys to GitHub or GitLab
- Test the SSH connection
- Add the new UPSTREAM REPOSITORY as remote named _origin_ to your local repo
- Push the main branch to the UPSTREAM REPOSITORY _origin_
- Check in the browser if the **README.md** arrived

Congratulations! 🎉 You have mastered the basics of git.
</div>

---

<!-- .slide: data-state="logo yellow_flag black_overlay 6" data-background="./files/man-2264825_1920.jpg" -->
<!-- https://pixabay.com/photos/man-woman-push-ups-wellness-2264825/ -->

### Everyday git: Back and Forth ↔️

<div style="font-size: x-large;">

**Understanding the 5 Realms 🏰**

- ⚠️ After each of the following steps, check the status of the repo: &nbsp; `git status`
  - Create a few files
    - **committed.txt &nbsp; staged.txt &nbsp; edited.txt &nbsp; new.txt**
  - Add and commit **committed.txt** and **edited.txt**
  - Add (but not commit!) **staged.txt**
  - Remove **staged.txt** from WORKSPACE and INDEX
  - Create a file **.gitignore** and use it to exclude the file **new.txt**
  - Add and commit **.gitignore** and all the other files and push your LOCAL REPOSITORY to the REMOTE REPOSITORY
- Check in the browser the state of your REMOTE REPOSITORY
- Delete all **\*.txt** files, add the changes, and commit your changes to _main_
- Push your changes to the REMOTE REPOSITORY
- Check the status with &nbsp; `git status`
- Create a file **from_remote.txt** on github.com, commit directly to _main_
- Pull the latest changes from the REMOTE REPOSITORY
- Inspect the local files with  &nbsp; `ls -a`
- Check the status with &nbsp; `git status`

</div>

---

<!-- .slide: data-state="logo yellow_flag black_overlay 6" data-background="./files/man-2264825_1920.jpg" -->
<!-- https://pixabay.com/photos/man-woman-push-ups-wellness-2264825/ -->

### Everyday git: Branching Out 🎋

<div style="font-size: x-large;">

**Multi-dimensional ✨**

- Create and switch to a development branch called _development_
- Create, add to INDEX and commit a file **dev_stuff.txt**, name the commit "add dev stuff"
- Realize you were not done yet, create a file **more_dev_stuff.txt**
  - Add it to INDEX and commit it _to the same commit_ as **dev_stuff.txt** (make amends)
  - Name the commit "add dev stuff" as well
- Confirm that you have only one commit with `git log`
- "Accidentally" delete **dev_stuff.txt**
  - Don't worry, it's still saved in the LOCAL REPOSITORY! Restore it back to your WORKSPACE
- Create and add to INDEX a file **passwords.txt**
  - Realize it should not end up in the repo, and un-stage it from INDEX
  - Add it to the **.gitignore** file, just to be safe
  - Add all your changes and commit them
- Switch back to branch _main_
- Merge the branch _development_ into _main_
- If successful, tag the latest commit with an annotated tag "v1.0"
- Push the new branch and the tag to your REMOTE REPOSITORY _origin_

Yesss! 🥳 You are getting good at this.
</div>

---

<!-- .slide: data-state="logo yellow_flag black_overlay 6" data-background="./files/man-2264825_1920.jpg" -->
<!-- https://pixabay.com/photos/man-woman-push-ups-wellness-2264825/ -->

### Advanced git: Stashing Things 📦

<div style="font-size: x-large;">

**Temporarily Cleaning Up 🧽**

- Create a **file.txt**, and fill it with the line "I'm in the REPO"
- Add it to INDEX and commit to your LOCAL REPOSITORY
- Edit the content of **file.txt** to "And now I'm in INDEX"
- Add the file to INDEX
- Edit the file again and change the content to "Or in WORKSPACE?"
  - The file has now three different contents in three different places 😮
- Apply the `git diff` commands that show the differences of **file.txt** in
  - WORKSPACE ↔ INDEX
  - WORKSPACE ↔ LOCAL REPO
  - INDEX ↔ LOCAL REPO
- See what files you have now: &nbsp; `ls -a`
- Check the state of your local repo: &nbsp; `git status`
- Stash the mess you just created, including the untracked (not staged in INDEX) files
- See again what files you have now: &nbsp; `ls -a`
- Check again the state of your local repo: &nbsp; `git status`
- Re-apply the stash, _including the INDEX_
- Confirm that you have everything back, WORKSPACE, INDEX

</div>

---

<!-- .slide: data-state="logo yellow_flag black_overlay 6" data-background="./files/man-2264825_1920.jpg" -->
<!-- https://pixabay.com/photos/man-woman-push-ups-wellness-2264825/ -->

### Advanced git: Gaining Insight 👓

<div style="font-size: x-large;">

**Take a breather and study what you did 😌**

- Study what you have done in the repo so far: &nbsp; `git log`
- See what's inside the tag "v1.0": &nbsp; `git show v1.0`
- Find out (and blame) who made a mess with **file.txt**: `git blame file.txt`
  - Change, add and commit file.txt a few more times and do it again
  - Also check with `git log file.txt`
- See the last change of **file.txt**: &nbsp; `git show file.txt`

Take a break (if you haven't yet), get a coffee ☕ and prepare for the finale
</div>

---

<!-- .slide: data-state="logo yellow_flag black_overlay 6" data-background="./files/man-2264825_1920.jpg" -->
<!-- https://pixabay.com/photos/man-woman-push-ups-wellness-2264825/ -->

### git Enlightenment: Conflict Resolution 🕊️

<div style="font-size: x-large;">

**The Final Frontier 🚀**

- Switch to the _main_ branch, if you didn't already
- Add, commit and push all changes, start with a clean LOCAL REPOSITORY
- Create, add and commit a file **poem.txt**, containing my bad poem
- Push the LOCAL REPOSITORY to your REMOTE REPOSITORY _origin_
- Fix the poem in the browser in your REMOTE REPOSITORY, commit to _main_
- Fix the poem _differently_ in your LOCAL REPOSITORY, add and commit to _main_
- Pull the remote changes
- Resolve the merge conflict
  - The mergetool "vimdiff" uses CTRL-W to switch between panes, this collides with the browser shortcut to close windows; resolve the conflict "by hand" instead

Amazing! You made it. 🏅 You probably fought with JupyterLab, wrestled git, fixed unexpected errors, and still pulled through. You are ready to use git effectively in your own projects.

Keep learning and enjoy the journey.
</div>
