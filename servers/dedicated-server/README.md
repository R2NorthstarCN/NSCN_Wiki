
# 独立服务端

> NorthStarCN是一个开放的平台，您可以自行搭建独立游戏服务器并将其添加到服务器列表中，本文档将会为您一一讲解服务端的基本设置

## 配置文件

* `.\ns_startup_args_dedi.txt` 
  包含服务器的 [启动项](servers/dedicated-server/README#启动项)
* `.\R2Northstar\mods\Northstar.CustomServers\mod.json` 
  保存着 [全局变量](servers/dedicated-server/README#全局变量) 的默认参数
* `.\R2Northstar\mods\Northstar.CustomServers\mod\cfg\autoexec_ns_server.cfg` 
  保存着 [全局变量](servers/dedicated-server/README#全局变量) 的自定义参数，该文件在游戏加载时将覆盖上方的默认参数




## 启动项

独立服务端的启动参数可以在 `ns_startup_args_dedi.txt` 中添加

e.g: `+setplaylist ps +mp_gamemode ps`

| 启动项                         | 接受值                                                           | 描述                                                                                        |
| -------------------------- | ------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| `+setplaylist`             | 参考 [游戏模式](servers/dedicated-server/README#游戏模式) (该值应保持与 `mp_gamemode` 所设置的值相同,除非您设置的模式为私人比赛`private_match`) | 设置服务器的游戏模式 (如果您设置的值并非私人比赛`private_match`, 那么请务必添加 `+map` 并设置正确的游戏地图，若未设置 `+map`，服务器默认加载的地图为私人比赛大厅 `mp_lobby`(这是完全错误的搭配！！！) ，错误的模式与地图搭配会导致您的服务器**无法**在服务器浏览器上注册并对所有玩家可见) |
| `+setplaylistvaroverrides` | 参考 [游戏参数覆写](servers/dedicated-server/README#游戏参数覆写)                 | 设置服务器的游戏对局参数                                                                                |
| `-port`                    | `1-65535` 之间的整数值                                              | 设置服务器监听的UDP端口                                                                             |
| `+mp_gamemode`             | 参考 [游戏模式](servers/dedicated-server/README#游戏模式)                                  | 设置服务器载入某一游戏模式                                                                               |
| `+map`                     | 参考 [游戏地图](servers/dedicated-server/README#游戏地图) (如不指定，则为 `mp_lobby`)                       | 设置服务器载入某一游戏地图                                                                             |

| 特殊项                  | 描述                                                    |
| --------------------- | ----------------------------------------------------- |
| `-maxplayersplaylist` | 允许 [游戏参数覆写](servers/dedicated-server/README#游戏参数覆写) 覆写最大玩家数 |
| `-enablechathooks`    | 允许在聊天框中直接输入指令                                         |
| `-allowdupeaccounts`  | 允许服务器内同时存在多名相同ID玩家进行游戏  |

### 游戏参数覆写

游戏参数覆写能更改游戏内对局规则的设置. 您可以在`ns_startup_args_dedi.txt`中添加`+setplaylistvaroverrides`和具体参数值修改

所有参数必须位于引号中并以空格分开

例如: 
```
+setplaylistvaroverrides "run_epilogue 0 featured_mode_amped_tacticals 1 max_players 20 aegis_upgrades 1"
```

| 覆写项                            | 接受值   | 默认值 | 描述                                                                                                 |
| -------------------------------------------- | ----- | --- | -------------------------------------------------------------------------------------------------- |
| `max_players`                                | `int` |     | 设置对局内最大玩家数量                                   |
| `custom_air_accel_pilot`                     | `int` | `500` | 设置空中加速数值                                                                                                   |
| `pilot_health_multiplier`                    | `int` |     | 设置玩家HP相较于默认HP的倍数                                                                                                  |
| `run_epilogue`                               | `0-1` | `1` | 是否启用撤离                                                                                            |
| `respawn_delay`                              | `int` |     | 设置玩家复活所需等待时间                                                                                               |
| `boosts_enabled`                             | `0-1` | `0` | 是否禁用铁驭强化道具 |
| `earn_meter_pilot_overdrive`                 | `0-2` |     |                                                                                                    |
| `earn_meter_pilot_multiplier`                | `int` |     | 铁驭在游戏内获得奖励点数的倍数(即左下角呼叫泰坦或战术技能的充能条进度)                                                                                                   |
| `earn_meter_titan_multiplier`                | `int` |     | 泰坦在游戏内获得奖励点数的倍数(即左下角核心进度条与F2战术技能)                                                                                                   |
| `aegis_upgrades`                             | `0-1` | `0` | 是否启用泰坦神盾升级                                                                        |
| `infinite_doomed_state`                      | `0-1` |     |                                                                                                    |
| `titan_shield_regen`                         | `0-1` | `0` | 是否启用泰坦能量防护罩恢复                                                                                          |
| `scorelimit`                                 |       |     | 对局分数上限                                                                                                   |
| `roundscorelimit`                            |       |     |                                                                                                    |
| `timelimit`                                  |       |     |                                                                                                   |
| `oob_timer_enabled`                          | `0-1` |     | 是否限制玩家出界行为                                                                                             |
| `roundtimelimit`                             |       |     | 回合时间                                                                                                   |
| `classic_rodeo`                              | `0-1` |     | 是否启用经典训牛术(即拔出电池后不离机)                                                                                                 |
| `classic_mp`                                 | `0-1` | `1` | 是否启用入场运输船动画                                                                                            |
| `fp_embark_enabled`                          |       |     | 是否启用第一人称训牛术和进入泰坦动画                                                                                          |
| `promode_enable`                             | `0-1` | `0` | Dev / Debug                                                                                                   |
| `riff_floorislava`                           | `0-1` | `0` | 是否在地面生成电子烟雾                                                                                         |
| `featured_mode_all_holopilot`                | `0-1` | `0` | 是否将所有玩家战术技能替换为幻影                                                                                                   |
| `featured_mode_all_grapple`                  | `0-1` | `0` | 是否将所有玩家战术技能替换为钩爪                                                                                                   |
| `featured_mode_all_phase`                    | `0-1` | `0` | 是否将所有玩家战术技能替换为相位移动                                                                                                   |
| `featured_mode_all_ticks`                    | `0-1` | `0` | 是否将所有玩家战术技能替换为Tick炸弹                                                                                                   |
| `featured_mode_tactikill`                    | `0-1` | `0` |                                                                                                    |
| `featured_mode_amped_tacticals`              | `0-1` | `0` | 是否将所有玩家战术技能冷却数+1                                                                                                   |
| `featured_mode_rocket_arena`                 | `0-1` | `0` | 是否在游戏内启用火箭竞技场游戏规则                                                                                                   |
| `featured_mode_shotguns_snipers`             | `0-1` | `0` | 是否在游戏内启用Armed and Dangerous游戏规则，即仅允许使用霰弹与狙击枪                                                                                                   |
| `iron_rules`                                 | `0-1` | `0` | 是否禁止泰坦弹射和玩家离开泰坦                                                                                            |
| `riff_player_bleedout`                       | `0-1` |     | Dev / Debug                                                                                                   |
| `player_bleedout_forceHolster`               | `0-1` |     | Dev / Debug                                                                                                   |
| `player_bleedout_forceDeathOnTeamBleedout`   | `0-1` |     | Dev / Debug                                                                                                   |
| `player_bleedout_bleedoutTime`               | `int` |     | Dev / Debug                                                                                                   |
| `player_bleedout_firstAidTime`               | `int` |     | Dev / Debug                                                                                                   |
| `player_bleedout_firstAidTimeSelf`           | `int` |     | Dev / Debug                                                                                                   |
| `player_bleedout_firstAidHealPercent`        | `int` |     | Dev / Debug                                                                                                   |
| `player_bleedout_aiBleedingPlayerMissChance` | `int` |     | Dev / Debug                                                                                                   |

## 全局变量

全局变量位于 `R2Northstar\mods\Northstar.CustomServers\mod\cfg\autoexec_ns_server.cfg` 中.

您可在这里更改服务器名称，描述与TCP验证端口等.

| 名称                                               | 描述                                                      | 默认值                            | 接受值                              |
| ------------------------------------------------ | ------------------------------------------------------- | ------------------------------ | -------------------------------- |
| `ns_server_name`                                 | 您的服务器名称                                        | `"Unnamed Northstar Server"`   | `string`                         |
| `ns_server_desc`                                 | 您的服务器描述信息                                        | `"Default server description"` | `string`                         |
| `ns_server_password`                             | 服务器密码, 若`ns_auth_allow_insecure`被设置为`1`,所有客户端均可使用`connect`命令直接进入房间       |``                         | `string`                         |
| `ns_report_server_to_masterserver`               | 服务器是否对他人可见                 | `1`                            | `0-1`                            |
| `ns_report_sp_server_to_masterserver`            | 运行单人战役模式时，服务器是否对他人可见         | `0`                            | `0-1`                            |
| `ns_auth_allow_insecure`                         | 是否关闭验证措施，关闭后所有客户端均可使用`connect`命令直接进入房间         | `0`                            | `0-1`                            |
| `ns_erase_auth_info`                             | 服务器是否清除已使用过的验证信息, 保持值设置为`1`            | `1`                            | `0-1`                            |
| `ns_player_auth_port`                            | 服务器用于被主服务器验证的`TCP`端口                              | `8081`                         | `1-65535`                        |
| `everything_unlocked`                            | 服务器是否解锁所有道具                                  | `1`                            | `0-1`                            |
| `ns_should_return_to_lobby`                      | 服务器是否在对局结束后返回私人比赛大厅，若值设为`0`，则会在多人游戏地图池中轮换            | `1`                            | `0-1`                            |
| `ns_private_match_only_host_can_change_settings` | 0 --> 玩家可以更改所有设置；1 --> 玩家仅能更改地图与模式；2 --> 玩家不能更改任何设置     | `0`                            | `0-2`                            |
| `ns_private_match_countdown_length`              | 在私人比赛大厅开始游戏后，游戏开始的倒计时时长                                 | `15`                           | `int`                            |
| `ns_private_match_last_mode`                     | 覆写私人比赛大厅所选择的的默认模式                                             | `tdm`                          | 所有的 [游戏模式](servers/dedicated-server/README#游戏模式)     |
| `ns_private_match_last_map`                      | 覆写私人比赛大厅的默认选择地图                                             | `mp_forwardbase_kodai`         | 所有的 [游戏地图](servers/dedicated-server/README#游戏地图)               |
| `ns_disallowed_weapons`                          | 武器黑名单                                                   |                                | 任何 [武器](servers/dedicated-server/README#武器) 以半角逗号分隔 |
| `ns_disallowed_weapon_primary_replacement`       | 替换武器黑名单中的武器为"   "                                                |                                | 一件 [武器](servers/dedicated-server/README#武器)          |
| `ns_should_log_unknown_clientcommands`           | 是否在控制台中显示未知的指令输入                                 | `1`                            | `0-1`                            |
| `net_chan_limit_mode`                            | 0 --> 不限制占用网络通道超时的客户端；1 --> 踢出占用网络通道超时的客户端；2 --> 将占用网络通道时间超时的客户端信息显示在控制台中 | `2`                            | `0-2`                            |
| `net_chan_limit_msec_per_sec`                    | net_chan_limit_mode 中的超时时间设定 (ms)                    | `30`                           | `int`                            |
| `base_tickinterval_mp`                           | 服务器Tickrate的间隔，值为 1 / 设置值                                | `0.016666667`                  | `float`                          |
| `sv_updaterate_mp`                               | 服务器每秒发送数据包的最大允许次数，即updaterate                            | `20`                           | `int`                            |
| `sv_max_snapshots_multiplayer`                   | 服务器所存储的用于击杀回放的Tick数量，应为 sv_updaterate_mp的 15倍          | `300`                          | `int`                            |
| `host_skip_client_dll_crc`                       | 服务器是否跳过验证客户端`client.dll`，使用MOD会更改此dll文件        | `1`                            | `0-1`                            |

## 游戏模式

游戏模式可以通过 [`+mp_gamemode`](servers/dedicated-server/README#启动项) 这一启动参数指定

如果设置了 [`ns_should_return_to_lobby 0`](servers/dedicated-server/README#全局变量) 这一条环境变量, 则[`ns_private_match_last_mode`](servers/dedicated-server/README#全局变量) 这一条环境变量也需要被正确设定

### 原版

| Playlist       | Title               |
| -------------- | ------------------- |
| `private_match` | 私人比赛                |
| `aitdm`     | 消耗战             |
| `at`         | 赏金猎人           |
| `coliseum`       | 竞技场                 |
| `cp`             | 强化据点                |
| `ctf`            | 夺旗                  |
| `fd_easy`   | 边境防御 (简单)     |
| `fd_normal` | 边境防御 (普通)  |
| `fd_hard`   | 边境防御 (困难)     |
| `fd_insane` | 边境防御 (疯狂)   |
| `fd_master` | 边境防御 (大师)   |
| `lf`             | 烈火战场                |
| `lts`            | Last Titan Standing |
| `mfd`            | Marked For Death    |
| `ps`             | 铁驭对铁驭               |
| `solo`           | 单人战役            |
| `tdm`            | 小规模战斗               |
| `ttdm`           | 泰坦争斗                |
| `alts`          | Aegis Last Titan Standing |
| `attdm`         | 神盾泰坦争斗                    |
| `ffa`           | 自由混战              |
| `fra`           | Free Agents               |
| `holopilot_lf` | 大骗局                       |
| `rocket_lf`    | 火箭竞技场              |
| `turbo_lts`    | Turbo Last Titan Standing |
| `turbo_ttdm`   | 涡轮泰坦争斗                    |

### MOD额外模式

| Playlist  | Title              |
| --------- | ------------------ |
| `chamber`   | One in the Chamber |
| `ctf_comp` | Competitive CTF    |
| `fastball`  | Fastball           |
| `gg`        | 军备竞赛               |
| `hidden`    | 幽灵猎杀               |
| `hs`        | 追迷藏                |
| `inf`       | 感染                 |
| `kr`       | 强化杀戮赛     |
| `sbox`      | 沙盒                 |
| `sns`       | 针锋相对  |
| `tffa`      | 泰坦自由混战          |
| `tt`        | Titan Tag          |
| `sp_coop` | 多人合作单人战役 |

## 武器

| Weapon Code                  | Weapon name    |
| ---------------------------- | -------------- |
| `mp_weapon_car`              | CAR            |
| `mp_weapon_alternator_smg`  | 转换者            |
| `mp_weapon_hemlok_smg`      | 电能冲锋枪          |
| `mp_weapon_r97`              | R-97           |
| `mp_weapon_hemlok`           | 汗洛             |
| `mp_weapon_vinson`           | 平行步枪           |
| `mp_weapon_g2`               | G2             |
| `mp_weapon_rspn101`          | R-201          |
| `mp_weapon_rspn101_og`      | R-101          |
| `mp_weapon_esaw`             | 专注轻机枪       |
| `mp_weapon_lstar`            | L-STAR         |
| `mp_weapon_lmg`              | 喷火轻机枪       |
| `mp_weapon_shotgun`          | EVA-8 Auto     |
| `mp_weapon_mastiff`          | 敖犬        |
| `mp_weapon_dmr`              | DMR            |
| `mp_weapon_sniper`           | 克莱伯            |
| `mp_weapon_doubletake`       | 双重击    |
| `mp_weapon_pulse_lmg`       | 冷战          |
| `mp_weapon_smr`              | Sidewinder SMR |
| `mp_weapon_softball`         | 榴弹发射器      |
| `mp_weapon_epg`              | EPG-1          |
| `mp_weapon_shotgun_pistol`  | 莫桑比克           |
| `mp_weapon_wingman_n`       | 菁英小帮手          |
| `mp_weapon_autopistol`       | RE-45          |
| `mp_weapon_semipistol`       | P2016          |
| `mp_weapon_wingman`          | 小帮手            |
| `mp_weapon_mgl`              | MGL            |
| `mp_weapon_arc_launcher`    | 电球发射器    |
| `mp_weapon_rocket_launcher` | 火箭筒         |
| `mp_weapon_defender`         | 电能步枪           |

## 游戏地图

地图可以通过 [`ns_should_return_to_lobby 0`](servers/dedicated-server/README#全局变量) 来设置自动轮换

下一回合游戏地图可以通过 [`ns_private_match_last_map`](servers/dedicated-server/README#全局变量) 指定

若需自定义地图轮换池，则需借助第三方MOD

### 多人游戏

| Map                     | Title  |
| ----------------------- | ------ |
| `mp_angel_city`         | 天使城    |
| `mp_black_water_canal` | 黑水运河   |
| `mp_box`                 | 沙盒   |
| `mp_coliseum`            | 竞技场    |
| `mp_coliseum_column`    | 梁柱     |
| `mp_colony02`            | 殖民地    |
| `mp_complex3`            | 综合设施   |
| `mp_crashsite3`          | 坠机现场   |
| `mp_drydock`             | 干坞     |
| `mp_eden`                | 伊甸     |
| `mp_forwardbase_kodai`  | 虎大前进基地 |
| `mp_glitch`              | 异常     |
| `mp_grave`               | 新兴城镇   |
| `mp_homestead`           | 家园     |
| `mp_lf_deck`            | 甲板     |
| `mp_lf_meadow`          | 草原     |
| `mp_lf_stacks`          | 堆积地    |
| `mp_lf_township`        | 城镇     |
| `mp_lf_traffic`         | 交通     |
| `mp_lf_uma`             | UMA    |
| `mp_lobby`               | 大厅     |
| `mp_relic02`             | 遗迹     |
| `mp_rise`                | 崛起     |
| `mp_thaw`                | 系外行星   |
| `mp_wargames`            | 战争游戏   |

### 战役

| Map                    | Title              |
| ---------------------- | ------------------ |
| `sp_training`           | 铁驭训练               |
| `sp_crashsite`          | BT-7274            |
| `sp_sewers1`            | 鲜血与钢铁              |
| `sp_boomtown_start`    | 踏入虚空 - Part 1      |
| `sp_boomtown`           | 踏入虚空 - Part 2      |
| `sp_boomtown_end`      | 踏入虚空 - Part 2      |
| `sp_hub_timeshift`     | 因果报应 - Part 1 / 3 |
| `sp_timeshift_spoke02` | 因果报应 - Part 2      |
| `sp_beacon`             | 信号台 - Part 1 / 3  |
| `sp_beacon_spoke0`     | 信号台 - Part 2       |
| `sp_tday`               | 烈火审判               |
| `sp_s2s`                | 圣柜                 |
| `sp_skyway_v1`         | 折叠时空武器             |