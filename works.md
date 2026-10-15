---
title: Works
---

# Works

{% assign categories = "journal,preprint,intl_conf,domestic_conf,other,invited,thesis,grant,award" | split: "," %}

{% for category in categories %}
  {% assign items = site.data.works | where: "category", category | sort: "date" | reverse %}
  {% if items.size > 0 %}
  <section class="works-section" id="{{ category }}">
    <h2>
      {% case category %}
        {% when "journal" %}学術論文
        {% when "preprint" %}プレプリント
        {% when "intl_conf" %}国際会議
        {% when "domestic_conf" %}国内学会
        {% when "other" %}その他の発表
        {% when "invited" %}招待講演
        {% when "thesis" %}学位論文
        {% when "grant" %}研究費
        {% when "award" %}受賞
      {% endcase %}
    </h2>
    <ul>
      {% for work in items %}
        {% include work-item.html work=work %}
      {% endfor %}
    </ul>
  </section>
  {% endif %}
{% endfor %}
