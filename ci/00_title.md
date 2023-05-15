<!--
title: Continuous Integration
description: Automate All The things!
author: Ole Mussmann
version: 4.3.1
plugins: RevealMarkdown, RevealChalkboard, RevealHighlight, RevealMath.KaTeX, RevealMenu, RevealNotes, RevealSearch, RevealZoom
-->

<!-- .slide: data-state="blue_overlay yellow_flag yellow_strip purple_half_circle_bottom purple_blob right_e_top" data-background-video="./files/steampunk-85358.mp4" data-background-video-loop data-background-video-muted="true" data-auto-animate data-auto-animate-id="title" -->

# Continuous Integration

[Ole Mussmann](mailto:o.mussmann@esciencecenter.nl)

---

<!-- .slide: data-state="blue_overlay yellow_flag yellow_strip purple_half_circle_bottom purple_blob right_e_top" data-background-video="./files/steampunk-85358.mp4" data-background-video-loop data-background-video-muted="true" data-auto-animate data-auto-animate-id="title" -->

# Continuous Integration
<img src="./files/automate.jpg">

[Ole Mussmann](mailto:o.mussmann@esciencecenter.nl)


===

<!-- .slide: data-state="blue_overlay yellow_flag logo" data-background="./files/reload-97640.svg" data-background-size="50%" data-auto-animate data-auto-animate-id="what" -->


# Continuous _What_ Now...?

---

<!-- .slide: data-state="blue_overlay 9 yellow_flag logo" data-background="./files/reload-97640.svg" data-background-size="50%" data-auto-animate data-auto-animate-id="what" -->

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

# Continuous _What_ Now...?

<div class="blockquote">
  Automating the integration of code changes from multiple contributors into a single software project.
<h4>&mdash; <a href="atlassian.com/continuous-delivery/continuous-integration">Atlassian</a></h4>
</div>

---

<!-- .slide: data-state="blue_overlay yellow_flag logo 9" data-background="./files/reload-97640.svg" data-background-size="50%" -->

## What Is It Good For?
- Linting
- Automated testing
- Security analyses
- Send messages
  - Slack, Discord, Matrix, Mastodon, email, ...
- Building & compiling
  - Code, Documentation, ...
- Deploying (PyPi, Kubernetes, GitHub Pages)
  - Just like these slides

---

<!-- .slide: data-state="blue_overlay yellow_flag logo 9" data-background="./files/reload-97640.svg" data-background-size="50%" -->

## Hands-On

<div style="float: left; width: 60%; margin-bottom: 1em;">
  <ol>
    <li>Create a new repo</li>
    <li>Clone, add code, commit, push</li>
    <li>Enable automatic testing</li>
    <li>Verify that tests ran</li>
    <li>Add a test that fails</li>
    <li>Open an issue</li>
    <li>Fork ⚠️ and clone colleague's repo</li>
    <li>Fix the broken test</li>
    <li>Open a pull request with auto-close</li>
    <li>Accept colleagues's pull request</li>
  </ol>
</div>
<img style="float: right; width: 39%;" src="./files/full-cycle-ci.png">

<a href="https://coderefinery.github.io/testing/full-cycle-ci/">coderefinery.github.io/testing/full-cycle-ci/</a>

---

<!-- .slide: data-state="blue_overlay yellow_flag logo 9" data-background="./files/reload-97640.svg" data-background-size="50%" -->

## Take-away

- Best practices are a time-investment _with returns_
- CI saves time and keeps your project clean
- What improvements could your project benefit from?
- What's nice to know, but overkill for your current work?
