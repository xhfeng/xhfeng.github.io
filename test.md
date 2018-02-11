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

    $.get(
       "http://xhfeng.freeddns.org:8000"
      ,{}
      ,function(data,status,xhr){

        $("#get_home").text(data);
      }
      ,'text'
  );

</script>

### 1. 这是阿里的数据

<div id="test_md" class="well"></div>

### 2. 这是我的猫

<div id="get_home" class="well"></div>

### 3. 表格绘制

| 名称 | 熟悉程度 | 名称 | 熟悉程度 |
| --: | :--: | --: | :--: |
| java | ★★★☆☆ | python | ★★★★☆ |
| C | ★★★☆☆ | javascript | ★★★★☆ |
| Linux | ★★★★☆ | Photoshop | ★★☆☆☆ |

### 4. 这是一份待办事宜

- [ ] 吃堞
- [ ] 睡觉
- [x] 打豆豆
- [x] 发呆
- [x] 新增功能