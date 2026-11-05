---
title: Home
---

{% include profile.html %}

<section class="activity-section">
  <h2>最新の活動</h2>
  <ul>
    {% assign empty_array = "" | split: "," %}
    {% assign news_items = site.data.news | default: empty_array %}
    {% assign latest_news = news_items | sort: "date" | reverse | slice: 0, 3 %}
    {% if latest_news.size == 0 %}
      <p>TODO: news.yml にデータを追加すると、新しい順にここに表示されます。</p>
    {% endif %}
    {% for item in latest_news %}
      {% include news-item.html news=item %}
    {% endfor %}
  </ul>
  <p class="activity-section__more">
    <a class="button" href="{{ '/news/' | relative_url }}">More Info</a>
  </p>
</section>
