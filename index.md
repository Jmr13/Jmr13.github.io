---
layout: home
title:  "Home"
date:   2026-01-01
---

<section>
  <h1>Latest posts</h1>
</section>
<main>
  {% for post in site.posts %}
    <article class="post">
      <header>
        <h2><a href="{{ post.url }}"><u>{{ post.title }}</u>&emsp; | &emsp;{{ page.date | date: "%m - %d - %Y" }}</a></h2>
      </header>
    </article>
  {% endfor %}
</main>