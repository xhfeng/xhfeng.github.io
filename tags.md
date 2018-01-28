---
layout: default
---
<script type="text/javascript">
	//var curTag = $.query.get("tag");

	var dataStr = '{ {% for tag in site.tags %}{% if tag[0] != site.tags.first[0] %},{% endif %}"{{ tag[0] }}":[{% for post in tag[1] %}{% if post != tag[1].first %},{% endif %}{"url":"{{post.url}}", "title":"{{post.title}}", "date":"{{post.date | date:"%d/%m/%Y"}}"}{% endfor %}]{% endfor %} }',
    data = JSON.parse(dataStr),
    curTag = $.query.get("tag"),
    archieves = data[curTag];

    var str="<ul>";
    for (var i = archieves.length - 1; i >= 0; i--) {
    	archieves[i]
    	str += '<li><a href="{{ site.baseurl}}' + archieves[i].url + '">' + archieves[i].url + '</a></li>';

    	//date，url，title
    }
    $("#tags_html").html(str+"</ul>");
</script>


<div id="tags_html" class="well"></div>

<!-- 
<div class="well">
    {% for tag in site.tags %}
    	<h1><%=curTag%></h1>
    	<h1>{{ tag[0] }}<sup>{{ tag[1].size }}</sup></h1>
    	{% if tag[0] == <%=curTag%> %}
	        <ul>
	            <a href="{{site.baseurl}}/tags?tag={{tag[0] | cgi}}" title="{{ tag[0] }}">{{ tag[0] }}<sup>{{ tag[1].size }}</sup></a>

	            {% for post in tag[1] %}
	                <li><a href="{{ site.baseurl}}{{ post.url }}">{{ post.title }}</a></li>
	            {% endfor %}
	        </ul>
        {% endif %}
    {% endfor %}
</div>
 -->



