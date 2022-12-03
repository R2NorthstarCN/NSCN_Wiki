# 在Linux上搭建独立服务器

!> **此页尚未完成编辑**

> 在Linux环境中搭建独立服务器目前可用途径只有使用[Wine](https://www.winehq.org/)来进行，在这一基础上我们也可以使用Docker来构建镜像，预置运行环境，实现即开即用以及多实例与集群管理。

## Docker

[![构建状态](https://img.shields.io/badge/docker%20build-passing-brightgreen)](https://northstarcn.coding.net/public-artifacts/northstarcn/northstarcn-dedi-docker/nscn-docker/version/19159335/overview)

在SSH终端输入以下指令即可Pull最新版本NorthStarCN Docker服务端运行镜像

```
docker pull northstarcn-docker.pkg.coding.net/northstarcn/northstarcn-dedi-docker/nscn-docker:latest
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
wget https://dl.d3-3109.cc/d/TTF2/R2N-Dedi-Server.rar
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

```
docker pull northstarcn-docker.pkg.coding.net/northstarcn/northstarcn-dedi-docker/nscn-docker:latest
```

Pull完成后，我们就可以来启动服务端实例了
```markdown
docker run --rm --interactive --pull always --publish 37006:37006/tcp --publish 37005:37005/udp --mount "type=bind,source=/home/titanfall,target=/mnt/titanfall,readonly" --env "NS_SERVER_NAME=[D3] 20\\u4eba TTDM \\u4f60\\u8bf4\\u5f97\\u5bf9\\u4f46\\u662f\\u4f60\\u8bf4\\u5f97\\u5bf9" "NS_SERVER_DESC=\\u6211\\u4e5f\\u4e0d\\u77e5\\u9053\\u4e3a\\u4ec0\\u4e48\\u4f60\\u4eec\\u90a3\\u4e48\\u559c\\u6b22\\u73a9\\u0032\\u0030\\u4eba\\u0054\\u0054\\u0044\\u004d" "NS_PORT=37005" "NS_PORT_AUTH=37006" "NS_EXTRA_ARGUMENTS=+ns_server_reg_token xxxxxxxxxxxxxxxxxxxxxxxxxxxx +net_compresspackets 1 +net_compresspackets_minsize 64 +sv_maxrate 127000 +map mp_homestead +ns_private_match_last_mode "ttdm" +setplaylist ttdm +mp_gamemode ttdm +ns_should_return_to_lobby 0 +ns_private_match_only_host_can_change_settings 2 +setplaylistvaroverrides "respawn_delay 15 max_players 20"" northstarcn-docker.pkg.coding.net/northstarcn/northstarcn-dedi-docker/nscn-docker:latest
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



