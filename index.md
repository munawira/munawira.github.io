---
layout: default
title: Home
---

<h1>GPGPU Microarchitecture Peformance Enhancement</h1>

<p class="lede">Energy efficient Instruction scheduling mechanisms for GPUs.</p>

I am an Associate Professor at Pillai University and Pillai HOC College of Engineering and Technology under Mahatma Education Society. 
I am a final year research scholar in Computer Science and Engineering at [IIT Bombay](https://www.cse.iitb.ac.in/), in Prof. Virendra Singh's Computer Architecture and Dependable Systems Lab (CADSL). 
My research interests lie in GPGPU Architecture and Performance, Microarchitecture Performance and OS-Microarch Interactioins. I am primarily conducting research in the area of GPU microarchitecture enhancements to accelerate non traditional, scientific and AI GPGPU workloads. The research involves designing novel out of order scheduling techniques and front end pipeline redesign to extract Instruction Level Parallelism from applications with limited data level parallelism.



## News

<ul class="news">
  <li><time>Sep 2026</time><span><strong>BB8</strong> accepted at <strong>ASP-DAC '27</strong> — breaking head-of-line stalling in GPGPUs via Instruction Bypassing.</span></li>
  <li><time>Aug 2026</time><span><strong>PRISM</strong> accepted at <strong>ICCD 2026</strong> — priority-ranked instruction scheduling mechanism for GPU scoreboard stalls.</span></li>
  <li><time>Aug 2026</time><span><strong>HOOP</strong> accepted at <strong>SBAC-PAD 2026</strong>, Madrid — hint-driven out-of-order issue without per-SM scoreboard logic.</span></li>
  <li><time>May 2026</time><span><strong>Best Paper Award</strong> at ACM Computing Frontiers 2026 in Catania for FlIP.</span></li>
</ul>


<h1>Publications</h1>

<!-- <p class="lede">Published and A</p> -->

## 2027
<div class="pub">
  <p class="pub-title">BB8:
Blocking Buffer for breaking head-of-line stalling in GPGPUs via
Instruction Bypassing.<span class="tag accepted">Accepted</span></p>
    <p class="pub-authors"><span class="me">Munawira Kotyad</span>, Ganesh Sai Shanmukhi, Yashvardhan Rathore, Virendra Singh</p>
  <p class="pub-meta"> 32nd Asia and South Pacific Design Automation
Conference (ASP-DAC), Tokyo, Japan, January 2027</p>
</div>
## 2026

<div class="pub">
  <p class="pub-title">PRISM: Priority Ranked Instruction Scheduling Mechanism<span class="tag accepted">Accepted</span></p>
  <p class="pub-authors"><span class="me">Munawira Kotyad</span>, Virendra Singh</p>
  <p class="pub-meta"> 44th IEEE International Conference on Computer Design (ICCD 2026), Hong Kong, November 2026</p>
</div>

<div class="pub">
  <p class="pub-title">HOOP: Hint-based Out-of-Order Processing for GPGPUs via Per-Kernel Dependency Analysis<span class="tag accepted">Accepted</span></p>
  <p class="pub-authors"><span class="me">Munawira Kotyad</span>, Ayush Agrawal,Virendra Singh</p>
  <p class="pub-meta">38th IEEE/SBC International Symposium on Computer Architecture and High Performance Computing (SBAC-PAD 2026), Madrid, October 2026</p>
</div>

<div class="pub">
  <p class="pub-title"><a href="https://doi.org/10.1145/3801487.3801823">FlIP: Flow-based Instruction Processing for Out-of-Order Scheduling in GPGPUs</a><span class="tag award">Best Paper</span></p>
  <p class="pub-authors"><span class="me">Munawira Kotyad</span>, Yashvardhan Rathore, Ganesh Sai Shanmukhi, Virendra Singh</p>
  <p class="pub-meta">ACM International Conference on Computing Frontiers (CF '26), Catania, Italy · <a href="https://doi.org/10.1145/3801487.3801823">10.1145/3801487.3801823</a></p>
</div>

<div class="pub">
  <p class="pub-title">Bypassing Blocking Instructions to Enable Out-of-Order Execution in GPGPUs</p>
  <p class="pub-authors"><span class="me">Munawira Kotyad</span>, Ganesh Sai Shanmukhi, Yashvardhan Rathore, Virendra Singh</p>
  <p class="pub-meta">Poster · ACM International Conference on Computing Frontiers (CF '26)</p>
</div>



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
