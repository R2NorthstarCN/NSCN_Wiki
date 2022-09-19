# 游戏内指令

## 呼出控制台

在游戏中, 按下键盘上 `` ` `` 键，该键位于 `TAB` 上方，数字键`1`左侧，`ESC`下方

若您在使用部分小语种输入法时按下`` ` ``键无法呼出控制台，请将输入法切换至`ENG(英语)`或者`中文(拼音)`

再次按下 `` ` `` 即可关闭控制台


### 更换控制台呼出按键

控制台只可绑定在 ```"`"``` 或功能键 ```"F1" - "F12"``` 上，其余按键绑定后并无效果

在游戏中，找到设置/Settings `控制 / Controls > 键鼠 / MOUSE/KEYBOARD > 按键绑定 / Key Bindings` ，更改首行 `"Toggle Developer Console"` 所绑定的按键即可

---

如需手动绑定，打开 `C:\Users\(此处为您的Win用户名)\Documents\Respawn\Titanfall2\local` 中的 `settings.cfg`.\
找到 `toggleconsole` 一行，若cfg中不存在该指令，您应该手动写入

例如
```
bind "`" "toggleconsole"
```

`"  "`中可以填写我们想要绑定的按键，此处我们将按键绑定至F4键上

```
bind "F4" "toggleconsole"
```
之后保存cfg，重新进入游戏即可

## 命令列表

### NorthStarCN附加指令

| 命令                              | 描述                                                                                                 | 接受值                                           |
| ------------------------------------ | ----------------------------------------------------------------------------------------------------------- | ----------------------------------------------- |
| `ns_masterserver_hostname`           | 主服务器URL                                                                                            | `https://nscn.wolf109909.top`                |
| `ns_auth_allow_insecure`             | 是否允许客户端不与主服务器验证也可通过`connect`指令加入游戏                                                | `0` / `1`                                       |
| `connect`                            | 连接至某一未启用验证的服务器，需要填写IP地址与端口号，若未填写端口则默认为37015                                                                | `<ip address>:<port>` 例: `3.3.3.3:37725`     |
| `reload_mods`                        | 重新加载 MODS                                                                                                 |                                                 |
| `ns_disallowed_tacticals`            | 禁止使用的铁驭战术技能                                                                | 例: `"mp_ability_grapple,mp_ability_heal"` |
| `ns_disallowed_tactical_replacement` | 替换禁止使用的铁驭战术技能为"  "                                               | 例: `"mp_ability_grapple"`                      |
| `give mp_weapon_peacekraber`         | 给予 玩家一把peacekraber，这是一把测试武器，使用了kraber的模型，即Apex Legends中的和平捍卫者                                                                                     |                                                 |
| `r_latencyflex`                      | 是否启用 [LatencyFleX](../../using-northstar/playing-on-linux/#latencyflex) (这是一个针对Linux端玩家的选项，仅在Linux环境下可以开启，开启前需要安装前置环境) | `0` / `1`                                       |

### 部分开发测试指令


需要先在控制台执行 `sv_cheats 1` ，然后才能使用以下指令

| 命令                                    | 描述                                                           |
| ------------------------------------------- | --------------------------------------------------------------------- |
|`thirdperson`|切换至第三人称模式|
|`firstperson`|切换至第一人称模式|

!> 以下部分指令仅在服务端也启用`sv_cheats 1`时才会生效，若您使用自己的电脑在游戏中开启了私人比赛房间，该房间服务端是在您电脑上本地运行的，在控制台输入`sv_cheats 1`相当于客户端和服务端均启用了作弊，所以指令可以生效，若您连接到一个没有启用作弊的远程服务器，即使在本地启用`sv_cheats 1`，以下指令也不会生效

| 命令                                    | 描述                                                           |
| ------------------------------------------- | --------------------------------------------------------------------- |
|`script DevSpawnTitan()`|在您的位置上生成您在选择页面所装备的泰坦|
|`script SetGameEndTime(1200.0)`|将比赛剩余时间设置为1200秒|
|`ent_create npc_soldier`|在准星处生成NPC步兵|
|`ent_create npc_stalker`|在准星处生成NPC幽灵战士|
|`ent_create npc_spectre`|在准星处生成NPC潜行者|
|`ent_create npc_titan`|在准星处生成NPC泰坦(使用前请先在地面生成您的泰坦，否则会导致游戏崩溃)|
|`ent_create npc_marvin`|在准星处生成NPC马文|
|`ent_fire !picker setteam 2`|将准星处实体所属阵营设置为IMC|

`1`为测试阵营，对IMC和MIL均中立，`2`为IMC，`3`为MIL

### 服务端指令

| 命令                                    | 描述                                                           | 默认值 |
| ------------------------------------------- | --------------------------------------------------------------------- | ------- |
| `sv_cheats`                                 | 是否允许玩家使用作弊指令                 | 0       |
| `sv_AllWaysSupportsSaveRestore`             | Dev / Debug                                                                       | 0       |
| `sv_allTicksFinal`                          | Dev / Debug                                                                | 0       |
| `sv_allowSendTableTransmitToClients`        | Dev / Debug                                                                        | 1       |
| `sv_alltalk`                                | 是否启用全局语音.             | 0       |
| `sv_balanceTeams`                           | 是否让服务器在对局间尝试平衡队伍. | 1       |
| `sv_bounds_show_errors`                     | Dev / Debug                                                                      | 0       |
| `sv_clampPlayerFrameTime`                   | Dev / Debug                                                                        | 0       |
| `sv_clockcorrection`                        | Dev / Debug                                                                        | 1       |
| `sv_clockcorrection_msecs`                  | Dev / Debug                                                                        | 75      |
| `sv_compressPlaylists`                      | Dev / Debug                                                                        | 1       |
| `sv_connectingClientDelay`                  | Dev / Debug                                                                        | 3       |
| `sv_debug_deferred_trace`                   | Dev / Debug                                                                        | 0       |
| `sv_debug_deferred_trace_overlay`           | Dev / Debug                                                                        | 0       |
| `sv_debug_prop_send`                        | Dev / Debug                                                                        | 0       |
| `sv_debugmanualmode`                        | Dev / Debug                                                                      | 0       |
| `sv_disconnectOnTooManySnapshotFrames`      | Dev / Debug                                                                      | 1       |
| `sv_dumpstringtables`                       | Dev / Debug                                                                      | 0       |
| `sv_earlyPersistenceRead`                   | Dev / Debug                                                                      | 0       |
| `sv_edgefriction`                           | Dev / Debug                                                                      | 2       |
| `sv_everyThirdTick`                         | Dev / Debug                                                                      | 0       |
| `sv_extra_client_connect_time`              | Dev / Debug                                                                      | 60      |
| `sv_gravity`                                | 游戏内物理重力数值，默认为`750`                                | 750     |
| `sv_hibernate_ms`                           | Dev / Debug                                                                      | 5       |
| `sv_hibernate_ms_vgui`                      | Dev / Debug                                                                      | 5       |
| `sv_hibernate_postgame_delay`               | Dev / Debug                                                                      | 5       |
| `sv_hibernate_when_empty`                   | 服务器是否在房间内无玩家时自动休眠，在有玩家尝试加入时会自动唤醒，启用该项可以在无玩家时节约服务器资源消耗                        | 0       |
| `sv_instancebaselines`                      | Dev / Debug                                                                      | 1       |
| `sv_kickPlayersTooFarInFuture`              | Dev / Debug  | 1       |
| `sv_lerpAnims`                              | Dev / Debug                                                                      | 1       |
| `sv_lobbyType`                              | Dev / Debug                                                                      | 1       |
| `sv_massreport`                             | Dev / Debug                                                                      | 0       |
| `sv_maxUserCmdsPerPlayerPerFrame`           | Dev / Debug                                                                      | 10      |
| `sv_max_prop_data_dwords_lobby`             | Dev / Debug                                                                      | 100000  |
| `sv_max_prop_data_dwords_multiplayer`       | Dev / Debug                                                                      | 125000  |
| `sv_max_prop_data_dwords_singleplayer`      | Dev / Debug                                                                      | 300000  |
| `sv_max_props_lobby`                        | Dev / Debug                                                                      | 50000   |
| `sv_max_props_multiplayer`                  | Dev / Debug                                                                      | 75000   |
| `sv_max_props_singleplayer`                 | Dev / Debug                                                                      | 200000  |
| `sv_max_snapshots_lobby`                    | Dev / Debug                                                                      | 100     |
| `sv_max_snapshots_multiplayer`              | Dev / Debug                                                                      | 300     |
| `sv_max_snapshots_singleplayer`             | Dev / Debug                                                                     | 10      |
| `sv_maxclientframes`                        | Dev / Debug                                                                      | 300     |
| `sv_maxrate`                                | Dev / Debug                                                                      | 0       |
| `sv_maxroutable`                            | Dev / Debug                                                                      | 1200    |
| `sv_maxupdaterate`                          | Dev / Debug                                                                      | 60      |
| `sv_minrate`                                | Dev / Debug                                                                      | 128000  |
| `sv_minupdaterate`                          | Dev / Debug                                                                      | 20      |
| `sv_noclipaccelerate`                       | 启用`noclip`指令后玩家的加速度.                                 | 10000   |
| `sv_noclipduringpause`                      | 是否允许服务器暂停后，客户端启用`noclip`指令，启用后客户端玩家仅可移动自己的视角，而玩家实体无法在三维空间内移动，因为此时服务器运算完全暂停，这是一个仅用于测试的指令                                 | 0       |
| `sv_noclipspeed`                            | 启用`noclip`指令后玩家的移动最大速度.                                                 | 5       |
| `sv_normalSimulationCommandThreshold`       | Dev / Debug                                                                      | 3       |
| `sv_parallel_sendsnapshot`                  | Dev / Debug                                                                      | 1       |
| `sv_partyDediOnly`                          | Dev / Debug                                                                      | 0       |
| `sv_pausable`                               | 设置服务器是否可以暂停，若设置为1，则可在控制台输入pause来暂停服务器，此时服务器运算会完全暂停，客户端不会丢失与服务器的连接                                                                      | 0       |
| `sv_physics_maxvelocity`                    | Dev / Debug                                                                      | 4000.0  |
| `sv_playerNameAppendCheater`                | Dev / Debug                                                                      | 1       |
| `sv_playerSimTimeBuffer`                    | Dev / Debug                                                                      | 0       |
| `sv_precacheinfo`                           | Dev / Debug                                                                      |         |
| `sv_printClockCorrections`                  | Dev / Debug                                                                      | 0       |
| `sv_printClockTiming`                       | Dev / Debug                                                                      | 0       |
| `sv_props_funnel_into_portals`              | Dev / Debug                                                                      | 1       |
| `sv_props_funnel_into_portals_deceleration` | Dev / Debug                                                                      | 2.0f    |
| `sv_querylimit_per_sec`                     | Dev / Debug                                                                      | 10      |
| `sv_quota_stringcmdspersecond`              | Dev / Debug                                                                     | 60      |
| `sv_rcon_banpenalty`                        | Dev / Debug                                                                      | 0       |
| `sv_rcon_log`                               | 是否将RCON命令执行记录到LOG中                                          | 1       |
| `sv_rcon_maxfailures`                       | Dev / Debug                                                                      | 10      |
| `sv_rcon_minfailures`                       | Dev / Debug                                                                      | 5       |
| `sv_rcon_minfailuretime`                    | Dev / Debug                                                                      | 30      |
| `sv_regeneration_wait_time`                 | Dev / Debug                                                                      | 20.0    |
| `sv_rejectClientConnects`                   | Dev / Debug                                                                      | 0       |
| `sv_rejectConnections`                      | Dev / Debug                                                                      | 0       |
| `sv_robust_explosions`                      | Dev / Debug                                                                      | 1       |
| `sv_scarySnapDeltaPrints`                   | Dev / Debug                                                                      | 50      |
| `sv_screenShake_enabled`                    | Dev / Debug                                                                      | 1       |
| `sv_script_think_interval`                  | Dev / Debug                                                                      | 0.1     |
| `sv_sendPlaylists`                          | Dev / Debug                                                                      | 1       |
| `sv_separate_freq_change_prop_send`         | Dev / Debug                                                                      | 1       |
| `sv_shiftPlayerSimTimeBackwards`            | Dev / Debug                                                                      | 1       |
| `sv_showClientTickCmds`                     | Dev / Debug                                                                      | 0       |
| `sv_showLargeSnapshotSize`                  | Dev / Debug                                                                      | 10000   |
| `sv_showLargeSnapshots`                     | Dev / Debug                                                                      | 0       |
| `sv_showUserCmds`                           | Dev / Debug                                                                      | 0       |
| `sv_show_placement_help_in_preview`         | Dev / Debug                                                                      | 0       |
| `sv_showents`                               | Dev / Debug                                                                      | 0       |
| `sv_showfiredbullets`                       | Dev / Debug                                                                      | 0       |
| `sv_showhitboxes`                           | Dev / Debug                                                                      | -1      |
| `sv_showlagcompensation`                    | Dev / Debug                                                                      | 0       |
| `sv_shutdown`                               | 关闭服务器，与stop效果等同                                               |         |
| `sv_single_core_dedi`                       | Engine Debug，强制服务端进程使用单核                                                                      | 0       |
| `sv_skyname`                                | Dev / Debug                                                                      |         |
| `sv_soundscape_printdebuginfo`              | Dev / Debug                                                                      |         |
| `sv_specaccelerate`                         | Dev / Debug                                                                      | 1000.0  |
| `sv_specnoclip`                             | Dev / Debug                                                                      | 1       |
| `sv_specspeed`                              | Dev / Debug                                                                      | 5       |
| `sv_stats`                                  | Dev / Debug                                                                      | 1       |
| `sv_stressbots`                             | Dev / Debug                                                                      | 1       |
| `sv_strugglecheck`                          | Dev / Debug                                                                      | 1.016   |
| `sv_teststepsimulation`                     | Dev / Debug                                                                      | 0       |
| `sv_thinktimecheck`                         | Dev / Debug                                                                      | 0       |
| `sv_threaded_post_process_ai`               | Dev / Debug                                                                      | 1       |
| `sv_threaded_post_process_players`          | Dev / Debug                                                                      | 1       |
| `sv_turbophysics`                           | Dev / Debug                                                                      | 1       |
| `sv_turbophysics_player`                    | Dev / Debug                                                                      | 1       |
| `sv_unnecessaryConnectDelay`                | Dev / Debug                                                                      | 60      |
| `sv_updaterate_mp`                          | 此指令在Convar全局变量中已经提及，此处不再赘述                                                                      | 20      |
| `sv_updaterate_sp`                          | Dev / Debug                                                                      | 20      |
| `sv_useReputation`                          | Dev / Debug                                                                      | 1       |
| `sv_use_edgefriction`                       | Dev / Debug                                                                      | 1       |
| `sv_usercmd_before_entities`                | Dev / Debug                                                                      | 1       |
| `sv_usercmd_fairness_dediOnly`              | Dev / Debug                                                                      | 0       |
| `sv_usercmd_max_queued`                     | Dev / Debug                                                                      | 40      |
| `sv_usercmd_num_per_iteration`              | Dev / Debug                                                                      | 1       |
| `sv_usercmd_shuffle_players`                | Dev / Debug                                                                      | 1       |
| `sv_visiblemaxplayers`                      | Dev / Debug                                                                      | -1      |
| `sv_visualizetraces`                        | Dev / Debug | 0       |
| `sv_visualizetraces_duration`               | Dev / Debug                                                                      | 0.5     |
| `sv_voiceDebug`                             | Dev / Debug                                                                      | 0       |
| `sv_voiceEcho`                              | Dev / Debug                                                                      | 0       |
| `sv_voiceenable`                            | Dev / Debug                                                                      | 1       |
| `sv_warnAboutCmdNumJumps`                   | Dev / Debug                                                                      | 20      |
| `sv_weapon_despawn_time`                    | 武器掉落在地面后经多少秒消失                                                                      | 90      |
| `sv_writeSendTableStreamFile`               | Dev / Debug                                                                       |         |
