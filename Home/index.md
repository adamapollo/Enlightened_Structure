---
layout: default
---

Enlightened Structure
=====================

Enlightened Structure is a set of Free Culture idea seeds
for global infrastructure software projects for social good.
All of the content on this site is reusable and remixable under a Creative Commons license.

Free Culture Seeds
------------------

<dl>
  {% for post in site.posts %}
    <dt>
      <span>{{ post.date | date_to_string }}</span>
      &raquo;
      <a href="{{ post.url }}">{{ post.title }}</a>
    </dt>
    <dd>
      <em>
        {{ post.excerpt }}
      </em>
    </dd>
  {% endfor %}
</dl>

