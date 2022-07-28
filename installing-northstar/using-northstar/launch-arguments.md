# 启动参数

这里展示的是北极星客户端新引入的启动参数, 其值应包括在 `ns_startup_args.txt` 或 `ns_startup_args_dedi.txt` 中.

|         参数         |               描述              |            接受值            |
| :----------------: | :---------------------------: | :-----------------------: |
|   `-disablelogs`   |          禁用日志与日志文件的写入         |                           |
|     `-vanilla`     |            阻止北极星的加载           |                           |
|    `-northstar`    |            启用北极星加载            |                           |
|    `-dedicated`    |       以独立服务器模式（无视频输出）启动       |                           |
|     `-language`    |           强制指定客户端的语言          |   语言字符串 例如: `portuguese`  |
| `-waitfordebugger` |        在调试程序附加到游戏之后再运行游戏      |                           |
|     `-profile=`    | 用一个特殊的配置文件夹. 默认值: R2Northstar | 例如: `-profile="dev mods"` |
| `-enablechathooks` |        为 Mod 启用chathook       |                           |

#### 起源自带的启动参数

|     参数     |     描述    | 接受值 |
| :--------: | :-------: | :-: |
|  `-novid`  | 禁用启动页介绍视频 |     |
| `-nosound` |  禁用所有游戏声音 |     |

#### `环境变量`

|  变量名  |                                 描述                                |     接受值    |
| :---: | :---------------------------------------------------------------: | :--------: |
| `LFX` | 启用 [LatencyFleX](../playing-on-linux.md#latencyflex) (Linux-only) | `0` or `1` |

``

``
