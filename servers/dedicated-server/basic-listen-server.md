# 搭建一个基本监听服务器

## 简介

如果您想搭建一个 Northstar 的机本监听服务器的话, 再大厅点击 `私人比赛` 按钮来创建一个大厅服务器. 尽管这允许您创建一个服务器, 其他人可能无法加入您的比赛, 因此您应在路由器或网关交换机中转发以下端口至公网以允许其他人加入.\


**注意：Frp 与 Nps 等**_**端口映射软件不等同于端口转发且无法正常工作**_\


在默认设置下，您需要转发的端口为 `37015` UDP 与 `8081` TCP , 如果您正常设置了端口转发，那么此时您的服务器会显示在大厅的服务器列表中, 并且他人应该可以正常加入您的游戏了.\
![screenshot select private match](https://raw.githubusercontent.com/R2Northstar/NorthstarWiki/main/docs/assets/lobbyprivatematch.png)

## 服务器配置

无论您搭建的是基本监听服务器又或者是专有服务器，您应该都会想自己调点什么参数. 虽然默认的参数是万金油参数, 但更改服务器的名称啊，密码啊，tickrate啊什么的还是需要您亲自动手. 您可以在 `R2Northstar/mods/Northstar.CustomServers/mod/cfg/autoexec_ns_server.cfg` 中更改服务器设置, 更改的参数会在服务器启动时自动加载.\
总而言之，专有服务器的设置与基本监听服务器的参数设置方法没有什么不同.\
服务器启动参数位于 `Titanfall2/ns_startup_args.txt`\
Convars 位于 `R2Northstar/mods/Northstar.CustomServers/mod/cfg/autoexec_ns_server.cfg` 基本监听服务器与专有服务器的唯一区别为基本服务器需要房主一直在房间中.

相关设置请参考 [专有服务器章节](../../hosting-a-server-with-northstar/dedicated-server/#convars)

## 一些小技巧:

您可以在控制台通过以下指令更改地图与模式:

```
sv_cheats 1; script GameRules_ChangeMap( "mp_forwardbase_kodai", "ctf" ); sv_cheats 0
```

将 `mp_forwardbase_kodai` 与 `ctf` 替换为您想要的地图与模式.\
地图列表在 [这里](./#maps).\
游戏模式列表在 [这里](./#gamemodes).

如果有人一直在乱搞模式与地图等设置的话, 将 `ns_private_match_only_host_can_change_settings` 设置为 `2`, 就只有房主能更改了.

您可以将 `ns_private_match_countdown_length` 设置为 `1` 用来跳过开始游戏前的倒计时（车门焊死，谁也别想倒计时的时候跑路）.\
除此之外，您可以将 `ns_private_match_only_host_can_start` 设置为 `1` 就只有你能开始游戏了.
