---
layout: default
---


<script type="text/javascript">
	$.get(
       "http://lp.taobao.com/go/rgn/citydistrictdata.php"
      ,{}
      ,function(data,status,xhr){
        //console.log(data);
        tnodes = data.nodes;
        shtml = "<ul>";
        //for (var i = tnodes.length - 1; i >= 0; i--) {
        for (var i = 0; i < tnodes.length; i++) {
        	shtml += "<li>" + tnodes[i].id + "</li>";
        }
        shtml += "</ul>";

        $("#test_md").html(shtml);
      }
      ,'jsonp'
  );
</script>


<div id="test_md" class="well"></div>

### 1. 流程图绘制

```flow
st=>start: 开始
op=>operation: 作业
cond=>condition: 是/否?
e=>结束

st->op->cond
cond(是)->e
cond(否)->op
```

### 2. 表格绘制

| 名称 | 熟悉程度 | 名称 | 熟悉程度 |
| --: | :--: | --: | :--: |
| java | ★★★☆☆ | python | ★★★★☆ |
| C | ★★★☆☆ | javascript | ★★★★☆ |
| Linux | ★★★★☆ | Photoshop | ★★☆☆☆ |
