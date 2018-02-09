---
layout: default
---
<script type="text/javascript">
	var curTag = $.query.get("tag");
    var str = "";
    {% for tag in site.tags %}
        str += '<ul>';
        {% if tag[0] == 'esp' %}
            
            {% for post in tag[1] %}
                str +=  '<li><a href="{{ site.baseurl}}{{ post.url }}">{{ post.title }}</a></li>';
            {% endfor %}

        {% endif %}
        str += '</ul>';
    {% endfor %}
    

    $("#tags_html").html(str);
</script>


<div id="tags_html" class="well"></div>

<!-- 
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

 -->


