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

        $("#test_md").text(tnodes);
      }
      ,'jsonp'
  );
</script>

<div id="test_md" class="well"></div>


