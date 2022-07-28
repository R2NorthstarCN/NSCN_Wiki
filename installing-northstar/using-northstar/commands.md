# 命令

## 开启控制台

所有的命令，再无特殊说明的情况下都应在控制台输入. 为了启动它, 按下 `` ` `` (该键位于 `TAB` 上方).\
注意控制台只能被位于英文模式下的键盘输入触发 (ANSI US, ISO UK, ...).

例如德文键盘中此键位于 `BACKSPACE` 左侧，但是按下此键无法触发控制台.

为了正确触发控制台，请在游戏 **运行前** 将键盘布局切换至 英语 (美国) .

<!--
注：译者目前未在任何中文键盘上遇到此问题，但以防万一任保留此处
-->

### 重绑定触发按键
请确保您的北极星是最新版本.
控制台仅可绑定在 ```"`"``` 或功能键 ```"F1" - "F12"``` 中.

定位至 `Controls > Settings > Key Binds` 使用其中的 `"Toggle Developer Console"` 绑定控制台.

---

如果 `"Toggle Developer Console"` 选项不存在，您可能会需要禁用所有非 `Northstar.` 开头的Mod 或者手动绑定该按键.

如需手动绑定，在 官服/北极星 均关闭的情况下，定位到 `My Documents\Respawn\Titanfall2\local\` 中的 `settings.cfg`.\
寻找包含 `toggleconsole` 的那一行, 例如：

```txt
bind "`" "toggleconsole"
```

并将 `` ` `` 替换为您需要的按键. 比如说您想以 `F5` 打开控制台, 将该行更改为

```txt
bind "F5" "toggleconsole"
```

## 命令列表

### Northstar Commands

| 命令                              | 描述                                                                                                 | 接受值                                           |
| ------------------------------------ | ----------------------------------------------------------------------------------------------------------- | ----------------------------------------------- |
| `ns_masterserver_hostname`           | Masterserver URL                                                                                            | 默认为 `https://nscn.wolf109909.top`                |
| `ns_auth_allow_insecure`             | 允许客户端在不与主服务器验证的情况下加入游戏                                                | `0` / `1`                                       |
| `connect`                            | 直接连接至某一Northstar 服务器                                                                  | `<ip address>:<port>` 例: `localhost:37015`     |
| `reload_mods`                        | 重载 mods                                                                                                 |                                                 |
| `ns_disallowed_tacticals`            | 禁止使用的铁驭技能                                                                | 例: `"mp_ability_grapple,mp_ability_heal"` |
| `ns_disallowed_tactical_replacement` | 替换禁止使用的铁驭技能为                                               | 例: `"mp_ability_grapple"`                      |
| `give mp_weapon_peacekraber`         | 给予你 peacekraber （和平捍卫者?）                                                                                       |                                                 |
| `r_latencyflex`                      | 启用 [LatencyFleX](../../using-northstar/playing-on-linux/#latencyflex) (Linux-only, 默认启用) | `0` / `1`                                       |

### Useful dev commands

需要 `sv_cheats 1`

Command|作用
-|-
`thirdperson`|第三人称模式
`script DevSpawnTitan()`|生成你的泰坦
`script SetGameEndTime(1200.0)`|将剩余比赛时间设置为1200秒
`ent_create npc_soldier`|在准星处生成步枪兵
`ent_create npc_stalker`|在准星处生成幽灵战士
`ent_create npc_spectre`|在准星处生成潜行者
`ent_create npc_titan`|在准星处生成泰坦 (Warning as of v1.4.0, this crashes your game if you don't have your own titan)
`ent_create npc_marvin`|在准星处生成马文
`ent_fire !picker setteam 2`|Sets entity at crosshair to team 2

### Server commands

| 命令                                    | 描述                                                           | 默认值 |
| ------------------------------------------- | --------------------------------------------------------------------- | ------- |
| `sv_cheats`                                 | Whether players can use cheat commands (i.e. noclip) .                 | 0       |
| `sv_AllWaysSupportsSaveRestore`             |                                                                       | 0       |
| `sv_allTicksFinal`                          |                                                                       | 0       |
| `sv_allowSendTableTransmitToClients`        |                                                                       | 1       |
| `sv_alltalk`                                | 是否启用全局语音.             | 0       |
| `sv_balanceTeams`                           | 服务器是否会在对局间尝试平衡队伍. | 1       |
| `sv_bounds_show_errors`                     |                                                                       | 0       |
| `sv_clampPlayerFrameTime`                   |                                                                       | 0       |
| `sv_clockcorrection`                        |                                                                       | 1       |
| `sv_clockcorrection_msecs`                  |                                                                       | 75      |
| `sv_compressPlaylists`                      |                                                                       | 1       |
| `sv_connectingClientDelay`                  |                                                                       | 3       |
| `sv_debug_deferred_trace`                   |                                                                       | 0       |
| `sv_debug_deferred_trace_overlay`           |                                                                       | 0       |
| `sv_debug_prop_send`                        |                                                                       | 0       |
| `sv_debugmanualmode`                        |                                                                       | 0       |
| `sv_disconnectOnTooManySnapshotFrames`      |                                                                       | 1       |
| `sv_dumpstringtables`                       |                                                                       | 0       |
| `sv_earlyPersistenceRead`                   |                                                                       | 0       |
| `sv_edgefriction`                           |                                                                       | 2       |
| `sv_everyThirdTick`                         |                                                                       | 0       |
| `sv_extra_client_connect_time`              |                                                                       | 60      |
| `sv_gravity`                                | 服务器重力                                 | 750     |
| `sv_hibernate_ms`                           |                                                                       | 5       |
| `sv_hibernate_ms_vgui`                      |                                                                       | 5       |
| `sv_hibernate_postgame_delay`               |                                                                       | 5       |
| `sv_hibernate_when_empty`                   | 服务器是否在无人时休眠.                        | 0       |
| `sv_instancebaselines`                      |                                                                       | 1       |
| `sv_kickPlayersTooFarInFuture`              | Whether to kick players whose internal time is too far in the future.  | 1       |
| `sv_lerpAnims`                              |                                                                       | 1       |
| `sv_lobbyType`                              |                                                                       | 1       |
| `sv_massreport`                             |                                                                       | 0       |
| `sv_maxUserCmdsPerPlayerPerFrame`           |                                                                       | 10      |
| `sv_max_prop_data_dwords_lobby`             |                                                                       | 100000  |
| `sv_max_prop_data_dwords_multiplayer`       |                                                                       | 125000  |
| `sv_max_prop_data_dwords_singleplayer`      |                                                                       | 300000  |
| `sv_max_props_lobby`                        |                                                                       | 50000   |
| `sv_max_props_multiplayer`                  |                                                                       | 75000   |
| `sv_max_props_singleplayer`                 |                                                                       | 200000  |
| `sv_max_snapshots_lobby`                    |                                                                       | 100     |
| `sv_max_snapshots_multiplayer`              |                                                                       | 300     |
| `sv_max_snapshots_singleplayer`             |                                                                       | 10      |
| `sv_maxclientframes`                        |                                                                       | 300     |
| `sv_maxrate`                                |                                                                       | 0       |
| `sv_maxroutable`                            |                                                                       | 1200    |
| `sv_maxupdaterate`                          |                                                                       | 60      |
| `sv_minrate`                                |                                                                       | 128000  |
| `sv_minupdaterate`                          |                                                                       | 20      |
| `sv_noclipaccelerate`                       | noclip 加速度.                                 | 10000   |
| `sv_noclipduringpause`                      | 服务器暂停时是否进入noclip状态.                                 | 0       |
| `sv_noclipspeed`                            |  noclip 速度.                                                 | 5       |
| `sv_normalSimulationCommandThreshold`       |                                                                       | 3       |
| `sv_parallel_sendsnapshot`                  |                                                                       | 1       |
| `sv_partyDediOnly`                          |                                                                       | 0       |
| `sv_pausable`                               |                                                                       | 0       |
| `sv_physics_maxvelocity`                    |                                                                       | 4000.0  |
| `sv_playerNameAppendCheater`                |                                                                       | 1       |
| `sv_playerSimTimeBuffer`                    |                                                                       | 0       |
| `sv_precacheinfo`                           |                                                                       |         |
| `sv_printClockCorrections`                  |                                                                       | 0       |
| `sv_printClockTiming`                       |                                                                       | 0       |
| `sv_props_funnel_into_portals`              |                                                                       | 1       |
| `sv_props_funnel_into_portals_deceleration` |                                                                       | 2.0f    |
| `sv_querylimit_per_sec`                     |                                                                       | 10      |
| `sv_quota_stringcmdspersecond`              |                                                                       | 60      |
| `sv_rcon_banpenalty`                        |                                                                       | 0       |
| `sv_rcon_log`                               | 是否记录 RCON 命令.                                          | 1       |
| `sv_rcon_maxfailures`                       |                                                                       | 10      |
| `sv_rcon_minfailures`                       |                                                                       | 5       |
| `sv_rcon_minfailuretime`                    |                                                                       | 30      |
| `sv_regeneration_wait_time`                 |                                                                       | 20.0    |
| `sv_rejectClientConnects`                   |                                                                       | 0       |
| `sv_rejectConnections`                      |                                                                       | 0       |
| `sv_robust_explosions`                      |                                                                       | 1       |
| `sv_scarySnapDeltaPrints`                   |                                                                       | 50      |
| `sv_screenShake_enabled`                    |                                                                       | 1       |
| `sv_script_think_interval`                  |                                                                       | 0.1     |
| `sv_sendPlaylists`                          |                                                                       | 1       |
| `sv_separate_freq_change_prop_send`         |                                                                       | 1       |
| `sv_shiftPlayerSimTimeBackwards`            |                                                                       | 1       |
| `sv_showClientTickCmds`                     |                                                                       | 0       |
| `sv_showLargeSnapshotSize`                  |                                                                       | 10000   |
| `sv_showLargeSnapshots`                     |                                                                       | 0       |
| `sv_showUserCmds`                           |                                                                       | 0       |
| `sv_show_placement_help_in_preview`         |                                                                       | 0       |
| `sv_showents`                               |                                                                       | 0       |
| `sv_showfiredbullets`                       |                                                                       | 0       |
| `sv_showhitboxes`                           |                                                                       | -1      |
| `sv_showlagcompensation`                    |                                                                       | 0       |
| `sv_shutdown`                               | 停止服务器.                                                |         |
| `sv_single_core_dedi`                       |                                                                       | 0       |
| `sv_skyname`                                |                                                                       |         |
| `sv_soundscape_printdebuginfo`              |                                                                       |         |
| `sv_specaccelerate`                         |                                                                       | 1000.0  |
| `sv_specnoclip`                             |                                                                       | 1       |
| `sv_specspeed`                              |                                                                       | 5       |
| `sv_stats`                                  |                                                                       | 1       |
| `sv_stressbots`                             |                                                                       | 1       |
| `sv_strugglecheck`                          |                                                                       | 1.016   |
| `sv_teststepsimulation`                     |                                                                       | 0       |
| `sv_thinktimecheck`                         |                                                                       | 0       |
| `sv_threaded_post_process_ai`               |                                                                       | 1       |
| `sv_threaded_post_process_players`          |                                                                       | 1       |
| `sv_turbophysics`                           |                                                                       | 1       |
| `sv_turbophysics_player`                    |                                                                       | 1       |
| `sv_unnecessaryConnectDelay`                |                                                                       | 60      |
| `sv_updaterate_mp`                          |                                                                       | 20      |
| `sv_updaterate_sp`                          |                                                                       | 20      |
| `sv_useReputation`                          |                                                                       | 1       |
| `sv_use_edgefriction`                       |                                                                       | 1       |
| `sv_usercmd_before_entities`                |                                                                       | 1       |
| `sv_usercmd_fairness_dediOnly`              |                                                                       | 0       |
| `sv_usercmd_max_queued`                     |                                                                       | 40      |
| `sv_usercmd_num_per_iteration`              |                                                                       | 1       |
| `sv_usercmd_shuffle_players`                |                                                                       | 1       |
| `sv_visiblemaxplayers`                      |                                                                       | -1      |
| `sv_visualizetraces`                        |                                                                       | 0       |
| `sv_visualizetraces_duration`               |                                                                       | 0.5     |
| `sv_voiceDebug`                             |                                                                       | 0       |
| `sv_voiceEcho`                              |                                                                       | 0       |
| `sv_voiceenable`                            |                                                                       | 1       |
| `sv_warnAboutCmdNumJumps`                   |                                                                       | 20      |
| `sv_weapon_despawn_time`                    |                                                                       | 90      |
| `sv_writeSendTableStreamFile`               |                                                                        |         |
