---
layout: default
---

<div>
  <h1>Enlightened Structure: Free Culture Seeds</h1>

  <p>Enlightened Structure is a set of Free Culture idea seeds &#8211; global
  infrastructure software projects for social good. All of the content on this site is
  reusable and remixable under a Creative Commons license.</p>

  <div class="hr-ellipsis">&nbsp;</div>

  {% for post in site.posts %}
    <div class="excerpt">
      <h3><a href="{{ post.url }}">{{ post.title }}</a></h3>
      <p>
        {{ post.excerpt }}
      </p>
    </div>
  {% endfor %}
</div>
