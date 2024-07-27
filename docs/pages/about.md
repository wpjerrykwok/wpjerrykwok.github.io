---
layout: page
title: About
permalink: /about/
weight: 3
---

# **About Me**

Hi I am **{{ site.author.name }}** :wave:

<div class="row">
{% include about/skills.html title="Technical Skills" source=site.data.technical-skills %}
{% include about/skills.html title="Soft Skills" source=site.data.soft-skills %}
{% include about/skills.html title="Other Skills" source=site.data.other-skills %}
</div>

<div class="row">
{% include about/timeline.html %}
</div>