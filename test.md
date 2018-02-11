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

### 4. 制作一份待办事宜

- [ ] 支持以 PDF 格式导出文稿
- [ ] 改进 Cmd 渲染算法，使用局部渲染技术提高渲染效率
- [x] 新增 Todo 列表功能
- [x] 修复 LaTex 公式渲染问题
- [x] 新增 LaTex 公式编号功能