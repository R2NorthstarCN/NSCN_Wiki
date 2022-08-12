# 在Linux上搭建独立服务器

!> **此页尚未完成编辑**

> 在Linux环境中搭建独立服务器目前可用途径只有使用[Wine](https://www.winehq.org/)来进行，在这一基础上我们也可以使用Docker来构建镜像，预置运行环境，实现即开即用以及多实例与集群管理。

## Docker

[![构建状态](https://northstarcn.coding.net/badges/northstarcn/job/1473182/master/build.svg)](https://northstarcn.coding.net/public-artifacts/northstarcn/northstarcn-dedi-docker/nscn-docker/version/16818666/overview)

在SSH终端输入以下指令即可Pull最新版本NorthStarCN Docker服务端运行镜像

```
docker pull northstarcn-docker.pkg.coding.net/northstarcn/northstarcn-dedi-docker/nscn-docker:1.9.2
```

### 优势

- 比在Windows GUI环境下运行**更具效率**
- 无需额外操作，游戏服务端文件可在**不同服务端实例之间相互隔离，互不影响**
- **统一管理**服务端全局变量与启动项，开服更方便
- **更佳的版本管理与系统环境兼容性**，不必担心Windows系统下的环境配置和版本更新问题
- 镜像经**多重优化**，尽可能降低服务端所需空间与性能损耗
- 服务端进程在因意外退出时，可利用Docker特性优雅地**自动重启**，状态可随时更新

### 快速开始

使用Docker前，你需要在Linux系统中先行下载好精简的TTF2 NorthStarCN服务端

```
wget https://dl.northstar.cool/CDN/Titanfall2/R2N-Dedi-Server.rar
```
并且将服务端内所有文件解压到一个合适的目录中，此处我们将在/home目录下新建一个名为titanfall的文件夹，并且修改文件的读写权限
(希望您已经提前安装好了unrar)
```
mkdir /home/titanfall
mv R2N-Dedi-Server.rar /home/titanfall
unrar x R2N-Dedi-Server.rar
chmod -R 775 /home/titanfall
```
解压完成后，你可以自行删除R2N-Dedi-Server.rar，也可以把它留着

接下来就是pull我们事先已经编译好的镜像了
(我真诚地祈祷您已经安装好了Docker并且配置了一个可用的镜像加速器)

```
docker pull northstarcn-docker.pkg.coding.net/northstarcn/northstarcn-dedi-docker/nscn-docker:1.9.2
```

该镜像内没有预置其他修改游戏内容的MOD

Pull完成后，我们就可以来启动服务端实例了
```markdown
docker run --rm --interactive --pull always --publish 8081:8081/tcp --publish 37015:37015/udp --mount "type=bind,source=/home/titanfall,target=/mnt/titanfall,readonly" --env NS_SERVER_NAME="[CN] This is a Server running on Docker!" aichigua/nscn:1.9.0
```
当然，这样做似乎并不能实现实现多实例与集群管理，尤其是在配置env环境变量时，使用命令行传入十分容易出错，所以，在启动服务端实例前，我们向您推荐Portainer这一Docker管理面板，它将是您管理NorthStarCN服务器的利器

```markdown
docker volume create portainer_data
docker run -d -p (主机端口，任选一个你能开放的TCP端口即可):9000 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce
```
Portainer目前只有英语这一语言可用，如果您对这门语言并不算熟悉，也可以使用ysp的汉化版本，但是这不是最新版本

```markdown
docker run -d --restart=always --name=portainer -p (主机端口，任选一个你能开放的TCP端口即可):9000 -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data 6053537/portainer
```

随后，我们就可以在电脑上打开浏览器访问IP+您刚才在命令行中填写的TCP端口来访问我们的面板了

例如，我的服务器公网IP是1.12.12.12，刚才我填写的TCP端口是27000，则应该访问
```markdown
http://1.12.12.12:27000/
```
首次登录会要求您创建一个面板管理员账户并且配置一个Docker环境，管理员账户按照要求创建即可，Docker环境请选择local，然后点击下一步进入面板

左侧菜单栏


## 不使用Docker

> 在Linux系统上搭建服务器而不使用docker这一利器是相当折腾人的，但是如果你的目的就是学习如何在Linux上使用wine，亦或者你相当享受这种折腾的乐趣，那我也不应该拦着你，对吧。


