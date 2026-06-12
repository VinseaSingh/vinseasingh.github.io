---
layout: default
permalink: /news/
title: news
nav: true
nav_order: 4
---

<div class="post">

  <header class="post-header">
    <h1 class="post-title">{{ page.title }}</h1>
    <p class="post-description">All announcements and updates</p>
  </header>

  <article>
    <div class="news">
      {% if site.news != blank -%}
        {% assign news = site.news | reverse %}
        <div class="table-responsive">
          <table class="table table-sm table-borderless">
          {% for item in news %}
            <tr>
              <th scope="row" style="width: 20%">{{ item.date | date: "%b %d, %Y" }}</th>
              <td>
                {% if item.inline -%}
                  {{ item.content | markdownify }}
                {%- else -%}
                  <a class="news-title" href="{{ item.url | relative_url }}">{{ item.title }}</a>
                {%- endif %}
              </td>
            </tr>
          {% endfor %}
          </table>
        </div>
      {%- else -%}
        <p>No news items found.</p>
      {%- endif %}
    </div>
  </article>

</div>
