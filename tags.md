---
title: 分类标签
layout: default
---
<section class="content">
    <article id="index">
        <h2>所有分类标签：</h2>
        <div id="tag_cloud">
            {% for tag in site.tags %}<a href="javascript:;" onclick="showTag('{{ tag[0] }}')" title="{{ tag[0] }}" rel="{{ tag[1].size }}">{{ tag[0] }}</a>{% endfor %}
        </div>
        <div id="show-tag"><div style="text-align:center"><img src="/images/loading.gif"/>&nbsp;&nbsp;loading...</div></div>    
        <div id="post-bottom">
            <p style="text-align:right" class="more">
                <a href="{{site.baseurl}}">返回主页</a>
            </p>
        </div>
    </article>
</section>

<script type="text/javascript">
var dataStr = '{ {% for tag in site.tags %}{% if tag[0] != site.tags.first[0] %},{% endif %}"{{ tag[0] }}":[{% for post in tag[1] %}{% if post != tag[1].first %},{% endif %}{"url":"{{post.url}}", "title":"{{post.title}}", "date":"{{post.date | date:"%d/%m/%Y"}}"}{% endfor %}]{% endfor %} }',
    data = JSON.parse(dataStr),
    curTag = $.query.get("tag"),
    archieves = data[curTag];
</script>