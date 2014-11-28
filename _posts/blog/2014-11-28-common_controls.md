---
layout:     post
title:      常见控件的使用
category: blog
description: iOS中常用控件的基本介绍
---


###常见控件的使用
* 警告视图：UIAlertView
* 提示视图：UIActionSheet


* UIButton：响应用户的点击事件
  - 工厂方法
  - 常用属性
  - 事件和状态的属性不要写错

* UIImageView
  - userInteractionEnabled 属性默认是NO，如果想在UIImageView上添加其他UIView，并且可交互，需要设置userInteractionEnabled 为YES
  - highlighted属性：高亮时


* UISearchBar
* UISwitch
* UIProgress视图

*UIActivityIndicatorView
 - 提示用户当前正在加载数据，转菊花，常用于网络时
 - 开始方法：startAnimating
 - 结束方法：stopAnimating
 - 状态栏的菊花：[[UIApplication sharedApplication] setNetworkActivityIndicatorVisible:YES]

* UISlider
  - 滑动空间，控制系统声音，或者表示播放进度
  - 添加事件


* UISegmentedControl
  - 分段控件：页面的切换
  - 样式、事件、图片


* UIPageControl
  - 分页控件，通常与UIScrollerView连用，提示用户当前显示的页数
  - 控件的自定义
  - hidesForSinglePage：一页时隐藏该控件
  
* UITextField代理方法
  - 常用的方法需要掌握
  - 一定要设置代码，交给谁来实现
  - textFieldShouldBeginEditing：应该开始编辑
  - textFieldDidBeginEditing：开始编辑
  - textFieldShouldEndEditing：即将结束编辑
  - textFieldDidEndEditing：完成编辑
  - 键盘立马弹起来是因为键盘在加载时就成为第一响应者：becomeFirstRespond
  
  - 失去第一响应，将键盘移除：resignFirstRespond
  
  - shouldChageCharactersInRange：场景：显示键盘用户的输入
  - textFieldShouldClear
  - textFieldShouldReturn：失去第一响应
  
* UITextField
  - 文本输入控件
  - placeholder：提示用户内容文本
  - clearsOnBeginEditing
  - 常用属性
  - borderStyle
  - adjustsFontSizeToFitWidth
  - leftView
  
  - 自定义系统键盘：
    - inputView
    - inputAccessoryView
    - 中文模式以及英文模式的区别
  
  - secureTextEntry：安全（密码）
  - keyboardType
  - returnKeyType
  - autocapitalizationType:大小写
  
  
  
 * UILabel
   - 不需要每个控件，每个视图，每个方法都掌握了，大致要了解下，知道有这个一个东西
   - 重点放在代码的逻辑上，结构上，架构上，设计类；产品的创意上
   - UILabel：显示文本
     - 常用属性
     - textAlignment：对齐方式
     - shadowColor：阴影
     - 打断方式：lineBreakMode
     - 字体大小：font
     - 换行：numberOfLines
     - 根据内容来适应：sizeToFit
 
 
 
 * UIControl
   - 具有处理事件
   - 事件响应的3种形式：基础触摸、基于值、基于编辑
   - 添加事件：addTarget
   - 事件处理：UIControlEvent...
   
   