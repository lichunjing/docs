# 运行 Yunba C Demo

本文介绍如何运行 Yunba C SDK 中的其中一个 Demo 示例程序。

本文涉及的运行环境如下：
- Windows
	* Windows 10 Pro
	* Microsoft Visual Studio 2015
	* YunBa C SDK
- Linux & OS X
	* GNU Make,gcc
	* GNU bash
	* OpenSSL

## 准备工作

###1. 下载云巴 C SDK
这里使用的是云巴 C SDK 的 feature/windows_building 下的工程，这个工程是在 Visual Studio 2015 下 build 的。
可打开[其 GitHub 页](https://github.com/yunba/yunba-c-sdk/tree/feature/windows_building)，下载 Zip 文件。

![cpng_demo_directory.png](https://raw.githubusercontent.com/yunba/docs/master/image/cpng_demo_directory.png)

###2. 注册云巴开发者账号
打开 [云巴官方网站](https://yunba.io)，点击右上角的“注册”按钮创建账号。  

## 详细步骤

### - Windows

###1. 在云巴 Portal 上创建新应用
请参考 [运行 Yunba Android Demo](android_demo_quick_start.md) 
一文中的该步骤的做法，获得一个 AppKey。

###2. 打开工程
本文以 [stdoutsub](https://github.com/yunba/yunba-c-sdk/tree/feature/windows_building/Windows%20Build/stdoutsub) 工程为例，
演示 C SDK 的使用。
解压之前下载的 Zip 文件，在 Visual Studio 2015 中打开“Paho C MQTT APIs.sln”工程。如图：

![cpng_demo_open_sln.png](https://raw.githubusercontent.com/yunba/docs/master/image/cpng_demo_open_sln.png)

右击 stdoutsub 工程，选择“设为启动项目”。

![cpng_demo_vs.png](https://raw.githubusercontent.com/yunba/docs/master/image/cpng_demo_vs.png)

###3. 输入参数
修改 [stdoutsub](https://github.com/yunba/yunba-c-sdk/blob/feature/windows_building/src/samples/stdoutsub.c) 中的 main 函数的参数输入部分。

为了便于演示，我们将原程序的部分语句注释掉，对 AppKey 和 Topic 直接赋值。如下所示：

```C
int main(int argc, char** argv)
{
	//MQTTClient client;
//	MQTTClient_connectOptions conn_opts = MQTTClient_connectOptions_initializer;
	char topic[200] = "";
	char* buffer = NULL;
	int rc = 0;
	char url[100];
	char broker[100];

//	if (argc < 2)       
//		usage();
	
//	getopts(argc, argv);
	
//	sprintf(url, "%s:%s", opts.host, opts.port);
//  if (opts.verbose)
//		printf("URL is %s\n", url);

	char a[200] = "XXXXXXXXXXXXXXXX";   //填上你在步骤 1 中申请到的 AppKey。
	char b[200] = "news";               //填上 Topic 的名称，如，“news”。
//	strcpy(topic, argv[1]);

	opts.appkey = a;                    //给 opt.appkey 赋值
	strcpy(topic,b);                    //给 topic 赋值
	
	printf("Using topic %s\n", topic);
	
	//其他代码略。
	
```
###4. 运行程序
修改好后，直接运行。可以看到控制台的打印信息。
在控制台直接输入需要发送的信息，回车，即可向设定的 Topic 发送信息，如，发送一条“good news”。
在这个例子中，设定的 Topic 是“news”，且 C 客户端本身也订阅了“news”。因此，发出的消息自己也可以收到。
如果使用同一个 AppKey 的另一个客户端（如，Portal）向“news”发送消息，C 客户端也会收到，控制台会将收到的消息打印出来。

![cpng_demo_console.png](https://raw.githubusercontent.com/yunba/docs/master/image/cpng_demo_console.png)

### - Linux & OS X

###1. make
使用 make 来生成可执行文件，本 demo 包含一份 makefile，在 makefile 所在的路径下执行`make`，成功后会在 /yunba-c-sdk-master/build/output/sample/ 下生成 stdouta\_demo 和 stdinpub\_present 两个可执行文件。*注意在使用 make 的时候如果你的电脑有多于一个的 C 标准库，就需要在 make 的时候加上`-stdlib=libstdc++`来选择标准库，否则会产生错误。*

###2. 执行
使用 bash 或其它命令行工具进入可执行文件的路径，然后执行该程序。

###3. 'stdinpub\_present'的使用
stdinpub\_present 的使用方法是 `stdinpub\_present <topic name> --appkey <appkey> --deviceid <deviceid> --retained --qos <qos> --delimiter <delimiter>`。`<topic name>`和`<appkey>`是必须的，其余为可选项，不填的话使用默认值，其中`<deviceid>`可以使用已有的，没有的话系统会自动给您分配一个，用以在后台区分用户；`retained`默认关闭，打开后可以收到自己发送的消息；`<delimiter>`为分隔符，打出该字符后会发送该字符前的字符，默认为`\n`。

	- 示例：`./stdinpub_present test --appkey XXXXXXXXXXXXXXXXXXXXXXXX --retained`

###4. 结果
运行成功后会订阅该频道，并向该频道发送一个消息，您可以在 Portal 中看到。还会向服务器询问该 topic 的 aliaslist、topic 和 status 的信息，获取完以后当您按回车之后会发送在分割符`<delimiter>`之前的字符。

###5. 'stdouta\_demo'的使用
stdouta\_demo 的使用方法与 stdinpub\_present 类似，只是没有了向服务器查询的过程。

	- 示例：`./stdouta_demo tttest --appkey XXXXXXXXXXXXXXXXXXXXXXXX`
