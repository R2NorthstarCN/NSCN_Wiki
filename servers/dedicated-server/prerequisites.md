# 准备工作



## 端口转发

通过网页控制界面访问您的路由器并转到端口转发子菜单中

* `37015` (UDP) 用于处理游戏逻辑
* `8081` (TCP) 用于与主服务器验证以在主服务器中显示您的服务器

本地IP地址为您跑着服务器的那台pc的IP地址.

## 防火墙

您需要在防火墙中允许 `NorthstarLauncher.exe` 连接到互联网. 在默认情况下，系统应该会在您第一次运行时弹出窗口，记得允许.

如果您不小心点了拒绝（取消）按钮，那么手动设置的过程如下.

* 打开 `Windows Defender 防火墙`
* 选择 `允许应用或功能通过 Windows Defender 防火墙`
* 点击允许其他应用
* 点击浏览
* 定位到 NorthstarLauncher.exe 选择它
* 单击添加

## 最终检查

如果您想要检查设置是否正确，随便开启一个 Notrhstar 的服务器. 其他的 Northstar 用户应该可以在服务器浏览器中发现并加入您的服务器.\
您也可以使用网页端的 [服务器列表](https://stats.northstar.cool) 去查找您的服务器.

您还可以使用 [第三方网站](https://www.ipfingerprints.com/portscan.php) 来确认您的TCP端口 (通常为 `8081`) 是否正常 来确认您的服务器是否已经启动.

![Example check](https://raw.githubusercontent.com/R2Northstar/NorthstarWiki/main/docs/images/portforwarding-testing.png)

![Working portforwarding for the TCP port](https://raw.githubusercontent.com/R2Northstar/NorthstarWiki/main/docs/images/portforwarding-working.png)

这样的测试只适用于 TCP 端口 因为 UDP 与 Northstar 的工作方式与之不同.

注意在默认状态下，您的服务器名字为 `Unnamed Northstar Server`. 请注意去更改他.
