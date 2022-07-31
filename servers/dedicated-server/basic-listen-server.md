# 以您的电脑作为主机进行多人游戏

如果您想使用您的电脑创建


**注意：FRP 与 NPS 等内网穿透/代理因协议问题，无法在该情景使用**_ 


在默认设置下，您需要转发的端口为 `37015` UDP 与 `8081` TCP , 如果您正常设置了端口转发，那么此时您的服务器会显示在大厅的服务器列表中, 并且他人应该可以正常加入您的游戏了. 
![screenshot select private match](https://raw.githubusercontent.com/R2Northstar/NorthstarWiki/main/docs/assets/lobbyprivatematch.png)

## 准备工作


### 端口转发

通过网页控制界面访问您的路由器并转到端口转发子菜单中

* `37015` (UDP) 用于处理游戏逻辑
* `8081` (TCP) 用于与主服务器验证以在主服务器中显示您的服务器

本地IP地址为您跑着服务器的那台pc的IP地址.

### 防火墙

您需要在防火墙中允许 `NorthstarLauncher.exe` 连接到互联网. 在默认情况下，系统应该会在您第一次运行时弹出窗口，记得允许.

如果您不小心点了拒绝（取消）按钮，那么手动设置的过程如下.

* 打开 `Windows Defender 防火墙`
* 选择 `允许应用或功能通过 Windows Defender 防火墙`
* 点击`允许其他应用`
* 点击`浏览`
* 定位到 `NorthStarCNLauncher.exe` 并勾选
* 点击`添加`

### 最终检查

如果您想要检查设置是否正确，随便开启一个 Notrhstar 的服务器. 其他的 Northstar 用户应该可以在服务器浏览器中发现并加入您的服务器. 
您也可以使用网页端的 [服务器列表](https://stats.northstar.cool) 去查找您的服务器.

您还可以使用 [IPVoid](https://www.ipvoid.com/port-scan/) 来确认您的TCP端口 (通常为 `8081`) 是否正常 来确认您的服务器是否已经启动.

![Example check](https://raw.githubusercontent.com/R2Northstar/NorthstarWiki/main/docs/images/portforwarding-testing.png)

![Working portforwarding for the TCP port](https://raw.githubusercontent.com/R2Northstar/NorthstarWiki/main/docs/images/portforwarding-working.png)


## 服务器配置

无论您搭建的是基本监听服务器又或者是专有服务器，您应该都会想自己调点什么参数. 虽然默认的参数是万金油参数, 但更改服务器的名称啊，密码啊，tickrate啊什么的还是需要您亲自动手. 您可以在 `R2Northstar/mods/Northstar.CustomServers/mod/cfg/autoexec_ns_server.cfg` 中更改服务器设置, 更改的参数会在服务器启动时自动加载. 
总而言之，专有服务器的设置与基本监听服务器的参数设置方法没有什么不同. 
服务器启动参数位于 `Titanfall2/ns_startup_args.txt` 
Convars 位于 `R2Northstar/mods/Northstar.CustomServers/mod/cfg/autoexec_ns_server.cfg` 基本监听服务器与专有服务器的唯一区别为基本服务器需要房主一直在房间中.

相关设置请参考 [专有服务器章节](../../hosting-a-server-with-northstar/dedicated-server/#convars)

## 实用指令

您可以在控制台通过以下指令更改地图与模式:

```
sv_cheats 1     #更改地图前需要先启用作弊
script GameRules_ChangeMap( "mp_forwardbase_kodai", "ctf" )
sv_cheats 0      #更改完成后关闭作弊
```

将 `mp_forwardbase_kodai` 与 `ctf` 替换为您想要的地图与模式. 
地图列表在 [这里](./#maps). 
游戏模式列表在 [这里](./#gamemodes).

如果有人一直在乱搞模式与地图等设置的话, 将 `ns_private_match_only_host_can_change_settings` 设置为 `2`, 就只有房主能更改了.

您可以将 `ns_private_match_countdown_length` 设置为 `1` 用来跳过开始游戏前的倒计时（车门焊死，谁也别想倒计时的时候跑路）. 
除此之外，您可以将 `ns_private_match_only_host_can_start` 设置为 `1` 就只有你能开始游戏了.
