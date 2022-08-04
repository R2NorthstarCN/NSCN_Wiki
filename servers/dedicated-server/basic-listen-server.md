# 以您的电脑作为主机进行多人游戏

如果您想使用您的电脑在游戏中创建私人比赛房间(下文简称房间)并使其在服务器浏览器中可见，您需要一个公网IP(即Pubilc IP)

在IPv4资源已经枯竭的当下，所有网络供应商(ISP)都会有倾向地减少向家庭/办公宽带用户提供公网IP资源，转而使用NAT(Network address translation，网络地址转换)，这是一个创建网络端口与IP地址映射关系的网络技术(RFC 1918，RFC 2663)，利用该项技术，网络供应商就可以在节省IPv4地址资源的同时向用户提供基本网络服务，但这也会导致用户无法被其他网络终端主动访问，这催生出了STUN(RFC 3489，RFC 5389)等UDP打洞/穿透技术和内网穿透等技术(FRP，NPS)，但是NorthStar在开发之初就未考虑过嵌套网络的情况，**这导致了上述穿透技术皆因协议问题无法使用**

上述情况与国内外IPv4资源保有量有关，根据AS域统计数据显示，美国持有IPv4地址最多，每个网民平均可分配近6个地址，而中国、巴西、墨西哥等发展中国家网民人均仅有不到半个IPv4地址，北美与欧洲充足的网络资源导致这些地区的开发者在设计程序时几乎没有考虑过高嵌套网络环境的情况，同时，上述情况导致了国内三大运营商对家庭/办公宽带用户所分配的公网IP资源进一步缩减

国内联通和电信家庭宽带用户可以尝试向客服电话咨询，询问其是否可以为您分配一个动态的公网IPv4地址，最终能否分配将取决于当地运营商政策和客服和稀泥的程度，移动家宽用户不会分配到公网IPv4地址，询问移动客服通常会建议您订购商业宽带

> 在IPv6加速铺开的当下,NAT也会逐渐被淘汰，IPv6巨大的地址池足以解决IPv4时代地址不足的问题

在向网络供应商索要到一个公网IP后，由于国内运营商在办理宽带时为您提供的光猫等接入设备限制颇多，且通常性能低下，所以您需要一个额外的路由器，并将光猫的工作模式由拨号网关转换至网桥(Router ==> Bridge)，将路由器Wan口接至光猫的Lan口下，并使用路由器进行PPPoE拨号

在默认配置文件下，您需要在路由器端口转发设置的端口为**UDP** `37015` 与**TCP** `8081`，您必须至少拥有一个可用的TCP和UDP端口，端口号可根据您的网络情况自行修改，下文将使用**UDP** `37015` 与**TCP** `8081`两个端口作为示范

## 准备工作

### 修改服务端配置文件

* `.\ns_startup_args.txt` 
  包含游戏的 [启动项](./#startup-arguments)
* `. R2Northstar\mods\Northstar.CustomServers\mod.json` 
  保存着 [全局变量](./#convars) 的默认参数
* `. R2Northstar\mods\Northstar.CustomServers\mod\cfg\autoexec_ns_server.cfg` 
  保存着 [全局变量](./#convars) 的自定义参数，该文件在游戏加载时将覆盖上方[全局变量](./#convars)的默认参数

相关设置请参考 [专有服务器章节](../../hosting-a-server-with-northstar/dedicated-server/#convars)

### 我是否拥有一个公网IP？

在国内网络环境下，判断自己是否拥有公网IP最简单的办法通常是通过查看路由器拨号Wan口IP与您访问互联网所使用的IP是否一致

此处使用小米AX3600路由器举例

在浏览器访问路由器管理后台，切换到上网模式设置页

查看拨号信息中的分配到的IP地址

浏览器访问[IPIP](http://myip.ipip.net/)，将拨号信息中的分配到的IP地址与浏览器中所显示的IP进行比对

若IP结果均一致，且非192.168.0.0/16，172.16.0.0/16，10.0.0.0/8等局域网私有IP，则您应该已经成功分配到了一个公网IP


### 端口转发

在路由器管理后台找到端口转发管理页(部分品牌路由器也将该功能称作为虚拟服务器)

此处使用小米AX3600路由器举例

首先确认您要用来进行多人游戏的PC的局域网IP

您的路由通常会启动DHCP服务器为您自动分配一个IP

在您的电脑上打开任务管理器，点击性能详细页

点击您的网卡，查看路由器DHCP服务器为您分配的局域网IP

此处该PC的IP地址为`192.168.31.131`

回到路由器管理后台，点击添加端口转发规则

在默认配置下，您需要转发的端口如下

* `37015` (UDP)

![UDP-PORT-FORWARDING](https://wiki.northstar.cool/assets/UDP-PORT-FORWARDING.png)

* `8081` (TCP)

![TCP-PORT-FORWARDING](https://wiki.northstar.cool/assets/TCP-PORT-FORWARDING.png)

IP地址填写PC在局域网中分配到的IP地址，此处为`192.168.31.131`

完成创建转发规则后，点击保存&生效

### Windows防火墙

若您的PC等设备在路由器的下一层，而非直接暴露在公网中，那么我们推荐您直接关闭Windows系统自带的防火墙

若您的PC等设备直接暴露在公网中，那么您应该保持防火墙系统开启，并保持敏感服务端口关闭

若您启用了Windows防火墙，您需要在防火墙中允许 `NorthstarLauncher.exe` 访问互联网. 在默认情况下，系统应该会在您第一次运行`NorthstarLauncher.exe`时弹出询问窗口，请点击允许

如果您不小心点了拒绝（取消）按钮，手动设置的过程如下

* 打开 `Windows Defender 防火墙`
* 选择 `允许应用或功能通过 Windows Defender 防火墙`
* 点击 `允许其他应用`
* 点击 `浏览`
* 找到 `NorthStarCNLauncher.exe` 并勾选
* 点击 `添加`

### 环境检查

在完成上述步骤后，您已经可以使用您的电脑开启一个公开多人房间进行游玩了，在这之前，您也可以进行一次环境检查，以防在上述步骤中出现您未注意到的操作失误

在开启公开多人房间后，您可以使用网页端的[服务器浏览器](https://stats.northstar.cool)查看您的房间是否已经存在于浏览器中.

若房间长时间未出现在浏览器中，您可以先在PC上打开命令提示符(CMD)，分别输入`netstat -ano | findstr "37015"`和`netstat -ano | findstr "8081"`来查看进程是否在本机上正确监听这两个端口

![37015](https://wiki.northstar.cool/assets/37015.png)

![8081](https://wiki.northstar.cool/assets/8081.png)

若输入查询指令后并无结果返回，则应首先检查您是否已经关闭防火墙或是否已经添加防火墙相对应的允许规则

若您已经完成了防火墙的相关操作，则应是您的配置文件没有正确配置，导致游戏进程并未在监听**UDP** `37015` 与**TCP** `8081`，而是在监听其他端口，修改您的配置文件至正确的端口号即可

若您确认PC网络端口配置正确后，您还可以通过第三方网站提供的端口验通工具来确认您所开放的端口在互联网可以访问

此处我们使用[IPVoid](https://www.ipvoid.com/port-scan/)来检查您的TCP端口是否可以访问(上文已经提到，默认为 `8081`)

![SCAN-8081](https://wiki.northstar.cool/assets/SCAN-8081.png)

然后使用[IPVoid-UDP](https://www.ipvoid.com/udp-port-scan/)来检查您的UDP端口是否可以访问(上文已经提到，默认为 `37015`)

![SCAN-37015](https://wiki.northstar.cool/assets/SCAN-37015.png)

在确认所有端口均可访问，配置文件设置正确后，您就可以开启游戏，并等待其他玩家进入您的房间了

## 实用指令

您可以在控制台通过以下指令更改地图与模式:

```
sv_cheats 1     #更改地图前需要先启用作弊
script GameRules_ChangeMap( "mp_forwardbase_kodai", "ctf" )
sv_cheats 0      #更改完成后关闭作弊
```

您可以将 `mp_forwardbase_kodai` 与 `ctf` 替换为您想更改为的地图与模式 

您可以在控制台输入`ns_private_match_only_host_can_change_settings 2`，之后只有房主才有权限更改房间参数

您可以将 `ns_private_match_countdown_length` 设置为 `1` 用来跳过开始游戏前的倒计时
您可以将 `ns_private_match_only_host_can_start` 设置为 `1` ，只有只有房主才有权限开始游戏
