# 频道和别名

云巴支持 频道 和 别名 两种发布消息的方式。

## 概述

### 1. 通过“频道”进行一对多的消息发布

![productpng_kb_publish2topic.png](https://raw.githubusercontent.com/yunba/docs/master/image/productpng_kb_publish2topic.png)

- `Subscriber 1` 订阅了 `Topic A`，而 `Subscriber 2` 和 `Subscriber 3` 订阅了 `Topic B`；
- `Publisher 1` 向 `Topic A`发布消息，则 `Subscriber 1` 可以收到；
- `Publisher 2` 向 `Topic B` 发布消息，则 `Subscriber 2` 和 `Subscriber 3` 可以收到。

### 2. 通过“别名”进行一对一通信

![productpng_kb_publish2alias.png](https://raw.githubusercontent.com/yunba/docs/master/image/productpng_kb_publish2alias.png)

- `Client 1` 设置自己的别名；
- `Client 2` 设置自己的别名；
- `Client 1` 和 `Client 2` 向对方的别名发布消息，进行一对一的通信。

## 频道（Topic）


### 1. 什么是频道

在电视广播中，高频影像信号和伴音信号占有一定宽度的频带，叫频道。有了不同的频道，就可以将资讯分门别类地输送给不同的目标受众。云巴的频道（Topic）也是类似的概念。

在 MQTT 3.1 协议中，对 Topic Name（又叫 Subject 或 Channel）是这样描述的：The topic name is the key that identifies the information channel to which payload data is published. Subscribers use the key to identify the information channels on which they want to receive published information.

简而言之，频道名称是用来让发布者和订阅者区分不同频道的标识符。云巴的频道名称只支持英文、数字和下划线，长度不超过 50 个字符。


### 2. 频道的特点

* 同一个 [AppKey](product_kb_app_key.md) 下，可以创建多个频道，暂无上限。
* 多个用户可以订阅同一个频道；一个用户也可以订阅多个频道。
* 频道和订阅的逻辑均存储在云巴服务器上，一经生成，永不失效。
* 只有订阅了某个频道，才可以收到该频道的消息。
* 只要没有取消订阅某个频道，永远都可以收到这个频道的消息。
* 消息的发布者并不一定需要订阅频道。
* 某个频道在第一次被订阅时，会被自动创建。

### 3. 相关 API
下面以 JavaScript SDK 为例，介绍一下与频道相关的 API。

* [`subscribe`](js_sdk_api_manual.md#subscribe) 用来订阅某个频道。订阅频道是增加逻辑，不会影响到现有的订阅情况。
* [`unsubscribe`](js_sdk_api_manual.md#unsubscribe) 取消对某个频道的订阅。
* [`subscribe_presence`](js_sdk_api_manual.md#subscribe_presence) 用来监听某个频道下所有用户的别名状态的变化。
* [`unsubscribe_presence`](js_sdk_api_manual.md#unsubscribe_presence) 用来取消对某频道下用户别名状态变化的监听。
* [`publish`](js_sdk_api_manual.md#publish) 向某频道发布消息。
* [`publish2`](js_sdk_api_manual.md#publish2) 是 `publish` 的升级版本，支持更多参数。
* [`get_topic_list`](js_sdk_api_manual.md#get_topic_list) 用来查询用户订阅的频道列表。

### 4. 应用场景
频道主要用于一对多发布的场景。服务端和客户端分别集成了云巴的 SDK 后，客户端调用 `subscribe` 订阅某个 Topic，服务端调用`publish`向该 Topic 发布消息，那么，所有订阅了该 Topic 的客户端都会收到消息。


## 别名（Alias）


### 1. 什么是别名

MQTT 里没有别名的概念。云巴的别名（Alias），是为连接云巴的设备绑定账号，避免直接使用内部的 UID。

与 Topic 一样，Alias 也只支持英文、数字和下划线，长度不超过 50 个字符。

### 2. 别名的特点
* 别名与客户端是一一对应的关系。
* 同一个 Appkey 下，不允许存在重复的别名。
* 别名的设置采用的是覆盖的方式，新设置的别名会覆盖旧的别名。
* 将别名设置为空字符串，即可清除别名。
* 目前，云巴支持同一个账号（别名）在不同的终端上登录，但不支持多终端同时登录。

### 3. 相关 API
下面以 JavaScript SDK 为例，介绍一下与别名相关的 API。

* [`set_alias`](js_sdk_api_manual.md#set_alias) 用来设置别名。
* [`get_alias`](js_sdk_api_manual.md#get_alias) 用来获取当前的别名。
* [`get_state`](js_sdk_api_manual.md#get_state) 用来查看某个别名的在线状态。
* [`get_alias_list`](js_sdk_api_manual.md#get_alias_list) 用来获取订阅了某个频道的所有用户的别名。
* [`publish_to_alias`](js_sdk_api_manual.md#publish_to_alias) 向用户别名发送消息。
* [`publish2_to_alias`](js_sdk_api_manual.md#publish2_to_alias) 是 `publish_to_alias` 的升级版本，支持更多参数。

### 4.应用场景
在一对一发布的场景中，不同的客户端集成了云巴的 SDK 后，分别通过调用`set_alias`设置自己的别名，就可以用`publish_to_alias`互相收发消息，进行点对点的通信。


