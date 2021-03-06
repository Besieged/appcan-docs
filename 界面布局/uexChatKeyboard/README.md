#uexChatKeyboard###提供聊天输入相关的功能，集成了表情、拍照、从相册选取图片等分享功能，只需简单的widget配置即可实现自定义表情集和分享选项内容。方法:	open 打开聊天输入	close 关闭聊天输入监听方法：	onCommit  点击发送的监听方法	onShareMenuItem  点击分享里选项的监听方法	onVoiceAction  录音按钮的监听方法#### open  打开聊天输入  
`uexChatKeyboard.open(viewInfo) `  
说明:   在界面的底部打开聊天输入框界面参数:  
viewInfo: (String类型) 必选  聊天输入的信息  
该字符串为JSON格式，如下：```
{    "emojicons": "res://emojicons/emojicons.xml",    "shares": "res://shares/shares.xml",    "placeHold": "请输入内容",    "touchDownImg": "res://1.png",    "dragOutsideImg": "res://2.png",    "textColor": "#FFF",    "textSize": "15.5"}```各字段含义如下:|参数      |  参数类型 | 是否必须|说明||-----------|-------|-------|---||emojicons      |String|是|自定义表情配置文件的widget路径||shares	        |String |是	|自定义分享选项配置文件的widget路径||placeHold      |String	|否|	输入框提示语||touchDownImg	 |String	|否	|录音按钮按下时提示控件的背景||dragOutsideImg	 |String	|否	|按下录音按钮后滑动到录音范围之外时提示控件的背景||textColor   	|String	|否	|录音时间文字颜色||textSize       |String|	否	|录音时间文字大小|自定义表情的配置文件配置步骤：1. 在widget的wgtRes目录下创建emojicons目录；2. 在emojicons中放入表情以及删除的图片资源，表情的默认命名格式：ace_emoji_1，删除的默认命名格式：ace_emoji_delete.png；3. 在emojicons中创建emojicons.xml文件，格式如下：```<?xml version="1.0" encoding="utf-8"?><emojicons delete="ace_emoji_delete.png ">   <key>[微笑]</key>   <string> ace_emoji_1.png</string>   <key>[憋嘴]</key>   <string> ace_emoji_2.png</string></emojicons>```delete：删除对应的图片名；key：表情对应的文字；string：表情对应的图片名；     说明：表情目录、图片名以及配置文件名都可以自定义命名，但是必须保证配置文件中的图片名与资源图片对应。自定义分享选项的配置文件配置步骤:1. 在widget的wgtRes目录下创建shares目录；2. 在shares中放入分享选项的图片资源，图片的默认命名格式：ace_share_1；3. 在shares中创建shares.xml文件，格式如下：~~~<?xml version="1.0" encoding="utf-8"?><shares>	<key>拍照</key>	<string>ace_share_1.png</string>	<key>图片</key>	<string>ace_share_2.png</string>	<key>位置</key>	<string>ace_share_3.png</string></shares>~~~`key`：分享选项显示的文字  
`string`：分享选项对应的图片名说明;
分享目录、图片名以及配置文件名都可以自定义命名，但是必须保证配置文件中的图片名与资源图片对应。  
  
平台支持:  
Android 2.2+  
iOS 4.3+    

版本支持：  
    3.0.0+    

示例:```
var jsonstr ='{    "emojicons": "res://emojicons/emojicons.xml",    "shares": "res://shares/shares.xml",    "placeHold": "请输入内容",    "touchDownImg": "res://1.png",    "dragOutsideImg": "res://2.png",    "textColor": "#FFF",    "textSize": "15.5"}';uexChatKeyboard.open(jsonstr);```#### close关闭聊天输入  	uexChatKeyboard.close()  
说明:   
关闭聊天输入    
参数:  	无  
  
平台支持:  
Android 2.2+  
iOS 4.3+  
  
版本支持：  
3.0.0+  
示例:```
uexChatKeyboard.close();```  
#### onCommit 点击发送按钮时的监听方法`uexChatKeyboard.onCommit (data)`参数: 
data: (String类型)  必选  表情对应的文字该字符串为JSON格式。如下：```  
{    "emojiconsText": "[微笑] [憋嘴]"}```版本支持： 3.0.0+#### onShareMenuItem点击分享里选项的监听方法    
uexChatKeyboard. onShareMenuItem (data)  
  
参数: 
 data: (Number类型)  必选  分享里各选项对应的位置  
  
版本支持：  
3.0.0+#### onVoiceAction录音按钮的监听方法  
uexChatKeyboard. onVoiceAction (data)  
参数:   
 data: (String类型)  必选  录音按钮的状态  
  
该字符串为JSON格式。如下：{    "status": 1}各字段含义如下:
|参数 |是否必须|说明|
|----|-------|---||status|是  |录音按钮的状态，0--开始录音，1--录音完成，-1--取消录音|
版本支持： 3.0.0+