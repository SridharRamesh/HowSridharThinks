---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
---

You've come to the right place to see how Sridhar thinks about math.

<h1> All Posts, Unorganized</h1>

([Atom feed](/feed/math.xml))

{% comment %}
The below is taken from the `home` minima layout, but I've modified it, mostly just so that it displays "pages" rather than "posts". I'd rather not have to put dates in everything's filename, and I think of these as non-ephemeral objects anyway. But having them display with their date taken from their header is nice.
{% endcomment %}

<div class="home">
  {%- if page.title -%}
    <h1 class="page-heading">{{ page.title }}</h1>
  {%- endif -%}

  {%- assign posts = site.math -%}

  {%- if posts.size > 0 -%}
    <ul class="post-list">
      {%- for post in posts -%}
      <li>
        {%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
        <span class="post-meta">{{ post.date | date: date_format }}</span>
        <h3>
          <a class="post-link" href="{{ post.url | relative_url }}">
            {{ post.title | escape }}
          </a>
        </h3>
        {%- if site.show_excerpts -%}
          {{ post.excerpt }}
        {%- endif -%}
      </li>
      {%- endfor -%}
    </ul>

  {%- endif -%}

</div>