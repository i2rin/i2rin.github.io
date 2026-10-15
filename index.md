---
title: Home
---

{% include profile.html %}

<section class="works-section">
  <h2>主な業績</h2>
  <ul>
    {% assign featured = site.data.works | where: "featured", true %}
    {% if featured.size == 0 %}
      <p>TODO: works.yml で featured: true を付けた業績がここに表示されます。</p>
    {% endif %}
    {% for work in featured %}
      {% include work-item.html work=work %}
    {% endfor %}
  </ul>
</section>
