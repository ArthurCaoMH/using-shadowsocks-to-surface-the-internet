# using-shadowsocks-to-surface-the-internet
用shadowsocks科学上网
一、关于服务器的购买和配置请参考：

[自己搭建翻墙服务器 ](http://jiyiren.github.io/2016/10/06/fanqiang/)

二、shadowsocks服务端的安装

因为在搬瓦工购买的服务器仅支持centos服务端的shsdowsocks的安装，因此要在Ubuntu安装，需要一些命令来实现：

1.使用的是pip安装

apt-get install python-pip
pip install shadowsocks 

 2.配置多用户的使用端口号和密码——创建并编辑配置文件：

注意如果使用root账户登陆则不需要加sudo

sudo vi /etc/shadowsocks.json


以下是shadowsocks.json文件需要添加的内容

{
	"server":"ip", #填入你的IP地址
	"local_address": "127.0.0.1",
	"local_port":1080, 
	"port_password": 
		{ 
			"8381": "foobar1", #端口号，密码
			"8382": "foobar2", 
			"8383": "foobar3", 
			"8384": "foobar4" #注意这里没有逗号 
		},
	"timeout":300, #超时限制为3s 
	"method":"rc4-md5", #加密方式 
	"fast_open": false #关闭快速打开 
}

三、接下来就是客户端shadowsocks的安装了

这篇文章写的很好，[各个系统服务端shadowsocks的安装（mac/win/linux/android/ios）](http://www.jeyzhang.com/how-to-install-and-setup-shadowsocks-client-in-different-os.html)

目前iOS端没有客户端，而且暂时没有找到免费的替代品，有一个AppStore叫做wingy的软件需要收费8元，应该可以做替代，但是没有测试过，感兴趣的朋友们可以自己去尝试。

但是其中的下载链接已经失效，可以直接点击下面的链接到shadowsocks的github上下载

[1.Windows](https://github.com/shadowsocks/shadowsocks-windows/releases)

[2.Android](https://github.com/shadowsocks/shadowsocks-android/releases)

[3.mac](https://github.com/shadowsocks/ShadowsocksX-NG/releases)

Ubuntu下直接采用安装命令：

sudo add-apt-repository ppa:hzwhuang/ss-qt5

sudo apt-get update

sudo apt-get install shadowsocks-qt5

至此，就可以科学上网了！
