---
layout: post
title: "Sublime-Text-3-Python自动补全插件"
date: 2018-05-21 14:24:00 +0800
categories: [Sublime Text]
tags: [Sublime,Anaconda,Python,自动补全,插件]
comments: true
---




1. 安装Anaconda插件完成之后，会看到如下选项栏，说明Anaconda安装成功


安装Anaconda插件
============
1. Preference -> Package Control，Install Package 后按回车

2. 输入 Anaconda, 按回车安装

3. 安装完成后，在 Preference -> Package Settings 中可看到  Anaconda

配置自动补全
============

1. 打开 Preference -> Package Settings -> Anaconda -> Settings-Default

2. 设置Python主程序的实际位置，找到“python_interpreter” key，修改

如: 
```
"python_interpreter": "C:/Python36/python.exe"
```

3. 打开 Preference -> Package Settings -> Anaconda -> Settings-User
4. 键入以下json数据。保存，重启ST3即可。

```
{
    "python_interpreter": "C:/Python36/python.exe",
    "suppress_word_completions": true,
    "suppress_explicit_completions": true,
    "complete_parameters": true,
    "anaconda_linting":false
}
```

