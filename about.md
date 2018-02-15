---
layout: default
---

<script type="text/javascript">

	var murl = "http://xhfeng.freeddns.org:8000";
	murl = 'http://192.168.1.20:8000/';
	var myChart = echarts.init(document.getElementById('xhf_home_tmp'));

	option = null;
	function get_tmpdata() {
	    $.get(murl, function (data) {
	        data = data["data"];
	        var kt = [];
	        var ws = [];
	        for (var i = 0; i < data.length; i++) {
	            if (data[i]["did"] == "28FFA83CB416399") {
	                kt.push(data[i]);
	            } else {
	                ws.push(data[i]);
	            }
	        }
	        myChart.setOption(option = {
	            title: {
	                text: '博主家温度'
	            },
	            tooltip: {
	                trigger: 'axis'
	            },
	            xAxis: {
	                data: kt.map(function (item) {
	                    return item["created"];
	                })
	            },
	            yAxis: {
	                type: 'value',
	                min: 18,
	                splitLine: {
	                    show: true
	                }
	            },
	            toolbox: {
	                left: 'center',
	                feature: {
	                    dataZoom: {
	                        yAxisIndex: 'none'
	                    },
	                    restore: {},
	                    saveAsImage: {}
	                }
	            },
	            dataZoom: [{
	                startValue: kt[kt.length-50]["created"]
	            }, {
	                type: 'inside'
	            }],
	            visualMap: {
	                top: 10,
	                right: 10,
	                pieces: [{
	                    gt: -40,
	                    lte: 10,
	                    color: '#ff9933'
	                },{
	                    gt: 10,
	                    lte: 26,
	                    color: '#096'
	                }, {
	                    gt: 26,
	                    lte: 40,
	                    color: '#ffde33'
	                }, {
	                    gt: 42,
	                    color: '#ffde33'
	                }],
	                outOfRange: {
	                    color: '#999'
	                }
	            },
	            series: [{
	                name: '客厅温度',
	                type: 'line',
	                data: kt.map(function (item) {
	                    return item["value"];
	                }),
	                smooth: true,
	                markLine: {
	                    silent: true,
	                    data: [{
	                        yAxis: 50
	                    }, {
	                        yAxis: 100
	                    }, {
	                        yAxis: 150
	                    }, {
	                        yAxis: 200
	                    }, {
	                        yAxis: 300
	                    }]
	                }
	            },{
	                name: '卧室温度',
	                type: 'line',
	                data: ws.map(function (item) {
	                    return item["value"];
	                }),
	                smooth: true,
	                markLine: {
	                    silent: true,
	                    data: [{
	                        yAxis: 50
	                    }, {
	                        yAxis: 100
	                    }, {
	                        yAxis: 150
	                    }, {
	                        yAxis: 200
	                    }, {
	                        yAxis: 300
	                    }]
	                }
	            }]
	        });
	    });
	    if (option && typeof option === "object") {
	        myChart.setOption(option, true);
	    }
	}

	get_tmpdata();


</script>
{% assign current_year = site.time | date: '%Y' %}

HiFLy
===
{{ site.description }}
## 概况

- 邮箱：ylxhf#163.com
- 主页：


<div id="xhf_home_tmp" style="height: 100%"> </div>


