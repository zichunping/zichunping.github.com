---
layout: post
title: iOS 通讯录二级索引
description: 由于项目的需要，需要实现类似于iPhone通讯录的一级索引，同时将对应section下的联系人lastName做为二级索引，实现更快、更方便的通讯录联系人查找。
category: blog
---

##设计思路

contactViewController中新建两个tableView：contactsTableView、indexTableView。其中，contactsTableView用于展示手机通讯录联系人信息以及一级索引(与iPhone通讯录自带的一级索引一致)，indexTableView用于展示联系人姓的首字母对应的所有联系人列表。

在这两个tableView上进行各自的操作时，要判断当前的tableView是哪个，例如计算section中row的个数的方法：
 
  - (NSInteger)tableView:(UITableView *)tableView numberOfRowsInSection:(NSInteger)section
{
    if ([tableView isEqual:_contactTableView]) {
        NSString *key = [NSString stringWithFormat:@"%c",[ALPHA characterAtIndex:section]];
        return [[sectionDic objectForKey:key] count];
    } else if ([tableView isEqual:_indexTableView]){
        
        NSInteger count = 0;
        
        if ([_indexDataSource count] > 0) {
            count = [_indexDataSource count];
        } else {
            //如果一级索引下的联系人为空，则不展示二级索引
            [_indexTableView setHidden:YES];
        }
        
        //重新为二级索引tableview计算高度
        CGRect frame = tableView.frame;
        frame.size.height = count * tableView.rowHeight;
        frame.size.height = MIN(9*tableView.rowHeight, frame.size.height);
        tableView.frame = frame;
        
        return count;
    }
    return [filteredArray count];
}

##示例代码

  @property (nonatomic,strong) UITableView *contactTableView;
  @property (nonatomic,strong) UITableView *indexTableView;
  @property (nonatomic, strong) NSArray *indexDataSource; //二级索引的数据源