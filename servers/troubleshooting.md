# Document is empty

`[error] Failed reading masterserver authentification response: encountered parse error 'The document is empty.'`

主服务器需要与您的专有服务器进行验证信息的交换以将您的服务器信息添加至服务器列表中，该错误说明主服务器无法与您的专有服务器的 ` TCP ` 端口进行连接.

造成此错误的可能性有很多，不过您可以从外部网络验证服务器的可达性来缩小排障范围.

## 检查服务器是否可达

您可以使用浏览器确认您的服务器是否可达.

example : `http://{server_ip}:{server_tcp_port}/verify` 将会显示以下文本 `I am a northstar server!`

在检查时您的服务器 **必须** 正在运行.

## 如果在使用外部IP的情况下服务器可达

### 您的游戏版本已过时

请确保您的服务端为最新版本.

### MasterServer 下线

请在各分支的公告页面确认主服务器状态.

### 端口错误

您的服务端应该被配置为监听一个特定的端口.

Masterserver 需要与这个 TCP 端口进行通讯.

### 其他服务占用了此端口

关闭其他服务器以缩小问题范围

这通常没有帮助，但可以避免检查错误的服务器。

## 如公网无法访问服务器

检查您的服务器是否可以在内网访问 (通常为 `192.168.x.x`)

### 防火墙阻止了tcp连接
在某些情况下，您的防火墙或者反病毒软件可能会阻止北极星的连接.
如遇到这种情况，我们建议手动添加放行规则.
我们 ***不推荐*** 通过禁用防火墙来解决此问题.

## 如公网无法访问服务器但内网可以

### 路由器怕配置错误

如公网无法访问服务器但内网可以，那么很大的可能是你的路由器 NAT表 (端口映射/DMZ) 没有正确配置.

### CGNAT

参考 [CGNAT](https://r2northstar.gitbook.io/r2northstar-wiki/hosting-a-server-with-northstar/prerequisites#cgnat)

## 如果服务器在公 / 内 汪均无法连接

请检查本地回环链路 `http://127.0.0.1:{server_tcp_port}/verify`

### 其他程序占用了此端口

其他程序监听了和北极星服务器相同的 tcp 端口.

您可以使用 `netstat -a -b` 来确定是什么程序

更改 TCP 监听端口通常能解决此问题.

### 服务器使用了错误的端口

你可以使用 `netstat -a -b` 命令来确认服务器所使用的端口
