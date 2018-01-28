---
layout: default
---


<div class="well">
    {% for tag in site.tags %}
        <ul>
            <a href="{{site.baseurl}}/tags?tag={{tag[0] | cgi}}" title="{{ tag[0] }}">{{ tag[0] }}<sup>{{ tag[1].size }}</sup>&nbsp;</a>
            {% for otag in tag %}
                <li><small>{{ otag }}</small></li>
            {% endfor %}
        </ul>
    {% endfor %}
</div>

