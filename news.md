---
title: News
---

# News

{% assign empty_array = "" | split: "," %}
{% assign news_items = site.data.news | default: empty_array %}
{% assign sorted_news = news_items | sort: "date" | reverse %}

{% if sorted_news.size == 0 %}
<p>TODO: `_data/news.yml` にデータを追加すると、ここに年ごとに一覧表示されます。</p>
{% endif %}

{% assign current_year = "" %}
{% for item in sorted_news %}
  {% assign year = item.date | slice: 0, 4 %}
  {% if year != current_year %}
    {% unless forloop.first %}
  </ul>
</section>
    {% endunless %}
<section class="works-section" id="y{{ year }}">
  <h2>{{ year }}</h2>
  <ul>
    {% assign current_year = year %}
  {% endif %}
  {% include news-item.html news=item %}
{% endfor %}
{% unless sorted_news.size == 0 %}
  </ul>
</section>
{% endunless %}
