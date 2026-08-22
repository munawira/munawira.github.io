---
layout: default
title: Writing
permalink: /writing/
description: Notes and articles on GPU microarchitecture, warp scheduling, and simulation methodology.
---

<h1>Writing</h1>

<p class="lede">Notes on GPU microarchitecture — things I wanted explained plainly
when I started, and things I keep re-deriving.</p>

<ul class="postlist">
  {%- for post in site.posts %}
  <li>
    <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
    <time>{{ post.date | date: "%d %b %Y" }}{% if post.tags.size > 0 %} · {{ post.tags | join: " / " }}{% endif %}</time>
    {%- if post.excerpt_text %}<p>{{ post.excerpt_text }}</p>{% endif %}
  </li>
  {%- else %}
  <li><p>Nothing published yet.</p></li>
  {%- endfor %}
</ul>
