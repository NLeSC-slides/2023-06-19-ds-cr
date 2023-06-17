<!--
title: Good Practices in Research Software Development
description: An Introduction
author: Ole Mussmann
version: 4.3.1
plugins: RevealMarkdown, RevealChalkboard, RevealHighlight, RevealMath.KaTeX, RevealMenu, RevealNotes, RevealSearch, RevealZoom
-->

<!-- .slide: data-state="blue_overlay yellow_flag yellow_strip purple_half_circle_bottom purple_blob right_e_top" data-background-video="./files/Mood video Homepage 2.mp4" data-background-video-loop data-background-video-muted="true" -->

# Good Practices for Research Software Development

---

<!-- .slide: data-state="standard" data-background="./files/workspace-1280538_1280.jpg"-->
<!-- Image by <a href="https://pixabay.com/users/freephotocc-2275370/?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=1280538">Free Photos</a> from <a href="https://pixabay.com//?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=1280538">Pixabay</a> -->

<style>

/* Blockquote main style */
.blockquote {
    position: relative;
    font-weight: 800;
    padding: 30px 0;
    width: 100%;
    max-width: 500px;
    z-index: 1;
    margin: 80px auto;
    align-self: center;
    border-top: solid 1px;
    border-bottom: solid 1px;
}

/* Blockquote header */
.blockquote h1 {
    position: relative;
    font-size: small;
    font-weight: 800;
    line-height: 1;
    margin: 0;
}

/* Blockquote right double quotes */
.blockquote:after {
    position: absolute;
    content: "”";
    font-size: 10rem;
    line-height: 0;
    bottom: -43px;
    right: 30px;
}

/* increase header size after 600px */
@media all and (min-width: 600px) {
    .blockquote h1 {
        font-size: 60px;
   }

}

/* Blockquote subheader */
.blockquote h4 {
    position: relative;
    font-size: 1.4rem;
    font-weight: normal;
    line-height: 1;
    margin: 0;
    padding-top: 20px;
    z-index: 1;
}

</style>


## Programming vs Software Engineering

<div class="blockquote-wrapper fragment">
  <div class="blockquote">
      Software engineering is programming integrated over time.
    <h4>&mdash;Titus Winters, Google C++ devlead</h4>
  </div>
</div>

Note:
What's the difference between programming and software engineering?

---

<!-- .slide: data-state="standard" data-background="./files/whitebg.png"  -->

<img width="800" alt="development speed" src="./files/development-speed.svg">

---

<!-- .slide: data-state="standard" data-background="./files/workspace-1280538_1280.jpg"-->

## Development Speed ⚡

<div style="float: left;">
<ul>
  <li>Blue curve
  <ul>
    <li>Writing code</li>
  </ul>
  <li>Red curve
  <ul>
    <li contenteditable="true">...</li>
    <li contenteditable="true">...</li>
    <li contenteditable="true">...</li>
    <li contenteditable="true">...</li>
    <li contenteditable="true">...</li>
    <li contenteditable="true">...</li>
  </ul>
</ul>
</div>

Note:
- deleted wrong function
- need to onboard collaborators
- a new feature broke stuff
- need to rewrite
- need to teach users
<br>
<br>
- GitHub
- Version control
- Modular coding
- Documentation
- Code reviews
- Testing

---

<!-- .slide: data-state="standard" data-background="./files/workspace-1280538_1280.jpg"-->

## Projects are Different

<img style="height: 30vh;" src="./files/branching.png"/>

---

<!-- .slide: data-state="standard" data-background="./files/workspace-1280538_1280.jpg"-->

## What to Use When?

<div style="width: 49%; float: left; font-size: smaller;">
  <table>
    <tr>
      <th>⏱️&nbsp;lifetime</th>
      <th>use</th>
    </tr>
    <tr>
      <td>1-shot</td>
      <td class="fragment" data-fragment-index="1">🚫</td>
    </tr>
    <tr>
      <td>week+</td>
      <td class="fragment" data-fragment-index="2">Git &amp; GitHub</td>
    </tr>
    <tr>
      <td>3 months+</td>
      <td class="fragment" data-fragment-index="3">Testing</td>
    </tr>
    <tr>
      <td>6 months+</td>
      <td class="fragment" data-fragment-index="4">Documentation,<br>automate testing</td>
    </tr>
  </table>
</div>

<div style="width: 49%; float: right; font-size: smaller;" class="fragment" data-fragment-index="5">
  <table>
    <tr>
      <th>🧑🧑&nbsp;users</th>
      <th>use</th>
    </tr>
    <tr>
      <td>1</td>
      <td class="fragment" data-fragment-index="6">Push to main</td>
    </tr>
    <tr>
      <td>2+</td>
      <td class="fragment" data-fragment-index="7">Branches, merging</td>
    </tr>
    <tr>
      <td>2+ (+students)</td>
      <td class="fragment" data-fragment-index="8">Code review</td>
    </tr>
    <tr>
      <td>2+ (+external)</td>
      <td class="fragment" data-fragment-index="9">release branch, <br>&amp; everything else</td>
    </tr>
  </table>
</div>

Note:
- Train these tools
- Experience their effect
- Use own judgement, but
- avoid "but in my project..."

---

<!-- .slide: data-state="standard" data-background="./files/workspace-1280538_1280.jpg"-->

## Good practices are investments

Profits come in

- Development efficiency
- Reproducibility
- Reusability
- Faster debugging
- Robustness, fewer errors
- Fewer headaches!