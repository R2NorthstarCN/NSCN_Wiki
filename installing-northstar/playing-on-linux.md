
# 如何在🐧Linux发行版上游玩NorthStarCN (TODO)
> **this page is on editing phase at present**

> 如您所见，NorthStarCN和TTF2均不是为Linux发行版所编写和构建的软件，所以为了在POSIX类系统上运行这些程序，我们需要使用像Proton和Wine这样的兼容层来进行。

## 安装NorthStarCN

> 在开始安装NorthStarCN前，您应该首先安装好Proton或Wine，关于如何在Linux发行版上安装这两种兼容层已经有足够多的中文文档，此处故不再赘述

### Steam (Proton) 

> "Proton 是允许 Windows 游戏在 Linux 上运行的兼容层，它通过使用修改过的 Wine 版本和一套高性能图形 API 实现来达到这一点。 我们的团队开发并优化 Proton 已有一段时间，Proton 现已有较高覆盖率。 Proton 已支持大多数 API，大部分游戏可直接运行。 我们正在持续改善 Proton 的兼容性，而我们的目标是尽可能地接近 100% 覆盖率。"      
  ----Steam Dev

> **Note.** 您可以访问[ProtonDB](https://www.protondb.com/)来查看当前Proton可以运行的Windows游戏

> NorthStar创建了一个针对NorthStar优化的Proton分支，目前NorthStar Wiki推荐Linux Steam端和Steam Deck玩家使用该版本，但NorthStarCN并未在该版本上进行测试，故先保留该先前版本文档

1. 在[NorthStarCN启动器发布仓库](https://github.com/R2NorthstarCN/R2NorthstarCN_Launcher/releases/latest)下载最新版本的启动器文件
2. 将压缩包内所有文件解压至TTF2游戏的根目录下 ( 在Steam库中，您可以右键点击 _TitanFall 2_ ，点击 _属性_ ，然后在侧边栏点击 _本地文件_ ，然后在菜单处点击 _浏览_ )
3. 将 _Titanfall2.exe_ 暂时重命名为其他名称的文件 ( 比如 _Titanfall2old.exe_ , _Titanfall3.exe_ ), 之后将 _NorthstarLauncher.exe_ 重命名为 _Titanfall2.exe_.

 除了重命名 _NorthstarLauncher.exe_ 这一方法, 你也可以通过在两个exe文件之间创建一个软链接让未来更新NorthStarCN版本的时候稍微轻松一些. 在TTF2游戏根目录执行以下命令即可:

```markdown
ln NorthstarLauncher.exe Titanfall2.exe
```

之后从Steam库中启动TTF2时，NorthStarCN将会被自动启动.首次启动游戏时，您应该会看到[上文](installing-northstar/basic-setup.md#安装NorthStarCN)中所出现的询问窗口.

> **Note.** 部分玩家测试时发现有时Steam仍然会启动原版的TTF2游戏,而没有加载NorthStarCN.我们并不能完美复现出这一BUG，目前似乎并没有通用的解决方法,有一些玩家告知我们将Proton版本替换至 _Proton 5.13_ or _Proton Experimental_ 并将 _Proton prefix_ 的配置文件夹删除 (`Steam/steamapps/compatdata/1237970/`) 似乎可以解决这个问题. [Proton GE](https://github.com/GloriousEggroll/proton-ge-custom) 分支目前也存在该问题.
>
> 如果这个BUG像一块黏人的口香糖一样死死粘在了您的游戏上,您不妨试一试Lutris分支的Wine.

### Lutris (Wine)

1. 如果您先前还没有安装TTF2游戏，那不妨从[这里](https://lutris.net/games/titanfall-2/)安装
2. 在[NorthStarCN启动器发布仓库](https://github.com/R2NorthstarCN/R2NorthstarCN_Launcher/releases/latest)下载最新版本的启动器文件
3. 将压缩包内所有文件解压至TTF2游戏的根目录下
4. **如果您先前已经把TTF2游戏添加到了Lutris管理器内:** 右键点击 _Titanfall 2_ > _Configure_ > _Game Options_ > 将 _Executable path_ 设置为 _NorthStarCNLauncher.exe_
5. **如果没有:** 点击左侧顶部的 `+` 按钮 > 根据您的喜好设定一个名称，并且将 _Runner_ 改为 _Wine_ > 点击 _Game options_ > 将 _Executable path_ 设置为 _NorthstarLauncher.exe_ 之后保存.

> **如果您已经通过Steam安装了TTF2:** 将 _Wine prefix_ 设置为 `(你的Steam根目录)/steamapps/compatdata/1237970/pfx/`. 这样就不必再去下载一次Origin了.

现在通过Lutris启动TTF2时，NorthStarCN将会被自动启动.首次启动游戏时，您应该会看到[上文](installing-northstar/basic-setup.md#安装NorthStarCN)中所出现的询问窗口.

> **Note:** Origin might prompt you to log in and "set an installation folder for future downloads" on first launch. Just do those, close Origin, then launch the game again.

## SteamDeck

TODO.

Awaiting Editing.

## LatencyFleX

LatencyFleX is a Linux-only input latency reduction alternative to Nvidia Reflex that is supported by Northstar. Currently, LatencyFleX requires manual installation. A full install guide and current releases [can be found on their GitHub](https://github.com/ishitatsuyuki/LatencyFleX).

Northstar only requires the [Vulkan layer](https://github.com/ishitatsuyuki/LatencyFleX#latencyflex-vulkan-layer-essential) and [Wine extensions](https://github.com/ishitatsuyuki/LatencyFleX#latencyflex-wine-extensions-required-for-proton-reflex-integration) steps to be completed.

Once installed, LatencyFleX can be enabled by doing either of the following:

* **Steam:** Add the following to your Titanfall 2 launch options: `"LFX=1 %command%"`
* **Lutris:** Right click on Titanfall 2, click 'Configure', navigate to 'System Preferences' / 'System Options' / 'Environmental Variables', and use the following:

> Key: LFX Value: 1

Once in-game, LatencyFleX can be toggled off and on using the `"r_latencyflex"` console variable.

While playing with LatencyFleX, **VSync and Adaptive Super Sampling must be disabled**. If you wish to prevent tearing while using LatencyFleX, the following may be added to the end of `ns_startup_args.txt` in the root of your Titanfall 2 install:

> \+fps\_max\_use\_refresh 1

## Troubleshooting

> Read Lutris troubleshooting of [common issues with Origin](https://github.com/lutris/docs/blob/master/Origin.md) first.

### Blank console

This problem is caused due to missing fonts on your Titanfall 2 wine prefix, you will need [winetricks](https://github.com/Winetricks/winetricks) or [protontricks](https://github.com/Matoking/protontricks) depending on your installation. Follow these steps to install:

1. Close all Titanfall/Origin processes.
2. If you are using Lutris select your Titanfall 2 installation and click '▲' -> Winetricks. On Proton you can use `protontricks 1237970 --gui`
3. 'Select the default wineprefix' -> 'Install a font' -> Check the packages `lucida` and `arial`.
4. Click OK and wait for everything to install, if done correctly winetricks will popup again.
5. You can now close it and launch the game.

### Crackling sound

Can be fixed by adding [`tsched=0`](https://wiki.archlinux.org/title/PulseAudio/Troubleshooting#Glitches.2C\_skips\_or\_crackling) to `/etc/pulse/default.pa`

### Fullscreen issues

Running the game on fullscreen through Linux might lead to a black screen preventing you from launching the game. Edit your `ns_startup_args.txt` to include `-noborder -window` or edit `"setting.fullscreen"` and `"setting.nowindowborder"` at `<wineprefix>/drive_c/users/<username>/Documents/Respawn/Titanfall2/local/videoconfig.txt` to solve this.

For more info and proposed fixes, refer to [this issue thread on Github](https://github.com/R2Northstar/Northstar/issues/1)

### LatencyFleX issues

Some users have reported issues with enabling LatencyFleX. If you see `"Unable to load LatencyFleX library, LatencyFleX disabled."` in your logs, try adding `latencyflex_wine.dll` to your `bin/x64_retail` folder.

### Game crashes on launch with Cause: Access Violation Data Execution Prevention (DEP) at: 0x00000000

Try running with [ProtonGE](https://github.com/GloriousEggroll/proton-ge-custom/). In particular, `Proton-7.3-GE-1` (not `GE-Proton7-3`) has so far been found to be reliable in this case. Check this [Github issue comment for a guide](https://github.com/R2Northstar/Northstar/issues/1#issuecomment-1062483190).

### Reducing stuttering (Steam/Proton and Lutris/Wine)

You may feel that the game stutters frequently during the first hour of play. This is normal, it's just DXVK having to compile shaders at draw time due not having a ready state cache. The more you play, the less stuttering there will be in the future.

However if you don't want to wait you can try precompiled DXVK [_state cache_](https://github.com/doitsujin/dxvk#state-cache): [**Titanfall2.dxvk-cache**](https://github.com/begin-theadventure/dxvk-caches/blob/main/dxvk-caches/Titanfall/Titanfall%202/Titanfall2.dxvk-cache.md)

Proton: extract and put it in `/path/to/steamapps/shadercache/1237970/DXVK_state_cache` default is `~/.local/share/..` or next to .exe if shader pre-caching is turned off.

Wine: extract and put it next to game's .exe. Also remember to rename it if the .exe has a different name.

There are also other (not necessary) tweaks as:

_DXVK-_[_async_](https://github.com/Sporif/dxvk-async#improvements):

Wine: download [**dxvk-async**](https://github.com/Sporif/dxvk-async/releases), extract and put it in `~/.local/share/lutris/runtime/dxvk` then type the name of the folder in `▲` -> `Configure` -> `Runner Options` -> `DXVK version`, to enable add `DXVK_ASYNC 1` to `System Options` -> `Environment variables`

Proton: can be used with [**Proton-GE**](https://github.com/GloriousEggroll/proton-ge-custom). Type `DXVK_ASYNC 1 %command%` under `Properties..` -> `LAUNCH OPTIONS`

[_Preventing_](https://github.com/ValveSoftware/Proton/issues/4001#issuecomment-647014231) _Origin from writing certain files_:

Path:

Proton: `/path/to/steamapps/compatdata/1237970/pfx/drive_c/users/steamuser/Application Data/Origin` default is `~/.local/share/..`

Wine: `/path/to/drive_c/users/<username>/AppData/Roaming/Origin`

Access can be restricted using a file manager or terminal:

`chmod -R 555` -> access only

`chmod -R 755` -> access + save

It's also possible to create command aliases to type something short, such as tfoff/tfon.
