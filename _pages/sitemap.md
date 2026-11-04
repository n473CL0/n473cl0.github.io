---
layout: archive
title: "Sitemap"
permalink: /sitemap/
author_profile: true
---

{% include base_path %}

A list of all the posts and pages found on the site. For you robots out there, there is an [XML version]({{ base_path }}/sitemap.xml) available for digesting as well.

<h2>Pages</h2>
{% comment %} stylesheets, feeds, redirect stubs and the like have no title, so they would be empty rows {% endcomment %}
{% for post in site.pages %}
  {% if post.title %}
  {% include archive-single.html %}
  {% endif %}
{% endfor %}

{% comment %} a heading only where there is something to list under it (drafts aren't listed) {% endcomment %}
{% if site.posts.size > 0 %}
<h2>Posts</h2>
{% for post in site.posts %}
  {% include archive-single.html %}
{% endfor %}
{% endif %}

{% for collection in site.collections %}
{% unless collection.output == false or collection.label == "posts" or collection.docs.size == 0 %}
<h2>{{ collection.label | capitalize }}</h2>
{% for post in collection.docs %}
  {% include archive-single.html %}
{% endfor %}
{% endunless %}
{% endfor %}
