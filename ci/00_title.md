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

<!-- .slide: data-state="blue_overlay yellow_flag yellow_strip purple_half_circle_bottom purple_blob right_e_top" data-background-video="./files/Mood video Homepage 2.mp4" data-background-video-loop data-background-video-muted="true" data-auto-animate data-auto-animate-id="title" -->

# Continuous Integration
<img src="./files/automate.jpg">

[Ole Mussmann](mailto:o.mussmann@esciencecenter.nl)


===

<!-- .slide: data-state="standard" -->

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

## Continuous _What_ Now...?

<div class="blockquote-wrapper fragment">
  <div class="blockquote">
      Automating the integration of code changes from multiple contributors into a single software project.
    <h4>&mdash; <a href="atlassian.com/continuous-delivery/continuous-integration">Atlassian</a></h4>
  </div>
</div>

---

<!-- .slide: data-state="standard" -->
## Slide 3
- same column
