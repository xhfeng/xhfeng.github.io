---
layout: default
---


<script type="text/javascript">
  function get_tb_reg() {
    $.get(
         "http://lp.taobao.com/go/rgn/citydistrictdata.php"
        ,{}
        ,function(data,status,xhr){
          //console.log(data);
          tnodes = data.nodes;
          shtml = "<ul>";
          for (var i = 0; i < tnodes.length; i++) {
            shtml += "<li>" + tnodes[i].id + "</li>";
          }
          shtml += "</ul>";

          $("#resTbreg").html(shtml);
        }
        ,'jsonp'
      );
    }

  get_tb_reg();
</script>


### 2. 这是阿里的数据

<div id="resTbreg" class="well"></div>



### 3. 这是表格

| 名称 | 熟悉程度 | 名称 | 熟悉程度 |
| ------: | :------: | ------: | :------: |
| java | ★★★☆☆ | python | ★★★★☆ |
| C | ★★★☆☆ | javascript | ★★★★☆ |
| Linux | ★★★★☆ | Photoshop | ★★☆☆☆ |

### 4. 这是待办事宜

- [ ] 吃饭
- [ ] 睡觉
- [x] 打豆豆
- [x] 发呆
- [x] 新增功能