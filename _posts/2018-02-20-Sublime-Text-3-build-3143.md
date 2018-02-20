---
layout: post
title: "Sublime Text 3 build 3143"
date: 2018-02-20 19:28:00 +0800
categories: [Sublime Text]
tags: [Sublime,3143]
comments: true
---




万年不更新的Sublime Text 3更新了，新版进行了众多优化和高DPI优化支持...



下载安装
============

版本: Sublime Text 3 build 3143
下载安装这里就不多说了，自己去[官方](https://www.sublimetext.com/3)下载。


中文版设置
============

1. 点击 Tools  -> Install Package Control ，稍等一会会提示 Package Control was successfully installed

2. 点击 Preference -> Package Control，输入 install 找到 Install Package 后按回车

3. 输入 localiza ，细心的你会发现想要的东西，按回车安装

4. 点击 Help -> Language，选择“简体中文”即可


正版激活
============

激活码来自网友的分享，如要不妥，请联系移除。

```
—– BEGIN LICENSE —–
TwitterInc
200 User License
EA7E-890007
1D77F72E 390CDD93 4DCBA022 FAF60790
61AA12C0 A37081C5 D0316412 4584D136
94D7F7D4 95BC8C1C 527DA828 560BB037
D1EDDD8C AE7B379F 50C9D69D B35179EF
2FE898C4 8E4277A8 555CE714 E1FB0E43
D5D52613 C3D12E98 BC49967F 7652EED2
9D2D2E61 67610860 6D338B72 5CF95C69
E36B85CC 84991F19 7575D828 470A92AB
—— END LICENSE ——
```


中文输入问题
============

ubuntu(xubuntu)下不能输入中文问题

1. 首先，将你的操作系统升级到最新版

	```
	sudo apt-get update
	sudo apt-get upgrade
	```

2. clone修复项目到本地

	```
	git clone https://github.com/lyfeyaj/sublime-text-imfix.git
	```

3. 运行脚本

	```
	cd sublime-text-imfix && ./sublime-imfix
	```

4. 完成! 重新启动后就可以在sublime text 3! 

	感谢原作者的工作
	https://github.com/lyfeyaj/sublime-text-imfix


中文错位问题
============

ubuntu(xubuntu)下中文字体错位问题。
使用 文泉驿微米黑等宽 字体解决sublime 3143版本上述字体错位,空格缩小的问题,当然你也可以使用别的字体试试。
具体步骤如下:

1. 从ubuntu apt安装源安装文泉驿微米黑字体:

	```
	sudo apt-get install ttf-wqy-microhei
	```

2. 安装完成后,在sublime的Preferences->settings配置文件中加入 文泉驿微米黑等宽 字体:

	```
	"font_face": "WenQuanYi Micro Hei Mono",
	```
	   中文版在菜单 设置->用户设置（或为 首选项->设置）配置文件中加入 文泉驿微米黑等宽 字体:
	```
	"font_face": "文泉驿等宽微米黑",
	```

   我的配置为：

	```
	{
		"font_face": "文泉驿等宽微米黑",
		"font_size": 10.5,
		"ignored_packages":
		[
			"Vintage"
		]
	}
	```

