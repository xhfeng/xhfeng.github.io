---
layout: default
---


<div class="well">
    {% for tag in site.tags %}
    	<h1><%=$.query.get("tag")%></h1>
    	<h1>{{ tag[0] }}<sup>{{ tag[1].size }}</sup></h1>
    	{% if tag[0] == <%=$.query.get("tag")%> %}
	        <ul>
	            <a href="{{site.baseurl}}/tags?tag={{tag[0] | cgi}}" title="{{ tag[0] }}">{{ tag[0] }}<sup>{{ tag[1].size }}</sup></a>

	            {% for post in tag[1] %}
	                <li><a href="{{ site.baseurl}}{{ post.url }}">{{ post.title }}</a></li>
	            {% endfor %}
	        </ul>
        {% endif %}
    {% endfor %}
</div>




