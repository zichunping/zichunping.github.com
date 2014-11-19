---
layout:     post
title:      iOS Integrated youmeng
category: blog
description: iOS集成友盟分享组件
---

###iOS应用集成友盟分享组件
* 项目背景：由于该项目的私密性，不能使用已有的分享组件，需要使用第三方的分享SDK，考虑到目前比较主流且成熟的分享SDK，选择了友盟

* 第三方开放平台app注册、申请，参考友盟官方文档：<http://dev.umeng.com/social/ios/operation/step>
  - 微信：<http://open.weixin.qq.com>
  - qq：<http://op.open.qq.com/>
  - 新浪微博：<http://open.weibo.com/>

* 代码集成：
  - 通过pod依赖，集成友盟SDK：
    `pod 'UMengAnalytics' `
  - 在appdelegate的didFinishLaunchingWithOptions方法中集成友盟SDK:<br />
    #ifdef DEBUG
            [MobClick startWithAppkey:DCUMengAppKey 		reportPolicy:BATCH channelId:@"Daily"];
	#else
    		[MobClick startWithAppkey:DCUMengAppKey 			reportPolicy:BATCH channelId:nil];
		#endif
	- 导入友盟分享组件到工程中：现在分享SDK，之后解压SDK，将形如UMSocial_Sdk_x.x.x的文件夹拖入工程目录，具体操作参考：
	友盟教程：<http://dev.umeng.com/social/ios/share/quick-integration>
	- 在appdelegate的didFinishLaunchingWithOptions方法中添加如下代码：<br />
	
			[UMSocialData setAppKey:DCUMengAppKey];			[UMSocialQQHandler setQQWithAppId:DCQQAppId appKey:DCQQAppkey url:DCZhuojiOfficialWebsite];
			[UMSocialWechatHandler setWXAppId:DCWXAppId appSecret:DCWXAppSecret url:DCZhuojiOfficialWebsite];
			
			
	- 在appdelegate中添加如下方法：<br />
	
			(BOOL)application:(UIApplication *)application handleOpenURL:(NSURL *)url
			{
    		return [UMSocialSnsService handleOpenURL:url];
			}

			(BOOL)application:(UIApplication *)application openURL:(NSURL *)url sourceApplication:(NSString *)sourceApplication annotation:(id)annotation
			{
    		return [UMSocialSnsService handleOpenURL:url];
			}
			
	- 使用：在需要分享的视图源码中(viewController),添加以下代码<br >
	
			[UMSocialSnsService presentSnsIconSheetView:self
                                         appKey:DCUMengAppKey
                                      shareText:@"你要分享的文字"
                                     shareImage:[UIImage imageNamed:@"icon.png"]
                                shareToSnsNames:[NSArray arrayWithObjects:UMShareToWechatSession,UMShareToWechatTimeline,UMShareToQQ,UMShareToQzone,UMShareToSina,UMShareToTencent,UMShareToSms,nil]
                                       delegate:nil];

* 集成过程中遇到的问题：
  - 在qq的开放平台中注册了应用，通过审核过得到了appID以及appKey，工程中的appdelegate的didFinishLaunchingWithOptions中也添加了分享的代码，但是qq以及qzone的分享始终没有出来：
  	- 原因：qq的分享初始化代码滞后了，需要提交初始化，放到微信等平台的前面，如上面代码所示
  	
* 详细的集成请参考友盟官方文档：<http://dev.umeng.com/social/ios/share/>

	
