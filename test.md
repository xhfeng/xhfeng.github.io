---
layout: default
---


<script type="text/javascript">
	$.get(
       "http://lp.taobao.com/go/rgn/citydistrictdata.php"
      ,{}
      ,function(data,status,xhr){
        console.log(data);
        tnodes = data.nodes;
        shtml = "<ul>";
        for (var i = tnodes.length - 1; i >= 0; i--) {
        	shtml += "<li>" + tnodes[i].id + "</li>";
        }
        shtml += "</ul>";

        $("#test_md").html(shtml);
      }
      ,'jsonp'
  );
</script>

<div id="test_md" class="well"></div>


