---
layout: default
---


{% assign current_year = site.time | date: '%Y' %}

HiFLy
===
{{ site.description }}

<div class="checkbox">
    <label>
        <input id="at_home" type="checkbox" onclick="get_tmp_data()">
    </label>
</div>
<div id="xhf_home_tmp" style="height: 400px"> </div>

<script type="text/javascript" src="http://echarts.baidu.com/gallery/vendors/echarts/echarts.min.js"></script>
<script type="text/javascript" src="http://echarts.baidu.com/gallery/vendors/echarts-gl/echarts-gl.min.js"></script>
<script type="text/javascript" src="http://echarts.baidu.com/gallery/vendors/echarts-stat/ecStat.min.js"></script>
<script type="text/javascript" src="http://echarts.baidu.com/gallery/vendors/echarts/extension/dataTool.min.js"></script>

<script type="text/javascript">
    var ajax = null;
    var t1 = null;
    var myChart = echarts.init(document.getElementById('xhf_home_tmp'));
    myChart.on('datazoom', function (params) {
        if (t1) {
            window.clearInterval(t1);
        }
    });
    
    myChart.on('restore', function (params) {
        if (t1) {
            window.clearInterval(t1);
        }
        doit();
    });

    function show_my_chart(data, textStatus) {

        var xdt = data["xAxis"];
        var start = data["start"];
        var kt = [];
        var ws1 = [];
        var ws2 = [];

        data = data["data"];
        for (var i = 0; i < data.length; i++) {
            if (data[i]["did"] == "28FFE1826017344") {
                kt.push(data[i]);
            }
            if (data[i]["did"] == "28FFA83CB416399") {
                ws1.push(data[i]);
            }
            if (data[i]["did"] == "28FFE99E017476") {
                ws2.push(data[i]);
            }
        }

        option = {
            title: {
                text: '家里温度'
            },
            tooltip: {
                trigger: 'axis'
            },
            xAxis: {
                data: xdt.map(function (item) {
                    return item;
                }),
                axisLabel: {
                    formatter: function (value, index) {
                        // 格式化成月/日，只在第一个刻度显示年份
                        var date = new Date(value);
                        var texts = [(date.getMonth() + 1), date.getDate()];
                        if (index === 0) {
                            texts.unshift(date.getFullYear());
                        }
                        //return texts.join('-');
                        return texts.join('-') + " " + date.getHours() + ":" + date.getMinutes();
                    }
                }
            },
            yAxis: {
                type: 'value',
                axisLabel: {
                    formatter: '{value}℃'
                },
                min: 10,
                splitLine: {
                    show: true
                }
            },
            graphic:[{
                type: 'group',
                rotation: Math.PI / 4,
                bounding: 'raw',
                right: 160,
                bottom: 130,
                z: 100,
                children: [
                    {
                        type: 'text',
                        left: 'center',
                        top: 'center',
                        z: 100,
                        style: {
                            fill: '#fff',
                            text: '家  里  温  度',
                            font: 'bold 22px Microsoft YaHei'
                        }
                    },
                    {
                        type: 'polygon',
                        //invisible: true,
                        shape: {
                            points: [[-80, 20], [-120, -20], [125, -20], [85, 20]]
                        },
                        style: {
                            fill: 'rgba(0,0,0,0.3)'//,
                            //text: '家  里  温  度',
                            //font: 'bold 30px Microsoft YaHei'
                        }
                    }
                ]
            }],
            toolbox: {
                feature: {
                    dataZoom: {
                        yAxisIndex: 'none'
                    },
                    restore: {},
                    saveAsImage: {}
                }
            },
            dataZoom: [{
                //startValue: xdt[xdt.length-50]
                startValue: start
            }, {
                type: 'inside'
            }],
            visualMap: {
                bottom: 70,
                left: 100,
                pieces: [{
                    lte: 0,
                    color: '#0080FF'
                },{
                    gt: 0,
                    lte: 18,
                    color: '#0000FF'
                },{
                    gt: 18,
                    lte: 26,
                    color: '#65CC66'
                }, {
                    gt: 26,
                    color: '#CC0033'
                }],
                outOfRange: {
                    color: '#999'
                }
            },
            series: [{
                name: '客厅温度',
                type: 'line',
                data: kt.map(function (item) {
                    return item["value"].toFixed(2);
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
                name: '主卧温度',
                type: 'line',
                data: ws1.map(function (item) {
                    return item["value"].toFixed(2);
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
                name: '次卧温度',
                type: 'line',
                data: ws2.map(function (item) {
                    return item["value"].toFixed(2);
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
        };
        if (option && typeof option === "object") {
            myChart.setOption(option);
        }
    }

    function get_tmp_data() {
        if (ajax) {
            ajax.abort();
        }
        var murl = "{{ site.data.xhfeng.flyhome }}";
        if($('#at_home').prop("checked"))
        {
            murl = "{{ site.data.xhfeng.flyhome1 }}";
        }

        ajax = $.ajax({
            type: "GET",
            url: murl,
            //crossDomain: true,
            data: {},
            dataType: "json",
            success: show_my_chart,
           error: function (xhr, status, errMsg) {
           }
        });
    }
    function doit() {
        // body...window.clearInterval(int)
        t1 = window.setInterval(get_tmp_data, 10*1000);
    }
    doit();
   
</script>


