---
layout:     post
title:      iphone基础教程1内容整理
category: blog
description: 简单整理下第一章节的内容
---

###iPhone开发基础教程1整理
* iOS中的lazy loading
* Interface Build简单了解下 
* UI布局时坐标的计算
* 掌握iPhone各个型号的分辨率：宽、高
  - iPhone4之前机型：320*480
  - iphone4、iPhone4s：640*960
  - iPhone5、iPhone5s：640*1136
* iPhone图标的大小：
  - Icon.png：57*57
  - Icon@2x.png：114*114
* tableview中cell的复用机制以及使用的掌握
* hash方法以及isEqual方法的重写使用：对象的比较
* 程序调试时，方法是以压栈的形式展示的
* Prefix.pch文件：预处理文件，提前加载
* Info.plist：应用程序的元数据文件
* 尽量不适用硬编码，可以使用宏定义
* @2x的图片表示视网膜屏幕的图片，双倍图片
* 模拟器常用操作：
   - Home键：comman+shift+h
   - 切换模拟器大小：command+1（2、3）
   - 显示后台运行的应用程序：comman+shift+h 2下h
   - 保存模拟器屏幕快照：command+s
   - command+shift+4：全屏拍照
   - 锁屏：command+l
* 沙盒机制：
   - app之间彼此是不能互相访问的
   - NSBundle类可以直接程序的包路径
   - 数据持久性内容都存放在Documents目录下
* 应用程序的生命周期：
   - 发生在程序启动到终止发生的一系列事件构成
   - UIApplicationMain函数：创建应用程序、创建应用程序代理，创建事件循环
   - 自动释放池：用于内存管理
   - application的常用delegate方法：app的活跃状态、非活跃状态、前台、后台

* 加入苹果开发者计划
    - 个人
    - 企业：无法上传AppStore，作为企业内部分发
    - 只有参与开发者计划，才能进行真机调试以及发布程序