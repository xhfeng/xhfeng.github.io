---
layout: default
---


<script type="text/javascript">
  function get_tbreg() {
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
  var murl = "http://xhfeng.freeddns.org:8000";
  var mone = true;

  function get_data() {
    $.ajax({
        type: "GET",
        url: murl,
        //crossDomain: true,
        data: {},
        dataType: "text",
        success: function(data){
            $('#resText').empty();
            $('#resText').html(data);
        },
       error: function (xhr, status, errMsg) {
            console.log("xhr:", xhr);
            console.log("status:", status);
            console.log("errMsg:", errMsg);
            if (mone) {
              mone = false;
              murl = "http://192.168.1.20:8000";
              get_data();
            }
       }
    });
  }
  get_data();
  get_tbreg();
</script>

### 1. 这是我盒子里的数据

<div id="resText" class="well"></div>

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