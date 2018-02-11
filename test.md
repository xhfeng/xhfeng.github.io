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

    $.ajax({
        type: "GET",
        url: "http://xhfeng.freeddns.org:8000",
        //crossDomain: true,
        data: {},
        dataType: "text",
        success: function(data){
            $('#resText').empty();   //清空resText里面的所有内容
            $('#resText').html(data);
        },
       error: function (xhr, status, errMsg) {
            console.log(xhr, status, errMsg);
       }
    });

</script>

### 1. 这是阿里的数据

<div id="test_md" class="well"></div>

### 2. 这是我的猫

<div id="resText" class="well"></div>

### 3. 表格绘制

| 名称 | 熟悉程度 | 名称 | 熟悉程度 |
| --: | :--: | --: | :--: |
| java | ★★★☆☆ | python | ★★★★☆ |
| C | ★★★☆☆ | javascript | ★★★★☆ |
| Linux | ★★★★☆ | Photoshop | ★★☆☆☆ |

### 4. 这是待办事宜

- [ ] 吃堞
- [ ] 睡觉
- [x] 打豆豆
- [x] 发呆
- [x] 新增功能