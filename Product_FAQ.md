# 常见问题解答（FAQ）

## 商务合作


**问： 云巴是如何收费的？**

答： 请发邮件到：support@yunba.io 咨询。

---
**问： 免费版每秒 20 条信息，超出后会怎样？**

答： 如果用户的使用量超出了免费版的限额，我们会提醒用户升级为付费服务。如果用户拒不接受，我们会在后台做出相应的使用限制。

---

## 业务范围


**问： 在那些地区可以使用云巴的服务？**

答： 目前，云巴提供中国大陆、中国香港、东南亚及北美地区的接入服务，如需开通其他地区的接入服务，请联系我们的商务人员。

---
**问： 云巴是做推送的吗？**

答： 云巴，即云消息总线，是一个跨平台实时消息系统。消息推送只是云巴其中一个产品。

---
**问： 云巴可以用于智能家居、物联网吗？**

答： 云巴兼容标准的 MQTT 3.1 协议，即物联网协议，因而天然支持智能家居、物联网。

---
**问： 云巴对 MQTT 协议做了哪些扩展？**

答： 请参考我们的 [Porting 文档](https://github.com/yunba/docs/blob/master/yunba_MQTT_porting.md)。

---
**问： 云巴有哪些产品？**

答： Android、iOS 消息推送（集成 APNs），跨平台双向实时通信，实时查看统计信息，实时获取在线状态。

---
**问： 云巴能用在 Web 上吗？**

答： 可以。云巴支持 Socket.IO 协议。请参考官网上的 [Socket.IO API](http://yunba.io/docs2/socket.io_API/)、[RESTful API](http://yunba.io/docs2/restful_Quick_Start/) 及 [JavaScript SDK](http://yunba.io/docs2/Javascript_SDK/) 文档。

---
**问： 云巴系统可以用来发短信吗？**

答： 不可以。

---
**问： 云巴可以根据地域进行推送吗？**

答： 暂不支持。

---
**问： 请问从国外访问云巴的服务会有问题吗？**

答： 没问题。

---
**问： 云巴有完整的聊天系统可直接用吗？**

答： 云巴只做最底层的消息系统，发送的具体内容不做处理。

---

## 基础问题


**问： [什么是云巴 Portal？如何在云巴 Portal 上创建新应用？](http://yunba.io/docs2/portal)**

---
**问： [什么是 AppKey？](http://yunba.io/docs2/appkey)**

---

## 消息推送、实时消息


**问： [云巴 iOS 消息推送是怎样的？](http://yunba.io/docs2/yunba_ios_messaging)**

---
**问： [如何通过云巴实现 APNs 推送？](http://yunba.io/docs2/ios_apns_guide)**

---
**问： [云巴 Android 消息推送是怎样的？](http://yunba.io/docs2/yunba_android_messaging)**

---
**问： 和其他公司相比，云巴的消息推送有什么不同？**

答： 云巴支持双向推送，一个客户端既可以 Publish 也可以 Subscribe。而其他家的单向推送只能执行 Subscribe，在执行 Publish 时，还需要提供新的接口。

---
**问： [云巴支持的 频道 和 别名 两种发布方式，具体是怎样的？](http://yunba.io/docs2/topic_and_alias)**

---
**问： [如何实时获取用户（设备）的在线状态？](http://yunba.io/docs2/presence)**

---
**问： [云巴的离线消息是怎样的？](http://yunba.io/docs2/yunba_offline_message)**

---
**问： 云巴的消息送达率是多少？**

答： 排除网络链路层的因素，理论上送达率是百分之百。

---
**问： 云巴的实时消息系统依赖什么网络环境？**

答： 2G，3G，4G，Wi-Fi 均可。

---
**问： 发送消息出现超时是什么原因？**

答： 请先检查网络连接是否正常。

---
**问： 发送的消息大小有什么限制吗？**

答： 建议不要超过 2K。

---
**问： 支持发送语音、图片、视频吗？**

答： 大数据建议使用第三方存储。可先将资源保存到服务器，然后推送地址。

---
**问： 发出的消息有历史记录吗？**

答： 目前只有在 Portal 发的消息，才可以查看历史记录。

---
**问： 订阅一个频道后，可以收到在订阅之前频道内推送的消息吗？**

答： 不可以。

---
**问： 发送方怎样知道接收方收到了？**

答： 服务器收到第一条 PUBACK 时，会给发送方发一个 [RECVACK](http://yunba.io/docs2/socket.io_API/#recvack)。

---
**问： 发布的消息可以撤回吗？**

答： 目前不支持撤回。

---
**问： 是否保证消息按顺序送达？**

答： 不保证。

---
**问： 发布消息前必须先订阅频道吗？**

答： 发布端可以不用订阅，但接收端必须订阅了频道，才能收到该频道发布的消息。

---
**问： 为什么我可以收到自己发布的消息？**

答： 只要订阅了就会收到。

---
**问： App 重新安装以后，之前的别名、订阅等信息都还在吗？**

答： 在。别名、订阅关系都存储在云巴服务器上。

---
**问： 是不是订阅一次就可以永久有效？**

答： 是。

---
**问： 频道的数量有限制吗？**

答： 没有。

---
**问： 离线消息的数量有限制吗？**

答： 最多保留 50 条。如有需要，可以联系我们提高限制数量。

---
**问： 可以同时给多个频道推送消息吗？**

答： 不可以。一次只能向一个频道发布消息。

---
**问： 云巴可以定点推送给某个设备吗？**

答： 可以，请参考 [别名](http://yunba.io/docs2/topic_and_alias/#%E5%88%AB%E5%90%8Dalias)（alias）的相关文档。

---
**问： 推送的消息出现乱码是什么原因？**

答： 云巴采用二进制透传，不对消息做任何处理。如果出现乱码，请自行检查应用的编码解码程序。

---
**问： 使用云巴 SDK，怎样实现不同平台之间的通讯呢？**

答： 在云巴官网 Portal 创建新应用，创建后得到一个 AppKey，在不同平台上使用同一个 
AppKey，即可互相通讯。

---
**问： 不同 AppKey 之间可以互相通信吗？**

答： 不可以。一个应用包名对应一个 AppKey，使用同一个 AppKey 的客户端才可以相互通信。

---
**问： Android SDK 不同包名可以互相通信吗？**

答： 使用云巴 Android SDK，如果需要同一个 Appkey 不同包名的客户端之间能够互相通信，请把 Appkey 
对应的包名发到 support@yunba.io，我们会在内部做些处理来支持。

---
**问： 用 Portal 和一个设备做测试时，“在线用户” 显示 2 个用户？**

答： 因为 Portal 本身也是一个用户。

---

## iOS SDK


**问： 如何实现 iOS 应用退出或者处于后台时可以收到推送消息？**

答： 
* 需要生成 APNs 证书；
* 在 App 注册 remoteNotification 通知，获取 Device Token，并通过[`storeDeviceToken()`](http://yunba.io/docs2/iOS_API_Reference/#storeDeviceToken)函数保存 Device Token 到云巴服务端；
* 通过带有 ApnOption 的`publish2()`、`publish2ToAlias()`或者默认的`publish()`、`publishToAlias()`发送 APNs 消息，该参数设置详见云巴知识库的 [Payload](https://github.com/yunba/kb/blob/master/APNs/Payload.md) 一文，以及 [iOS 官方文档](https://developer.apple.com/library/ios/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/Chapters/TheNotificationPayload.html#//apple_ref/doc/uid/TP40008194-CH107-SW1)。

**注**：`publish2()`需要带有 ApnOption 参数才能成功发送 APNs 消息；而`publish()`会发送默认的 APNs 消息。

---
**问： 接收的消息，除了基本的内容（Topic 和 Message）还可以传递一些参数信息吗？**

答： 开发者可以封装多个数据到 data.msg。

---
**问： ApnOption 的 sound 和 badge 有什么作用？**

答： 可在`publish2ToAlias()`、`publish2()`的 ApnOption 参数设置消息通知的方式。
alert 设置消息通知栏的内容；badge 设置角标；sound 设置通知的铃声。

具体参考云巴知识库的 [Payload](http://yunba.io/docs2/ios_apns_payload) 一文，以及 [iOS 官方文档](https://developer.apple.com/library/ios/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/Chapters/TheNotificationPayload.html#//apple_ref/doc/uid/TP40008194-CH107-SW1)，或下载 [iOS demo]( http://yunba.io/developers/) 参考 ApnOption 的设置方法。

---
**问： 如何自定义 iOS 推送的铃声？**

答： 先将自定义的铃声文件加入你的 Xcode 工程里，然后，在推送的时候指定音频的名称即可。注意使用系统支持的音频格式。

```json
{
	"aps": {
		"alert":"yunba",
		"badge":3,
		"sound":"bingbong.aiff"
	}
}
```
 
 如使用默认铃声，则为：
```JSON
 "sound":"default"
```

---
**问： 如何处理 badge？**

答： 在推送的时候可通过指定 badge 的值来改变当前的 badge（如上例）；通过`[[UIApplication sharedApplication] setApplicationIconBadgeNumber:0];`可清除 badge 的值。

---
**问： iOS SDK`subscribe()`的 qosLevel 参数，和 YBPublish2Option 的 qos 这两个参数有什么区别？**

答：`subscribe()`的 qos Level 限制该话题下接收到 message 的最大 qos 等级。 例如：当设置`subscribe()`的 qosLevel 为 0，则 qos 为 1 的接收消息会降级到 qos 为 0。详见 [MQTT V3.1 Protocol Specification
]( http://public.dhe.ibm.com/software/dw/webservices/ws-mqtt/mqtt-v3r1.html#subscribe) 和 [QoS](http://yunba.io/docs2/qos) 的说明。

---
**问： iOS 端怎么设置不接收任何消息？**

答： 设置别名为空，并`unsubscribe()`所有 Topic。

---
**问： 当同时定义了`publish()`的 data 和 ApnOption 参数中 alert 的 message，消息内容将以哪个为准？**

答： 以 alert 的 message 为准。未定义 alert 时，则默认显示`publish()`的 data。

---
**问： iOS 端如何设置通知方式？**

答： 上传 APNs 证书；通过 YBPublish2Option 参数的 alert 设置通知栏内容、角标和声音等，具体参考 sdk 中关于[`pushlish2()`](http://yunba.io/docs2/iOS_API_Reference/#publish2)的介绍，也可以下载并参考 [iOS demo]( http://yunba.io/developers/) 中 YBPublish2Option 的设置。

完整的设置方法请参考 [iOS 官方文档](https://developer.apple.com/library/ios/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/Chapters/TheNotificationPayload.html#//apple_ref/doc/uid/TP40008194-CH107-SW1)。

---

## Android SDK


**问： 当 App 退出，进程被杀死时，能接收到 Message 吗？**

答： Android 端需要在后台保留进程才能接收消息；iOS 端的 APNs 在 App 退出后仍可接收消息。

Android 端的解决方法：增加相互拉起功能和后台守护进程，使 App 退出后仍能接收到推送消息。可下载并参考 [特殊版本的 SDK](https://raw.githubusercontent.com/yunba/yunba-sdk-releases/master/Android/YunBa-Android-sdk-1.6.3.zip)（该版本仅供测试）。

---
**问： Android 端如何设置 qos 等级？**

答：`publish2()`、`publish2ToAlias()`的 opts(JSONObject) 参数可以设置 qos。

附：qos 为服务质量等级。有三种取值：0 表示最多送达一次；1 表示最少送达一次；2 表示保证送达且仅送达一次。默认为 1。详见 [QoS](http://yunba.io/docs2/qos) 的说明。

---
**问： Android 端怎么设置离线消息时间？**

答： 设置`publish2()`、`publish2ToAlias()`的 opts（JSONObject） 参数；
qos 设置为 1 或 2，就能够保证离线消息的送达；设置 time_to_live，可以控制离线消息在云巴服务器上保留的时间（以秒为单位）。详见：[云巴的离线消息](http://yunba.io/docs2/yunba_offline_message) 。

---
**问： YunBa Android SDK 有没有设置通知栏的 API？**

答： 关于设置消息通知栏，YunBa Android SDK 没提供相关的 API。设置方法可参考 [Android 官方文档](http://developer.android.com/guide/topics/ui/notifiers/notifications.html)。


---
**问： 怎么获取 Message 的 Message ID？**

答： YunBa Android SDK 暂时没有提供获取接收消息的 Message ID 的API。
如果需要 Message ID 等自定义内容，可以封装自定义内容到 Message 进行发送，在接收时进行解析。

---
**问： Android 端如何断开连接，不接收消息？**

答： 可以调用[`stop()`](http://yunba.io/docs2/Android_API_Reference/#stop)停止推送服务，使所有的 API 都失效（包括 start API）；当需要重新使用推送服务时，必须要调用[`resume ()`](http://yunba.io/docs2/Android_API_Reference/#resume)。

---

##JavaScript SDK


**问： 如何获取`publish2()`的 opts 设置参数？**

答： 可以把 opts 参数封装到 Message，在接收时进行解析。

---
**问： 如何接收离线消息？**

答： 用[`connect_by_customid()`](http://yunba.io/docs2/Javascript_SDK/#connect_by_customid
) 进行连接，连接后的会话状态与上次连接一致（包括离线消息、已订阅的频道和别名）。`connect()`仅用于测试，无法接收离线消息。

---
**问： 如何判断消息来自频道还是用户？**

答： 开发者可传递 Message ID，接收时通过 Message ID 进行判断。设置 Message ID 的方法可以参考 demo 的 [mqtt_publish2 方法](https://github.com/yunba/yunba-javascript-sdk/blob/master/examples/yunba_javascript_demo.html)。

---
**问： 用户订阅的 Topic 和设置的别名 Alias 保存在哪里？**

答： 保存在云巴服务端，与 CustomID 对应。

---
**问： JavaScript SDK 兼容哪些浏览器？**

答： 支持浏览器的版本如下:

   | IE  | Safari | Chrome  | Opera  | Firefox |
   |:-----:|:-----:|:-----:|:-----:|:-----:|
   | 7+  |  ✓   |  ✓  |  ✓   |  ✓ |

IE7 以下版本需 [配置](https://github.com/yunba/yunba-javascript-sdk) 即可。


---
**问： 如何批量订阅频道？**

答： 可以将订阅频道放到数组里，循环订阅。

---

## RESTful API



**问： RESTful 如何设置离线消息保留时间？**

答： "opts" 设置 "qos" 值为 1 或 2，才能成功发送离线消息；设置 "time_to_live" 参数指定离线消息的保留时间，默认是5天，详见： [云巴的离线消息](http://yunba.io/docs2/yunba_offline_message) 和 [RESTful API 的示例]( http://yunba.io/docs2/restful_Quick_Start/#HTTPPOST)。

---
**问： 加 opts 参数之后，可以用 get 请求吗？**

答： GET 方法不支持复杂参数，只是用来做简单测试；可以用 POST 方法，具体参考 [官方文档](http://yunba.io/docs2/restful_Quick_Start/#HTTPPOST)。同时注意请求头的设置： Content-type: application/json。

---
**问： RESTful API 可以指定 Message ID 吗？**

答： 云巴服务端随机生成 Message ID。

---
**问： RESTful的`publish_to_alias_batch()`API 中别名 Alias 的最大数量有限制吗？**

答： 别名的数量建议在 1000 以下。

---
**问： RESTful 的 Message 支持最大传送数据多大？**

答： 建议不要超过 1k。

---
**问： RESTful 支持 https 进行加密吗？**

答： 付费用户支持 https 服务。可发邮件到 support@yunba.io 咨询。

---
**问： 使用 RESTful API 发送消息时需要区分 Android 和 iOS 平台设备吗？**

答： 不需要。 

**注**：apn_json 参数只针对 iOS 平台的 APNs 消息。具体参考 [官方文档](http://yunba.io/docs2/restful_Quick_Start/#HTTPPOST)，apn_json 参数的完整设置方法可参考 [iOS 官方文档](https://developer.apple.com/library/ios/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/Chapters/TheNotificationPayload.html#//apple_ref/doc/uid/TP40008194-CH107-SW1)。

---

## Socket.IO



**问： 使用什么版本的 Socket.IO-client？**

答： Node.js 请使用 0.9.17；Python 请使用 0.6.5。
