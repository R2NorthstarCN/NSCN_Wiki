# NorthStarCN游戏故障排除

!> 在首次启动NorthStarCN前，请先至少运行一次原版游戏

## 找不到 `Tier0.dll` 

![tier0.dll](../assets/tier0.dll-failure.png)

该错误通常是因为您没有把`NorthstarLauncher.exe`及其资源文件放置在正确的目录导致的，请将启动器及其资源文件放置在`Titanfall 2`游戏根目录下

* Steam安装默认目录: `%ProgramFiles(x86)%\Steam\steamapps\common\Titanfall2\` 或 `..\SteamLibrary\steamapps\common\Titanfall2\`
* Origin安装默认目录: `..\Origin Games\Titanfall2\`

**如果这个问题在您确认`NorthstarLauncher.exe`及其资源文件放置在正确目录后仍然出现:** 这意味着您的游戏资源文件出现了**缺失或损坏**

* 打开游戏根目录，找到\bin\x64_retail\该文件夹，确认您是否有以下所有文件

![根目录](../assets/dlls-list.png)

若出现缺失，请您在Steam/Origin修复游戏

## LSX Authentication Failed

![LSX](https://user-images.githubusercontent.com/97235072/148391447-300e1b47-6148-43f7-8854-b0882e150d12.png)

若您遇到该问题，请确认您先前已经运行过一次官服，之后请尝试重启Origin或重启电脑，如果这样依旧不能解决该问题，请依次尝试下方的步骤，直至您能进入游戏为止

* 请再次确认您已经在EA Desktop客户端中登陆了一个拥有TitanFall 2的账号，并且先前已经运行过一次官服！
* [在Origin或Steam中添加启动项](#launch-opts)，使用Steam/Origin来代替`Northstarlauncher.exe`启动游戏
* 退出登录Origin，并将Origin彻底关闭，之后启动`Northstarlauncher.exe`，这将需要您重新登录Origin，完成登录后，则应该可以进入游戏


## File Corruption Detected


Make sure you updated [Northstar to version v1.4.0 or higher](https://github.com/R2Northstar/Northstar/releases/) as this version features changes that address this problem.


![Engine Error: File corruption detected. Please repair or re-install the game.](https://user-images.githubusercontent.com/39478251/147338706-74797220-7d7f-4c81-9ba0-d88e29a2a1e2.png)

Don't panic! This warning seems to be caused by Origin and none of your files are actually corrupted. If you get this warning after launching the game try the following steps, closing the game before and launching it again after:

* Make sure you got the newest version of Northstar. In particular, [v1.4.0 or higher](https://github.com/R2Northstar/Northstar/releases/) have this problem fixed.
* Restart Origin\
  Also check task manager that all Origin processes are gone before restarting it\
  (even if you have the Steam version)
* Restart your PC
* Start Northstar with Origin already open
* Start Northstar with Origin fully closed.
* Start vanilla game and see if this works.\
  If vanilla doesn't work either, check [this thread on EA forums](https://answers.ea.com/t5/Titanfall-2/Titanfall-2-Wont-Laumch-DLL-file-issue/td-p/5660909)
* Check [this issue thread](https://github.com/R2Northstar/Northstar/issues/6) to see whether any of the solutions proposed there work for you.
* Verify game files via Steam/Origin (depending on where you own the game)
* Check Github issues if anyone else is experiencing this problem. Maybe current release has a bug.

If you followed all these steps and even launching the vanilla version of the game doesn't work, your final option is to fully remove the game and reinstall it.\
Then checking if vanilla works before reinstalling Northstar.

## Failed copying wsock32.dll <a href="#wsock" id="wsock"></a>

You are probably using EA Desktop app and it sets up game installations with no write permissions contrary to Origin.

### Solution 1

* Launch EA Desktop and the game as admin once so that it can copy that file.

### Solution 2

1. Copy `C:\WINDOWS\system32\wsock32.dll` to your Desktop / Temporary folder.
2. Rename the copied file to `wsock32.org.dll`.
3. Move `wsock32.org.dll` into `Titanfall2/bin/x64_retail/`.
4. Delete the copied `wsock32.org.dll` from your Desktop / Temporary folder.

Do NOT make any changes in `system32`, just copy the file.

### Solution 3

1. Locate your `Titanfall2` folder
2. Right click it and go `Properties > Security`
3. Give yourself write permissions

## Can't Join Servers (Issues with 10th+ gen Intel CPUs)<a href="#intel" id="intel"></a>

![Newer Intel CPU error: Data Center: Searching...](https://user-images.githubusercontent.com/18601697/148625000-882bf1db-b9b2-4e9e-88db-6d608e58a35b.png)

On newer Intel CPUs you might see a message like this

> "Contacting Respawn servers.../Data Center: Searching..."

If you are seeing this in the main menu of TF|2 and have a 10th or 11th generation Intel CPU this is a bug which has a simple fix:

In the Windows Start menu on the bottom left search for "Edit the system environment variables" and open the program. In the "advanced" tab click on "Environment Variables..." near the bottom.\
In System Variables (not user variables) click "New..." and add a new system variable where the variable name is `OPENSSL_ia32cap` and the value is `~0x200000200000000`. Make sure to click OK to apply the changes. Finally restart your device and you should be good to go.

If you're on Linux, you can set the appropriate environment variable via `env OPENSSL_ia32cap=~0x20000000 %command%`.

**Note:** This issue is not exclusive to Northstar client but also affects the vanilla version, so if you only get it on Northstar there might be a different problem at hand as well. In fact it's not even unique to Titanfall 2 either.

See also [this thread on Steam](https://steamcommunity.com/app/1237970/discussions/0/3081016749018656768/)

## I disabled all mods and now I cannot re-enable them <a href="#disabled-mods" id="disabled-mods"></a>

Go to your `Titanfall2` directory. From there go to the `R2Northstar` and delete `enabledmods.json`. This file stores information about which mods are enabled and disabled. By deleting this file Northstar will fall back to the default (all mods enabled) and re-create the file appropriately.

## VCRUNTIME140 Not found <a href="#vcruntime" id="vcruntime"></a>

If you get this error you can fix it by [installing vcredist 2015-2022](https://docs.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170). If it does not work install the 2013 version

## Server ALWAYS Full <a href="#servers-full" id="servers-full"></a>

* Double click on the server name in rapid succession.
* Alternatively, click on the server you want to join, and click "join".
  * Clicking on no server but clicking "join" will attempt to connect you to the very first server, which is usually full

## Launch Northstar Locked <a href="#locked-northstar" id="locked-northstar"></a>

Go to Mods at the bottom of your screen on the main menu, then click Authentication Agreement and accept

## I can't open the console <a href="#console" id="console"></a>

* Navigate to your Titanfall2 directory then open
* Open `R2Northstar\mods\Northstar.Client\mod\cfg\autoexec_ns_client.cfg`
  * And change the \` to one of the F keys (for example `F1` / `F2`) (Note: _Only \~ or F1-12 work_) - This _should_ fix it
    * _Restart game!_

## The Main Menu is blank <a href="#blank-menu" id="blank-menu"></a>

* Please remove conflicting mods such as `better.serverbrowser` and reinstall _Northstar core mods_ (those that start with `Northstar.` / are in the [NorthstarMods repository](https://github.com/R2Northstar/NorthstarMods) / included in the release zip).\\
* Try deleting `enabledmods.json` inside the R2Northstar folder as well.
* Otherwise pay attention in console for your errors if you know what you're doing.

## Adding Launch Options <a href="#launch-opts" id="launch-opts"></a>

Adding `-northstar` will start Northstar when launching from your launcher\
Adding `-vanilla` will start the normal game when you have Northstar installed

* For Steam
  * `Your library > Right click TF|2 > Properties > Launch Options > -northstar or -vanilla`
* For Origin
  * `Your library > Right click TF|2 > Game Properties > Advanced Launch Options > Command Line Arguments > -northstar or -vanilla`

## Access Violation

If your error says `Access Violation | Attempted to read from 0x00000000` specifically DO NOT post just THAT.\
The real error is most likely slightly higher. Please post that in issues or the discord

## I can't play the Campaign <a href="#campaign" id="campaign"></a>

Campaign is not supported in Northstar yet, but you could do one of these "**_fixes_**"

1. Doing `ns_auth_allow_insecure 1` in the console
   * [If you can't open the console](#console)
2. Adding `-vanilla` to your launch options
   * [How to add launch options](#launch-opts)

## Authentication Failed when clicking Launch Northstar <a href="#lsx2" id="lsx2"></a>

Before trying this check out [this section](#lsx).\
Alternative to that fix:

1. Close the game
2. Open task manager
3. End Origin (everything origin related)
4. Launch Origin as admin
5. Start the game through Origin with `-northstar` in [launch options](#launch-opts)
6. See if that fixed it

## Could't Initialize Sound / DEVICE_IN_USE <a href="#initsound" id="initsound"></a>

![Engine Error: Could't Initialize Sound](https://user-images.githubusercontent.com/2706225/153178714-2a50ac25-59fa-44d6-a47a-910058ec9888.png)

If message contains: `AUDCLNT_E_DEVICE_IN_USE`

1. Go to Windows Search Bar, type `mmsys.cpl`, press enter.
2. Make sure you selected the right audio device as default (your headset or speakers usually).
3. If it still does not work, disable exclusive mode on your default device:
![Disable exclusive mode](https://user-images.githubusercontent.com/2706225/153179355-01598326-3297-4588-be4b-ed5257e23941.png)
4. Restart your computer.

This issue could also be caused if you use some sort of audio wrapper to control volume and stuff like Voicemeter Banana. The above fix was tested with Voicemeter Banana.

-->