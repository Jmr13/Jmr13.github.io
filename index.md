---
layout: page
title:  "Home"
---

<section>
  <h1>Latest posts</h1>
</section>
<main>
  {% for post in site.posts %}
    <article>
      <header>
        <h2><a href="{{ post.url }}">{{ post.title }} | {{ post.date | date: "%m-%d-%Y" }}</a></h2>
      </header>
    </article>
  {% endfor %}
</main>