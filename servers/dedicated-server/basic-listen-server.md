# 以您的电脑作为主机进行多人游戏

如果您想使用您的电脑在游戏中创建私人比赛房间并使其在服务器浏览器中可见，您需要一个公网IP(即Pubilc IP)

在IPv4资源已经枯竭的当下，所有网络供应商(ISP)都会有倾向地减少向家庭/办公宽带用户提供公网IP资源，转而使用NAT(Network address translation，网络地址转换)，这是一个创建网络端口与IP地址映射关系的网络技术(RFC 1918，RFC 2663)，利用该项技术，网络供应商就可以在节省IPv4地址资源的同时向用户提供基本网络服务，但这也会导致用户无法被其他网络终端主动访问，这催生出了STUN(RFC 3489，RFC 5389)等UDP打洞/穿透技术和内网穿透等技术(FRP，NPS)，但是NorthStar在开发之初就未考虑过嵌套网络的情况，**这导致了上述穿透技术皆因协议问题无法使用**

上述情况与国内外IPv4资源保有量有关，根据AS统计数据显示，美国持有IPv4地址最多，每个网民平均可分配近6个地址，而中国、巴西、墨西哥等发展中国家网民人均仅有不到半个IPv4地址，北美与欧洲充足的网络资源导致这些地区的开发者在设计程序时几乎没有考虑过高嵌套网络环境的情况，同时，上述情况导致了国内三大运营商对家庭/办公宽带用户所分配的公网IP资源进一步缩减

国内联通和电信家庭宽带用户可以向客服电话咨询，询问其是否可以为您分配一个动态的公网IP地址，最终能否分配将取决于当地运营商政策和客服和稀泥的程度，移动家宽用户不会分配到公网公网IP地址，询问移动客服通常会建议您订购商业宽带

> 在IPv6加速铺开的当下,NAT也会逐渐被淘汰，IPv6巨大的地址池足以解决IPv4时代地址不足的问题

在向网络供应商索要到一个公网IP后，由于国内运营商在办理宽带时为您提供的光猫等接入设备限制颇多且通常性能低下，所以您需要一个额外的路由器，并将光猫的工作模式由拨号网关转换至网桥(Router ==> Bridge)，将路由器Wan口接至光猫的Lan口下，并使用路由器进行PPPoE拨号

在默认设置下，您需要在路由器端口转发设置的端口为**UDP** `37015` 与**TCP** `8081` 

## 准备工作

### 我是否拥有一个公网IP？



### 端口转发



* `37015` (UDP)
* `8081` (TCP)



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
