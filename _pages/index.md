---
layout: page
title: Home
id: home
permalink: /
---

# 개발하는 브로콜리의 디지털 정원 🥦

<p style="padding: 3em 1em; background: #f5f7ff; border-radius: 4px;">
  현재 진행중인 <span style="font-weight: bold">[[프로젝트]]</span>의 기획서입니다!
</p>

개발 외에도 이것 저것 다 해보는 개발자입니다. [깃허브 바로가기](https://github.com/MEKBANSUKOZINGER)

<strong>최근에 쓴 문서들</strong>

<ul>
  {% assign recent_notes = site.notes | sort: "last_modified_at_timestamp" | reverse %}
  {% for note in recent_notes limit: 5 %}
    <li>
      {{ note.last_modified_at | date: "%Y-%m-%d" }} — <a class="internal-link" href="{{ site.baseurl }}{{ note.url }}">{{ note.title }}</a>
    </li>
  {% endfor %}
</ul>

<style>
  .wrapper {
    max-width: 46em;
  }
</style>
