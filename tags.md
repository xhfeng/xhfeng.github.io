---
layout: default
---

{%for post in site.posts %}
    {% unless post.next %}
        <h1>{{ post.date | date: '%Y年' }}</h1>
        <ul>
    {% else %}
        {% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
        {% capture nyear %}{{ post.next.date | date: '%Y' }}{% endcapture %}
        {% if year != nyear %}
            </ul>
            <h1>{{ post.date | date: '%Y' }}</h1>
            <ul>
        {% endif %}
    {% endunless %}
    <li>{{ post.date | date: "%m月%d日" }} - <a href="{{ site.baseurl}}{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}
</ul>



