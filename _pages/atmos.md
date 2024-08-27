---
layout: archive
title: "Atmospheric Sciences Projects"
permalink: /atmo-projects/
author_profile: true
---

{% include base_path %}

<p style="text-align:justify">
I am a Ph.D. candidate in the Department of Atmospheric Sciences at Texas A\&M University, where I work under the guidance of Dr. Robert Korty. My research encompasses the development and application of high-resolution climate models to study the impact of climate change on tropical cyclones. I have focused on several key areas, including the rapid intensification of tropical cyclones in various paleo-climates, and the analysis of large-scale environmental conditions that influence tropical cyclone formation. My work employs a combination of deep learning techniques, numerical simulations, and data analysis to enhance our understanding of atmospheric processes and improve the accuracy of climate models.
</p>

{% for post in site.atmo reversed %}
  {% include archive-single.html %}
{% endfor %}
