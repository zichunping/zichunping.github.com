---
layout:     post
title:      iphone基础教程2内容整理
category: blog
description: UIView
---

###iphone教程第二章
* UIWindow：继承至UIView
  - UIKit框架
  - UIView
  - UIViewController
  - UIScreen：获取物理设备的屏幕大小
  - 获取当前UIWindow和级别

* UIView
  - 大部分控件都是UIView的子类
  - iOS坐标系统：
    - 从左上角开始
    - 每个view的frame所使用的坐标是已其父视图的左上角为原点
    - 函数：point：位置、size：大小、rect：位置和大小
  - iphone各个型号的手机的实际大小是其分辨率的一半：比如iPhone4s的分辨率是640\*960，那么它的实际大小就是：320\*480
  - Frame：已父视图为起点，得到自己的位置信息
  - Bounds：是已iOS坐标原点为起点，坐标为(0，0)
  - Center：表示视图中心点位置，改变该属性可以改变视图的位置

* 视图的层次关系
  - UIView的层次结构可以理解为“视图树”
  - subview，superview
  - 从视觉上看，子视图遮挡了父视图的内容，设置透明属性可以看到父视图内容
  - 一个视图的子视图可以有多个，但是父视图只能有一个
  - 常用的方法
  - 子视图的坐标是已父视图的坐标原点来相对计算的


* UIView的基本属性和自定义
  - UIView tag属性：默认为0，可以标示一个视图对象，通过viewWithTag获取
  - 通过tag来查找UIView
  - UIView的常用属性掌握：透明度：父视图上设置透明度，子视图也会受影响；Hidden：父视图上设置hidden，子视图也会受影响
  - 自定义UIView：   
  - dealloc方法的调用
  - 视图对象的清理


* 简单仿射变换：坐标系统变换
  - 缩放、旋转、平移，要与动画结合起来


* UIView的ContentModel：视图的内容模式
  - 决定了边界变化和缩放操作
  - contentModel属性
  - 只有png格式的图片不需要写后缀名
  - @2x后缀的图片标示高清视网膜屏幕
  - clipsToBounds属性：超出view的范围减掉它
  
* UIView简单动画
  - UIView的属性动画
  - 动画的委托方法
  - 配置动画的参数
  - UIView的作用：布局、动画、事件的传递
  