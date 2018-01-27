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
        var jq = jQuery.noConflict();
        jq(document).ready(function(){             

            jq('.posts a').each(function(index,element){
                var href = jq(this).attr('href');
                if(href.indexOf('#') == 0){
                }else if ( href.indexOf('/') == 0 || href.toLowerCase().indexOf('art.yanping.me')>-1 ){
                }else{
                    jq(this).attr('target','_blank');
                    jq(this).addClass('external');
                }
            });
           
        }); 

</script>

<script type="text/javascript">
  function showTag(tagStr) {
    jq.getJSON("../post.json",
    function(data) {
      $('#show-tag').empty(content);
      var content = "<h2>分类：" + tagStr + "</h2><ul class=\"posts\">";
      var count = 0;
      jq.each(data,
      function(i, item) {
        jq.each(item.tags,
        function(j, tag) {
          if (tag == tagStr) {
            content += "<li class=\"listing-item\"><time datetime=\"" + item.date + "\">" + item.date + "</time><a href=\"" + item.url + "\">" + item.title + "</a></li>";
            count++;
          }

        });
      });
      if (count > 0) {
        content += "</ul>";
        postNumStr = "<span>（" + count + "篇文章）</span>";
        $('#show-tag').append(content);
        $('#show-tag>h2').append(postNumStr);
      }
    });
  }
</script>

