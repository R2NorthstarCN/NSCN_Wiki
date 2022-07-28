# 序言

## 什么是NorthStarCN?

`NorthStar` 是一个开放式的TTF2 MOD与服务器框架，它能够让玩家们在游戏中加载预先编写好的MOD，架设自己的TTF2自定义服务器。对于一般路过玩家而言，使用NorthStar能够在游戏内启用功能增强MOD，在其他玩家架设的自定义服务器房间游玩，而不需要经过Respawn的服务器.

`NorthStarCN` 则是基于NorthStar这一框架，为了最大限度地照顾国内玩家的游戏体验，对NorthStar进行了大量本地化修改与部署的一个项目分支。该项目目前由一部分国内TTF2爱好者维护.


----

`NorthStar` 与 `NorthStarCN` 均设置了 `MIT` 开源许可证，该许可证允许和要求:

1.你可以自由地使用、复制、修改、合并、出版发行、分发、再授权及贩售软件及软件的副本

2.你可以自由地根据程序的需要修改授权条款为适当的内容

3.你需要在软件和软件的所有副本中设置版权声明和 `MIT` 开源许可证

----


许可证全文如下:
```markdown
MIT License

Copyright (c) 2021 R2NorthStarCN

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

## NorthStarCN与战地1，CSGO的运作模式有何区别?

在`BattleField 1`中，玩家可以向EA支付租金以租借由EA管理的游戏服务端实例，服务器基础设施则由AWS承担

玩家在租借了服务端实例后，可以在租借时间内自由更改服务端的游戏模式，地图，游戏参数和部分运行参数等，在此期间内玩家只拥有服务端的使用权，而没有所有权

因为服务端实例均**由EA直接管理**，所以玩家在自定义服务器中游戏也可以获得经验值等

----

在`CSGO`中，Valve提供的游戏服务器由Valve管理，服务器基础设施由Azure承担

玩家也可以通过Steam网络，以某一个玩家的电脑作为主机，通过P2P的模式进行自定义在线对战

而社区服务器则需要玩家自行购买服务器基础设施，自行安装相关环境并设置游戏服务端，同时还需要使用一个完成5美元验证和绑定了手机号的Steam账号申请一个API Token才能让服务器出现在社区服列表中，若无API Token，服务端将只能在局域网中连接

在此过程中，由于服务器**受到Valve的验证和间接管理**，所以在服务器中默认会启用Valve Anti Cheat，玩家数据可也在服务器中与官服同步

Valve Anti Cheat可由服务器管理者自行关闭，玩家数据也可以通过第三方插件进行更改(这是违反Valve TOS的行为)

----

`NorthStarCN`则是一个完全独立的平台，玩家的等级和物品数据并不会和Respawn处同步，而是完全隔离

在NorthStarCN平台游玩需要您在后台运行Origin，这是为了防止盗版游戏损害Respawn工作室的利益，同时也是为了方便社区的反作弊和管理工作

与CSGO相似，NorthStarCN在服务器列表中提供了部分由我们直接管理的服务器实例供您游玩，服务器基础设施由我们自行承担

同时，您也可以自行购买服务器基础设施，自行安装相关环境并设置游戏服务端，并将服务器添加到我们的服务器列表中，这些服务器则属于第三方服务器

请您注意，NorthStarCN并**无权限对第三方服务器进行直接管理**，我们最多能做的事也只是让某个服务器不能出现在我们的列表中

所以，当您在第三方服务器中遇到问题的时候，您需要自行联系服务器所有者进行沟通以解决问题，我们爱莫能助



