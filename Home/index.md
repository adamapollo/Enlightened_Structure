---
layout: default
---

Enlightened Structure
=====================

Lorem ipsum in cat a calis sum. Lorem ipsum in cat a calis sum. Lorem ipsum in cat a calis sum.
Lorem ipsum in cat a calis sum. Lorem ipsum in cat a calis sum. Lorem ipsum in cat a calis sum.
Lorem ipsum in cat a calis sum. Lorem ipsum in cat a calis sum. Lorem ipsum in cat a calis sum.

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

