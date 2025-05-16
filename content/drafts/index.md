---
# This is the index for the _drafts folder

layout: default
title: Drafts
---

You've come to the right place to see how Sridhar thinks about drafts.

<h1> All Drafts, Unorganized, Unfinished</h1>

{%- assign draftposts = site.drafts | reverse -%}
{%- include collectionIndex.html collection=draftposts -%}