---
layout:     post
title:      iPhone视频教程第三章
category: blog
description: 视图控制器与通知
---


###iphone教程第三章
* 视图控制器
  - 视图控制器的生命周期
  - 视图控制器的传值方式
  - 视图控制器负责创建和管理一组视图，它本身就提供一个视图，称为该控制器的根视图
  - 永远不要直接把UIView添加到UIWindow上面，而是添加一个UIViewController


*  视图控制器的创建
  - window的rootViewController属性


* 视图控制器视图的装载
  - UIViewController的生命周期
    - 只有进入到viewDidLoad时，view才被创建
    - viwDidLoad:当视图被加载后调用
    - 视图控制器装载的过程
    - 注意事项：当self.view=nil时，会出现循环调用loadView方法；不要在viewController的初始化方法中(init方法)做与视图相关的操作


* 视图控制视图的出现与消失
  - viewWillAppear：
  - viewDidAppear：
  - viewWillDisAppear：
  - viewDidDisappear：


* 视图控制器的卸载
  - view不在当前窗口上时，可以释放掉
  - 视图控制器的内存管理


* 模态视图，控制方向
  - 视图控制器的响应链：
  - 模态视图：出现场景一般是临时弹出的窗口叫模态视图：presentViewController
  - block：回调方法
  - UIDevice：获取当前设备相关信息
  - 关闭窗口：dismissViewController
  - 模态视图不会受到父视图的挟持
  
  
*  代理设计模式（**重点掌握**）
  - 代理：想做一件事情，但是没有能力去做，需要找一个代理(委托人)去做
  - 委托人中一定要设置代理
  - 一般应用于两个视图控制器之间


* 通知的用法(**重点掌握**)
  - 两个类完全没有关系
  - 通知不要滥用，耦合性太强，代码阅读性较差
  - 注册的通知要与post出去的通知一致
  - 当程序退出时(页面销毁)，dealloc方法，移除通知