# Mac Connect to Linux
- 实现mac和Linux系统之间的即时通讯
## Method
- ssh
## step
1. linux
```
# 添加用户
$ sudo useradd -m name
# 设置密码
$ sudo passwd name
# 设置权限
$ sudo usermod -s /bin/basn name
# 安装ssh服务端
$ sudo apt-get install openssh-server
```
2. mac
```
$ ssh name@host
```
3. linux
```
$ mesg y
$ write name
```
## Problem
不知道为什么，Linux可以很顺利地向mac发送消息，但是mac那边死活就是没办法向Linux发消息，双方的mesg都已经设置成yes，但是还是提示
```
write: linux_user has messages disabled
```
