---
layout: post
title: "Arduino - Nano针脚分配时需要注意的事项"
date: 2018-02-09 08:42:06 +0800
categories: Arduino
tags: [Arduino,Nano]
comments: true
---


- 0、1为Rx、Tx 针脚，这两个针脚一般作为串口使用，非串口设备尽量不占用该针脚。
- 2、3为中断口，分别对应中断0、中断1，需要中断功能的设备，必须接入此。
- 2～13、A0～A5，共18个针脚，都可以作为数字针脚，编号连起来，分别是2～19。
- 13针脚只能为OUTPUT模式，只能作为输出端，不能用作输入端。
- A6、A7针脚只能用做模拟信号，不能用作数字信号。

一般情况下，除了0、1、13、A6、A7这几个针脚比较特殊外，其他的针脚都可以按照正常功能使用。也就是说，2～12、A0～A5这17个针脚，基本可以放心使用。

<!-- UY BEGIN -->
<div id="uyan_frame"></div>
<script type="text/javascript" src="http://v2.uyan.cc/code/uyan.js?uid=2157469"></script>
<!-- UY END -->
<!--PC和WAP自适应版-->
<div id="SOHUCS" sid="请将此处替换为配置SourceID的语句" ></div> 
<script type="text/javascript"> 
(function(){ 
var appid = 'cytswofO5'; 
var conf = 'prod_923169747b26e1e787907408f0d9aaf2'; 
var width = window.innerWidth || document.documentElement.clientWidth; 
if (width < 960) { 
window.document.write('<script id="changyan_mobile_js" charset="utf-8" type="text/javascript" src="http://changyan.sohu.com/upload/mobile/wap-js/changyan_mobile.js?client_id=' + appid + '&conf=' + conf + '"><\/script>'); } else { var loadJs=function(d,a){var c=document.getElementsByTagName("head")[0]||document.head||document.documentElement;var b=document.createElement("script");b.setAttribute("type","text/javascript");b.setAttribute("charset","UTF-8");b.setAttribute("src",d);if(typeof a==="function"){if(window.attachEvent){b.onreadystatechange=function(){var e=b.readyState;if(e==="loaded"||e==="complete"){b.onreadystatechange=null;a()}}}else{b.onload=a}}c.appendChild(b)};loadJs("http://changyan.sohu.com/upload/changyan.js",function(){window.changyan.api.config({appid:appid,conf:conf})}); } })(); </script>