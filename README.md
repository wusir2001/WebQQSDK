python所写的WebQQSDK

源码地址：https://github.com/linyuchen/WebQQSDK

支持收发好友消息，临时消息，群消息，好友在线状态改变，暂时不支持收发图片
支持好友验证消息，加群验证消息（群员邀请的不支持）
支持字体设置（大小，颜色，粗体、斜体、下划线），注意：气泡模式下是看不到字体的

所有消息均采用事件方式处理，
如果要添加处理消息的代码，请用插件开发方式
插件开发示例在plugins/example.py
开发文档在doc文件夹

直接运行main.py，会自动加载plugins内的插件

作者：0yuchen.com

更新日志：

V1.4

修复别人已经添加我为好友报错bug
添加群名片的支持
提高网络容错性,加入联网失败后重试两次的功能

v1.3

提高网络容错性，网络错误等原因不会让程序卡死
登陆插件的输入验证码改为异步方式

v1.2
修复密码和验证码错误时编码报错的bug

v1.1 release
msg的reply方法新增fontStyle参数


v1.1 beta3
新增:
    新增去除重复消息

    新增好友状态改变消息事件:
       addFriendStatusChangeEvent(self,msgEvent) 
    新增我被踢出群消息事件:
        addLeaveGroupEvent(self,msgEvent):
    新增群管理员变更消息事件:
        addGroupAdminChangeEvent(self,msgEvent)
    新增发送消息事件:
        addSendBuddyEvent(self, msgEvent)
        addSendGroupEvent(self, msgEvent)
    新增日志事件(日志消息包括：登录登出消息，收发消息，处理验证（好友和群）消息):
        addLogMsgEvent(self, msgEvent)
    Friend新增getName方法
        有备注返回备注，无则返回昵称

修改:
    同意别人加群后自动获取新群成员信息
    删除群成员直接返回删除结果字符串
    去掉了ip获取，实际上ip只是腾讯服务器的局域网ip，没什么用途
修复:
    msg修复reply的uin错误bug
    修复群成员获取失败bug

v1.1 beta2

新增错误处理msg和event
    ErrorMsg有两个属性，
        msg : string 详细错误信息
        summary : 简略的错误信息
    程序有错误时会发送ErrorMsg给event
    也可以调用addErrorMsg发送自定义错误信息给event

msg新增originalMsg属性，他是个列表，包含发送的文本消息和表情图片
msg新增pause方法，调用此方法后本msg处于暂停，暂时不让其他event处理
msg新增resume方法，让msg从暂停状态恢复过来
msg新增destroy方法，让msg销毁，销毁后其他event接收不到
msg新增reply方法，用于直接回复此消息,只有好友消息，临时会话，群消息可以使用

WebQQClient新增:
    self.startTime 程序启动时间 
        int型时间戳
    self.loginSucCount 登录成功的次数
        int型



