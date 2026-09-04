---
layout: default
title: Home
---

<h1>GPGPU Microarchitecture Peformance Enhancement</h1>

<p class="lede">Instruction-issue mechanisms for throughput processors — warp
scheduling, scoreboard stall reduction, and lightweight out-of-order execution
for workloads that GPUs were never really built for.</p>

I am a research scholar in Computer Science and Engineering at
[IIT Bombay](https://www.cse.iitb.ac.in/), in Prof. Virendra Singh's CCCP lab.
My research interests lie in GPGPU Architecture and Performance, Microarchitecture Performance and OS-Microarch Interactioins. I am primarily conducting research in the area GPU microarchitecture enhancements to accelerate non traditional, scientific and AI GPGPU workloads. The research involves designing novel out of order scheduling techniques and front end pipeline redesign to extract Instruction Level Parallelism from applications with limited data level parallelism.

I have a Master's of Science Degree from North Carolina State University, Raleigh. Most of my courses and projects were focused on Microarchitecture, Operating Systems and Parallel computing.

After graduating, I started working as a Core OS developer at Intel Corporation in Oregon. I worked on OS optimization of Windows operating systems across Intel architecture. My work required writing kernel drivers to implement various power saving features for Windows OS.


## News

<ul class="news">
  <li><time>Sep 2026</time><span><strong>BB8</strong> accepted at <strong>ASP-DAC '27</strong> — breaking head-of-line stalling in GPGPUs via Instruction Bypassing.</span></li>
  <li><time>Aug 2026</time><span><strong>PRISM</strong> accepted at <strong>ICCD 2026</strong> — priority-ranked instruction scheduling mechanism for GPU scoreboard stalls.</span></li>
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
  <p class="pub-meta">IEEE International Conference on Computer Design (ICCD 2026), Hong Kong</p>
</div>

<div class="pub">
  <p class="pub-title">HOOP: Hint-based Out-of-Order Processing for GPGPUs via Per-Kernel Dependency Analysis<span class="tag accepted">Accepted</span></p>
  <p class="pub-authors"><span class="me">M. Kotyad</span>, A.Agrawal, V. Singh</p>
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
