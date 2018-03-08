---
layout: post
title: "TensorFlow学习-(1)快速入门"
date: 2018-03-06 14:02:00 +0800
categories: [tensorflow]
tags: [tensorflow]
comments: true
---


TensorFlow，Google开源的一款人工智能学习系统。支持多种设备，而且TF的使用很方便，几行代码就能开始跑模型，这让神经网络的入门变得非常简单。

毫不夸张得说，TensorFlow的流行让深度学习门槛变得越来越低，只要你有Python和机器学习基础，入门和使用神经网络模型变得非常简单。TensorFlow支持Python和C++两种编程语言，再复杂的多层神经网络模型都可以用Python来实现，如果业务使用其他编程也不用担心，使用跨语言的gRPC或者HTTP服务也可以访问使用TensorFlow训练好的智能模型。


TensorFlow安装
===========
我的环境：xUbuntu 16.04，python3.5

我安装的是CPU版本：
```
pip3 install tensorflow
```


如安装GPU版，则为：
```
pip3 install tensorflow-gpu
```

具体安装步骤，网上有很多，不在多说。


TensorFlow基础概念
============

* <b>Graph</b>图：用来表示计算任务，就是我们要做的一些操作。

* <b>Session</b>会话：在会话 (Session) 的上下文 (context) 中执行图；

  建立会话，此时会生成一张空图；在会话中添加节点和边，形成一张图，一个会话可以有多个图，通过执行这些图得到结果。如果把每个图看做一个操作台，那会话就是一个生成线，里面有若干个操作台，用来把数据生产成结果。


* <b>Tensor</b>张量：用来表示数据，是我们的原料。

* <b>Variable</b>变量：用来记录一些数据和维护状态。

* <b>feed和fetch</b>：可以为任意的操作(arbitrary operation) 赋值或者从其中获取数据。相当于一些操作台上的工具，可以操作数据。


TensorFlow 是一个编程系统, 使用图来表示计算任务. 图中的节点被称之为 op (operation 的缩写). 一个 op 获得 0 个或多个 Tensor, 执行计算, 产生 0 个或多个 Tensor. 每个 Tensor 是一个类型化的多维数组. 例如, 你可以将一小组图像集表示为一个四维浮点数数组, 这四个维度分别是 [batch, height, width, channels].

一个 TensorFlow 图描述了计算的过程. 为了进行计算, 图必须在 会话 里被启动. 会话 将图的 op 分发到诸如 CPU 或 GPU 之类的 设备 上, 同时提供执行 op 的方法. 这些方法执行后, 将产生的 tensor 返回. 在 Python 语言中, 返回的 tensor 是 numpy ndarray 对象; 在 C 和 C++ 语言中, 返回的 tensor 是 tensorflow::Tensor 实例.

TensorFlow综述
============
