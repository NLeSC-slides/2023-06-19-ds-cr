<!--
title: Testing
description: Getting more professional
author: Ole Mussmann
version: 4.3.1
plugins: RevealMarkdown, RevealChalkboard, RevealHighlight, RevealMath.KaTeX, RevealMenu, RevealNotes, RevealSearch, RevealZoom
-->

<!-- .slide: data-state="blue_overlay yellow_flag yellow_strip purple_half_circle_bottom purple_blob right_e_top" data-background-video="./files/606762245.mp4" data-background-video-loop data-background-video-muted="true" -->
<!-- https://pixabay.com/videos/engine-motor-mechanic-technology-5497/ -->

# Testing

[Ole Mussmann](mailto:o.mussmann@esciencecenter.nl)

===

<!-- .slide: data-state="standard" data-background="./files/lab-gbbd4af2a9_1280.jpg" -->

## Why Test?

<ul>
  <li>Preserve functionality
  <ul>
    <li>Detect new errors early</li>
    <li>Facilitate reproducability for research software</li>
  </ul></li>
  <li class="fragment">Help users
  <ul>
    <li>Verify correct installation</li>
    <li>Improve correctness for research output</li>
  </ul></li>
  <li class="fragment">Enable developers
  <ul>
    <li>Make refactoring easier</li>
    <li>Simplify external contributions</li>
  </ul></li>
</ul>

<h3 style="margin-top: 1em;" class="fragment">🧮 Manage Complexity 🧩</h3>

---

<!-- .slide: data-state="standard" data-background="./files/lab-gbbd4af2a9_1280.jpg" -->

## Why Not Test?

<div class="r-stack">
  <img style="height: 30vh;" src="./files/dev_speed_time_2.svg">
  <img class="fragment" style="height: 30vh;" src="./files/dev_speed_time_1.svg">
</div>

---

<!-- .slide: data-state="standard" data-background="./files/lab-gbbd4af2a9_1280.jpg" -->

## Test Types

<ul>
  <li>Unit test
  <ul class="fragment fade-up" data-fragment-index="1">
    <li>Smallest possible unit</li>
    <li>No dependency on outside code...</li>
    <li>(... replace them with mocks, stubs, etc.)</li>
  </ul></li>
</ul>
<ul class="fragment fade-up" data-fragment-index="2">
  <li>Integration test
  <ul class="fragment fade-up" data-fragment-index="3">
    <li>Test unit interaction</li>
    <li>Can be on small scales, or system wide</li>
  </ul></li>
</ul>

<div class="fragment fade-up" data-fragment-index="4" style='position:relative; padding: 0 0 calc(55.00% + 44px) 0; margin: -9em auto 0 auto;'><iframe src='https://gfycat.com/ifr/BriefUniformHornet' frameborder='0' scrolling='no' width='100%' height='100%' style='position:absolute;top:0;left:0;' allowfullscreen></iframe></div><p style="font-size: large; margin: 0; padding: 0;"> <a href="https://gfycat.com/briefuniformhornet">via Gfycat</a></p>

---

<!-- .slide: data-state="standard" data-background="./files/lab-gbbd4af2a9_1280.jpg" -->

## Analyze Test Covorage

[codecov.io](https://about.codecov.io/)

<!-- Image by <a href="https://pixabay.com/users/hellbergstina-13347982/?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=5396788">hellbergstina</a> from <a href="https://pixabay.com//?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=5396788">Pixabay</a> -->

<img class="fragment" style="height: 20vh;" src="./files/scale-ga51297104_640.png">
