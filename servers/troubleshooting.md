# Document is empty

`[error] Failed reading masterserver authentification response: encountered parse error 'The document is empty.'`

主服务器需要与您的专有服务器进行验证信息的交换以将您的服务器信息添加至服务器列表中，该错误说明主服务器无法与您的专有服务器的 ` TCP ` 端口进行连接.

造成此错误的可能性有很多，不过您可以从外部网络验证服务器的可达性来缩小排障范围.

## 检查服务器是否可达

您可以使用浏览器确认您的服务器是否可达.

example : `http://{server_ip}:{server_tcp_port}/verify` 将会显示以下文本 `I am a northstar server!`

在检查时您的服务器 **必须** 正在运行.

请检查本地回环链路 `http://127.0.0.1:{server_tcp_port}/verify`
