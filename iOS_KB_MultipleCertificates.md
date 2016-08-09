# 多证书

## 场景

某些 iOS 应用在发布时可能会分为不同的版本，如打车软件的司机版和乘客版、交易软件的买家版和卖家版。
开发者往往希望在发推送时，不同版本的应用都能同时收到。

在这种场景下，可以使用云巴提供的 “多证书” 功能。

## 使用对象

**“多证书” 针对的对象是：同一个 [AppKey](Product_KB_AppKey.md)、不同版本的 iOS 应用。**

## 如何使用

“多证书” 的使用很简单，只需在 [Portal](Product_KB_Portal.md) 创建应用时上传多个证书即可。
上传的界面如下图所示。


云巴会自动检测哪个证书对应哪个设备，确保消息送达所有的订阅设备。



![multicert.png](https://raw.githubusercontent.com/yunba/docs/master/image/for_kb/multicert.png)
