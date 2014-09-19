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

##定义tableView以及数据源

       @property (nonatomic,strong) UITableView *contactTableView;
       @property (nonatomic,strong) UITableView *indexTableView;
       @property (nonatomic, strong) NSArray *indexDataSource; //二级索引的数据源


##获取手机通讯录
       /**
        *  导入通讯录
        *  此方法是重点，sectionDic(NSMutableDictionary),key值为排序联系人姓的首字母(已分组，排序)*，value为姓首字母对应的联系人数组
       */
       -(void) loadContacts{
         [sectionDic removeAllObjects];
         [phoneDic   removeAllObjects];
         [contactDic removeAllObjects];
         for (int i = 0; i < 26; i++) 
             [sectionDic setObject:[NSMutableArray array] forKey:[NSString stringWithFormat:@"%c",'A'+i]];
         [sectionDic setObject:[NSMutableArray array] forKey:[NSString stringWithFormat:@"%c",'#']];
    
         ABAddressBookRef myAddressBook =ABAddressBookCreate();
    
         CFArrayRef results = ABAddressBookCopyArrayOfAllPeople(myAddressBook);
         CFMutableArrayRef mresults=CFArrayCreateMutableCopy(kCFAllocatorDefault,
                                                        CFArrayGetCount(results),
                                                        results);
        //将结果按照拼音排序，将结果放入mresults数组中
         CFArraySortValues(mresults,
                      CFRangeMake(0, CFArrayGetCount(results)),
                      (CFComparatorFunction) ABPersonComparePeopleByName,
                      (void*) ABPersonGetSortOrdering());
        //遍历所有联系人
         for (int k = 0; k < CFArrayGetCount(mresults); k ++) {
            ABRecordRef record=CFArrayGetValueAtIndex(mresults,k);
            NSString *personname = (__bridge NSString *)ABRecordCopyCompositeName(record);
            ABMultiValueRef phone = ABRecordCopyValue(record, kABPersonPhoneProperty);
            ABRecordID recordID=ABRecordGetRecordID(record);
            for (int k = 0; k<ABMultiValueGetCount(phone); k++)
            {
               NSString * personPhone = (__bridge NSString*)ABMultiValueCopyValueAtIndex(phone, k);
            
               if (personPhone.length < 3) {
                 continue;
               }
            
               NSRange range = NSMakeRange(0,3);
               NSString *str=[personPhone substringWithRange:range];
               if ([str isEqualToString:@"+86"]) {
                  personPhone=[personPhone substringFromIndex:3];
               }
            
              [phoneDic setObject:(__bridge id)(record) forKey:[NSString stringWithFormat:@"%@%d",personPhone,recordID]];
            
            
            }
            char first=pinyinFirstLetter([personname characterAtIndex:0]);
            NSString *sectionName;
            if ((first>='a'&&first<='z')||(first>='A'&&first<='Z')) {
               if([self searchResult:personname searchText:@"曾"])
                  sectionName = @"Z";
               else if([self searchResult:personname searchText:@"解"])
                  sectionName = @"X";
               else if([self searchResult:personname searchText:@"仇"])
                  sectionName = @"Q";
               else if([self searchResult:personname searchText:@"朴"])
                  sectionName = @"P";
               else if([self searchResult:personname searchText:@"查"])
                  sectionName = @"Z";
               else if([self searchResult:personname searchText:@"能"])
                  sectionName = @"N";
               else if([self searchResult:personname searchText:@"乐"])
                  sectionName = @"Y";
               else if([self searchResult:personname searchText:@"单"])
                  sectionName = @"S";
               else
                  sectionName = [[NSString stringWithFormat:@"%c",pinyinFirstLetter([personname characterAtIndex:0])] uppercaseString];
            }
            else {
               sectionName=[[NSString stringWithFormat:@"%c",'#'] uppercaseString];
            }
        
           [[sectionDic objectForKey:sectionName] addObject:(__bridge id)(record)];
           [contactDic setObject:(__bridge id)(record) forKey:[NSNumber numberWithInt:recordID]];
         }
       }




##显示通讯录一级索引
       -(NSInteger)tableView:(UITableView *)tableView sectionForSectionIndexTitle:(NSString *)title atIndex:(NSInteger)index
       {
    
        if ([tableView isEqual:_contactTableView])
        {
         //获取用户点击的一级索引的字母是哪个
         NSString *key = [NSString stringWithFormat:@"%c",[ALPHA characterAtIndex:index]];
        
         //显示二级索引
         [_indexTableView setHidden:NO];
        
         //获取对应字母下的联系人姓的列表
         _indexDataSource = [self getLastNameFromRecord:key withtag:YES];
         [_indexTableView reloadData];
        
         return  [ALPHA rangeOfString:title].location;
        }
    
        return 0;
       }



##实现点击二级索引的cell，联系人tableView滑动到指定的位置
       - (void)tableView:(UITableView *)tableView didSelectRowAtIndexPath:(NSIndexPath *)indexPath {
         if ([tableView isEqual:_indexTableView]) {
         NSString *name = [_indexDataSource objectAtIndex:indexPath.row];
         NSString *first= [[NSString stringWithFormat:@"%c",pinyinFirstLetter([name characterAtIndex:0])] uppercaseString];
         int sectionIndex = [ALPHA rangeOfString:first].location;
         //根据first(例如：M)，找到对应M对应的的所有联系人，ABPerson类型
         NSMutableArray *contactLastNames = [self getLastNameFromRecord:first withtag:NO];
         NSUInteger arrayRow = [contactLastNames indexOfObject:name];
        
         //联系人列表滑动到指定section的指定row
         [_contactTableView scrollToRowAtIndexPath:[NSIndexPath indexPathForRow:arrayRow inSection:sectionIndex] atScrollPosition:UITableViewScrollPositionTop animated:NO];
         }
        }