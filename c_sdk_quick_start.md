#Yunba C 快速入门
## 注册开发者账号

打开 [云巴官方网站](https://yunba.io)， 点击注册创建账号。

![create_accout.png](https://raw.githubusercontent.com/yunba/docs/master/image/productpng_portal_register_account.png)

## 创建应用
注册账号成功跳转到我的应用界面，点击我的应用 --> 创建新应用，输入应用名称和包名

![productpng_portal_creat_application.png](https://raw.githubusercontent.com/yunba/docs/master/image/productpng_portal_creat_app.png)


##从哪里获得 SDK

你可以使用下面命令去获得 SDK

打开 [开发者资源页面](https://yunba.io/developers/) 下载 C SDK。

##怎么开始
###1.添加 lib 以及 header 到 Makefile：

```c
INCLUDEPATH = -I/home/yunba/test/yunba-c-sdk/install/include
LIBPATH = -L/home/yunba/test/yunba-c-sdk/install/lib
```

其中/home/yunba/test/yunba-c-sdk/install 是你的 yunba SDK 目录。

###2.在应用中添加 yunba 服务。
在你的代码中应用包含:

```c
#include "yunba.h"
```

在入口函数中添加 yunba 服务初始化：
```c
REG_info my_reg_info;
int res = MQTTClient_setup_with_appkey(appkey, &my_reg_info);
if (res < 0) {
	printf("can't get info");
	return -1;
}
```
上面 appkey 为用户注册获得的 appkey。

获得url.
```c
char url[200];
MQTTClient_get_host(appkey, url);
```
url用来保存获得url.


接下来,
```c
MQTTClient_connectOptions conn_opts = MQTTClient_connectOptions_initializer;
rc = MQTTClient_create(&client, url, my_reg_info.client_id, MQTTCLIENT_PERSISTENCE_NONE, NULL);

rc = MQTTClient_setCallbacks(client, NULL, NULL, messageArrived, NULL, extendedCmdArrive);
```
连接到服务器。

```c
conn_opts.username = my_reg_info.username;
conn_opts.password = my_reg_info.password;
if (MQTTClient_connect(*client, opts) != 0) {
	return -1;
}
```

订阅你的频道

```c
rc = MQTTClient_subscribe(client, "your_channel");
```

其中messageArrived， extendedCmdArrive为回调函数。

下面函数处理status, get alias get-topic等扩展命令。

```c
int extendedCmdArrive(void *context, EXTED_CMD cmd, int status, int ret_string_len, char *ret_string)
{
  //处理接收到的扩展命令返回。
}

int messageArrived(void* context, char* topicName, int topicLen, MQTTClient_message* m)
{
  //处理topic以及推送的消息内容。
}
```  

当你的程序退出时，不要忘记使用：

```c
MQTTClient_destroy(&client)
```

## 例子代码

在 C SDK 目录下 src/samples/stdinpub_present.c 。


