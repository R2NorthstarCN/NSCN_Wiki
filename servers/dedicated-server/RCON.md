# RCON(远程控制台)

!> RCON尚未被NorthStar正式收录到主分支中，且RCON特性目前尚还在开发测试阶段，以下信息只在目前的RCON测试分支版本中有效

RCON功能会占用与您游戏服务器UDP端口相同端口号的TCP端口，默认情况下这个端口是 `37015`

RCON功能目前仅在独立服务端上启用

您必须在全局变量`rcon_password`中为RCON功能设置一个长度大于8的密码，否则RCON功能不会启用

在独立服务端启动后，如果控制台中有 `Remote server access initialised` 的信息输出，则RCON功能已启用

有关RCON的更多特性，您可以访问[Valve的官方文档](https://developer.valvesoftware.com/wiki/Source_RCON_Protocol)查看

[RCON PR](https://github.com/R2Northstar/NorthstarLauncher/pull/100)

[cpdt's rust based RCON client](https://github.com/cpdt/northstar-rcon-client)

[RCON PR download guide](https://github.com/R2Northstar/NorthstarLauncher/pull/100#issuecomment-1188877309)

[GeckoEidechse/northstar-dedicated-rcon](https://github.com/GeckoEidechse/northstar-dedicated-rcon)