# chatroom
java命令行聊天室项目  
安卓培训时做的java项目，  

一，已经完成的，  
通过java客户登录注册修改密码修改资料，并存在服务器中，  
能够添加好友，进入群，实现好友聊天，群聊功能，  
能够查看历史聊天记录，  
能够查看在线好友，  
能查看好友资料，包括好友国籍，实现多国语言聊天，  
二，未完成的，  
查看好友留言，  
创建添加可以永久保存的群，  

三，细节  
1,登录注册是选择模式，  
a)用户名有限制，  
ascii字符只允许数字字母下划线，  
utf8大于ascii的部分不限制，  
b)登录注册失败都是直接断开连接，  
c)登录过程中强制退出的情况也能被服务器捕获到，  
d)注册完成后直接就已经登陆，  
e)上一次的登陆没退出的话会将上一次登陆强制下线，  

2,登录后是命令模式，  
a)每一行(nextLine())都处理一次，  
b)所有斜杠/开头的输入都当成命令，  
用空格分隔作为多个参数，  
c)参数个数不对也视为未知命令，  
d)不是命令的输入直接发送出去，  

3,发送消息，  
a)房间管理模式，  
所有人登陆后进入名为"hall"的房间，  
所有人发送的消息都是转发给同一房间的所有人，  
b)在房间"hall"里面发送的消息无视，  
c)收发双方的资料里的国家如果不同就先翻译消息，  
d)聊天都是创建新房间然后所有人进来聊，  

4,聊天，  
a)/talkto 房间名 用户名[ 用户名...]  
b)单人聊天就是只有两人的多人聊天，  
c)只有互相添加好友才能聊天，  

5,好友，  
a)/makefriend 用户名  
b)添加好友对方不知道，  
c)/onewayfriend 如果对方没添加自己为好友，自己也能看到，  
d)不能添加自己为好友，  

6,翻译  
a)发送消息时带上自己的资料，  
然后管理房间的类负责判断是否要翻译，  
b)百度翻译api，  
chatroom.translate.BaiduTranslate这个类里面填上相关信息才能用，  

7,聊天记录，  
a)管理房间的类负责将自己收到的消息存进数据库，  
b)存的是翻译前的消息，  
b)读取的聊天记录不翻译，  

8,用户资料，  
a)/setalldata 修改所有资料，  
b)每个资料都能分别改，  

-------------------  
原本是放在另一个仓库里的，  
https://github.com/AoEiuV020/android-training/tree/master/java/net/chatroom  
突然觉得这就是一个完整的应用了，  
可以单独放一个仓库，  
关于数据库，  
设置外键时mysql总是报错1005: Can't create table  
无法解决，遂放弃，不用外键，  

