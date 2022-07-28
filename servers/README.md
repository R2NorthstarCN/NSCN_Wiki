# 关于服务器
## 什么是主服务器(MasterServer)?
玩家在使用服务器浏览器查看服务器列表时候，需要连接到主服务器（也就是MasterServer）来获取服务器列表信息。
此外玩家搭建的服务器也需要连接主服务器来报告自身服务器信息，以供其他玩家看到。
主服务器并不提供游玩服务，主服务器会获取玩家信息但不会进行存储或用于其他目的。

## 关于NorthStarCN 的官方服务器
NorthStarCN 团队并没有提供 以NorthStarCN官方负责的 可游玩的服务器房间。属于NorthStarCN官方团队维护的服务器仅有MasterServer，其他可供游玩的服务器由玩家提供或者NorthStarCN团队成员自发提供。
因此若游玩服务器出现问题应该先与服务器管理者取得联系而非NorthStatCN团队。

## 服务器存在各种问题？
这作为一个刚发布没多久的框架来说蛮正常的，我们也在努力积极解决。如果你遇到了游玩问题请尝试重新连接重新启动联系服务器管理员。
若想要为NorthStarCN提交问题或者bug请在github项目发布仓库页提交issues。

## 我想要连接获取 外服/NorthStar原版 服务器列表
你只需要修改/R2Northstar/mods/Northstar.Client/mod/cfg/autoexec_ns_client.cfg文件中的`ns_masterserver_hostname`,修改为：
```
ns_masterserver_hostname "https://northstar.tf"
```
保存，重启游戏即可，无需更换客户端