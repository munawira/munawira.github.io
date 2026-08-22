---
layout: default
title: Home
---

<h1>Making GPUs stall less.</h1>

<p class="lede">I design instruction-issue mechanisms for throughput processors — warp
scheduling, scoreboard stall reduction, and lightweight out-of-order execution
for workloads that GPUs were never really built for.</p>

I am a PhD candidate in Computer Science and Engineering at
[IIT Bombay](https://www.cse.iitb.ac.in/), in Prof. Virendra Singh's CCCP lab.
My work sits at the front end of the GPU pipeline: the point where a warp has an
instruction ready, a functional unit is free, and the machine issues nothing
anyway. Across the benchmark suites I study, roughly 40% of issue cycles are lost
to that class of stall. Recovering even part of it is cheaper than adding SMs.

Before the PhD I spent two and a half years at Intel in Oregon, working on
processor power management at the OS–hardware boundary. I also teach computer
architecture and operating systems at Pillai University, Navi Mumbai, where I set
up the department's research lab.

## News

<ul class="news">
  <li><time>Aug 2026</time><span><strong>PRISM</strong> accepted at <strong>ICCD 2026</strong> — priority-ranked instruction scheduling for GPU scoreboard stalls.</span></li>
  <li><time>Aug 2026</time><span><strong>HOOP</strong> accepted at <strong>SBAC-PAD 2026</strong>, Madrid — hint-driven out-of-order issue without per-SM scoreboard logic.</span></li>
  <li><time>May 2026</time><span><strong>Best Paper Award</strong> at ACM Computing Frontiers 2026 in Catania for FlIP.</span></li>
</ul>

## Selected work

<div class="pub">
  <p class="pub-title"><a href="https://doi.org/10.1145/3801487.3801823">FlIP: Flow-based Instruction Processing for Out-of-Order Scheduling in GPGPUs</a><span class="tag award">Best Paper</span></p>
  <p class="pub-authors"><span class="me">M. Kotyad</span>, Y. Rathore, G. S. Shanmukhi, V. Singh</p>
  <p class="pub-meta">ACM Computing Frontiers (CF '26) · <a href="https://doi.org/10.1145/3801487.3801823">10.1145/3801487.3801823</a></p>
</div>

<div class="pub">
  <p class="pub-title">PRISM: Priority Ranked Instruction Scheduling Mechanism<span class="tag accepted">Accepted</span></p>
  <p class="pub-authors"><span class="me">M. Kotyad</span>, V. Singh</p>
  <p class="pub-meta">IEEE International Conference on Computer Design (ICCD 2026)</p>
</div>

<div class="pub">
  <p class="pub-title">HOOP: Hint-based Out-of-Order Processing for GPGPUs<span class="tag accepted">Accepted</span></p>
  <p class="pub-authors"><span class="me">M. Kotyad</span>, V. Singh</p>
  <p class="pub-meta">IEEE/SBC Symposium on Computer Architecture and High Performance Computing (SBAC-PAD 2026), Madrid</p>
</div>

<p style="margin-top:22px"><a href="{{ '/publications/' | relative_url }}">All publications →</a></p>

## Writing

<ul class="postlist">
  {%- for post in site.posts limit: 3 %}
  <li>
    <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
    <time>{{ post.date | date: "%d %b %Y" }}</time>
    {%- if post.excerpt_text %}<p>{{ post.excerpt_text }}</p>{% endif %}
  </li>
  {%- endfor %}
</ul>

<p style="margin-top:22px"><a href="{{ '/writing/' | relative_url }}">All writing →</a></p>
