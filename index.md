---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
---

You've come to the right place to see how Sridhar thinks about math.

Keep in mind, nothing here is polished, it's full of TODOs, you shouldn't be reading this site, who told you it even exists?

<h1> All Posts, Unorganized</h1>

([Atom feed](/feed/math.xml))

{%- assign mathposts = site.math | reverse -%}
{%- include collectionIndex.html collection=mathposts -%}