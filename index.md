---
title: Home
---

{% include profile.html %}

<section class="activity-section">
  <h2>最新の活動</h2>
  <ul>
    {% assign empty_array = "" | split: "," %}
    {% assign news_items = site.data.news | default: empty_array %}
    {% assign work_items = site.data.works | default: empty_array %}
    {% assign activities = work_items | concat: news_items | sort: "date" | reverse %}
    {% assign latest = activities | slice: 0, 5 %}
    {% if latest.size == 0 %}
      <p>TODO: works.yml や news.yml にデータを追加すると、新しい順にここに表示されます。</p>
    {% endif %}
    {% for activity in latest %}
      {% include activity-item.html activity=activity %}
    {% endfor %}
  </ul>
</section>
