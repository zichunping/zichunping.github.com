##iOS中通知的使用
* NSNotificationCenter是Cococa消息中心，统一管理单进程内不同线程之间的消息通讯，其职责有两个：
	* 提供“观察者们”对感兴趣消息的监听注册
	
    		[[NSNotificationCenter defaultCenter] 				addObserver:self selector:@selector(printName:)       			name: @"messageName" 	object:nil];
    	* **defaultCenter**：消息中心只有一个，通过类方法获取它的单例
    	* **addObserver**：添加监听者实例，此处为当前实例(self)
    	* **selector**：observer中的一个方法指针，当有消息的时候会执行此方法，并把相关上下文已参数传递过去
    	* **name**：注册所关心消息的名称
    	* **object**：是消息发送方的一个过滤，此参数说明当前监听器对某个对象发出的消息感兴趣
    	
    	* **整体的意思**：向消息中心注册一个“监听者”(当前实例self)，当有名为NSWindowDidBecomeMainNotification的消息发送到消息中心时，执行实例的aWindowBecomeMain方法
    
    * 接收“消息”，并把消息  发送给关心它的“观察者们”
    	* 消息的推送
    	
    			[[NSNotificationCenter defaultCenter] postNotificationName:@"messageName" object:nil userInfo: [NSDictionary dictionaryWithObject:@"jory" forKey:@"name"|^Archive.zip]];
    		* postNotificationName：推送消息的名称，匹配在注册消息监听者时的消息名称
    		* object：发送消息的实例
    		* userInfo：发送消息时附带的消息上下文，此实例是一个字典实例
    
    * 当有消息推送到小心中心后，会把此消息发送给相关的“监听者”，并执行消息注册时的方法
    
    		-(void)printName:(id)sender{  
			NSString *name = [[sender userInfo] 			objectForKey:@"name"];  
			NSLog(@"name: %@",name);  
			} 
	方法很简单，从消息上下文中(发送消息时的userInfo)，获取“name”并打印
	
##实例
* iPhone软件开发的时候会遇到这种情况：打开app后会在后台运行某个方法，例如下载文件，下载完成后可能需要调用某个方法来刷新页面，这时候可能没法在下载的函数中回调。(通知)NSNotificationCenter是一个很好的选择
	* 定义(注册)通知：
	
			[[NSNotificationCenter defaultCenter] 			addObserver: self
			selector: @selector(callback)
			name: @"back"
			object: nil];
			
	* 定义通知中使用的方法：
	
    		- (void)callback{
			NSLog(@"i am back.");
			}
			
	* 调用通知：
	
			- (void)getIT{
			NSLog(@"get it.");
			//发出通知
			[[NSNotificationCenter defaultCenter] 			postNotificationName:@"back" object:self];
			}
	**在调用通知的时候，程序会在整个项目中寻找此通知的名称，找到后发出请求，因此通知的名称需要在整个项目中唯一**
    
    
    
    
    
    
    