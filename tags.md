---
layout: default
---


<div class="well">
    {% for tag in site.tags %}
        <ul>
            <a href="{{site.baseurl}}/tags?tag={{tag[0] | cgi}}" title="{{ tag[0] }}">{{ tag[0] }}<sup>{{ tag[1].size }}</sup>&nbsp;</a>

            {% for post in tag[1] %}
                <li><a href="{{ site.baseurl}}{{ post.url }}">{{ post.title }}</a></li>
            {% endfor %}
        </ul>
    {% endfor %}
</div>

<script type="text/javascript">
	var curTag = $.query.get("tag");
</script>


