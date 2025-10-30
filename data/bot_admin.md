# Bot 管理帮助

## nonebot_plugin_admin

source: <https://github.com/yzyyz1387/nonebot_plugin_admin>

## 指令💻

**Tips:**

- 关于命令，对/sp这类`斜杠+英文`的命令做了保留，汉字命令去除了`/`若使用者担心错误触发，可下载源码自行修改`__init__.py`
- 群词云功能所用库 wordcloud 未写入依赖，请自行安装：`pip install wordcloud` 安装失败参考：[WordCloud 第三方库安装失败原因及解决方法](https://www.freesion.com/article/4756295761/)
- 一般情况下可正常使用，可能由于权重出现问题，matcher权重请自行查看代码
- 使用`开关状态`指令查看各功能状态，首次使用可能会下载100Mb+的`Chromium`，请耐心等待

```plaintext
【初始化】：
  群管初始化 ：初始化插件

【群管】：
权限：permission=SUPERUSER | GROUP_ADMIN | GROUP_OWNER
  禁言:
    禁 @某人 时间（s）[1,2591999]
    禁 时间（s）@某人 [1,2591999]
    禁 @某人 缺省时间则随机
    禁 @某人 0 可解禁
    解 @某人
    禁言时，该条消息中所有数字都会组合作为禁言时间，如：‘禁@某人 1哈2哈0哈’，则禁言120s
    
  全群禁言 若命令前缀不为空，请使用//all,若为空，需用 /all 来触发
    /all 
    /all 解
    
  改名片
    改 @某人 名片
    
  踢出：
    踢 @某人
  踢出并拉黑：
   黑 @某人
   
  撤回:
   撤回 (回复某条消息即可撤回对应消息)
   撤回 @user [(可选，默认n=5)历史消息倍数n] (实际检查的历史数为 n*19)
   
  设置精华
    回复某条消息 + 加精
  取消精华
    回复某条消息 + 取消精华
    
【头衔】
  改头衔
    自助领取：头衔 xxx 
    自助删头衔：删头衔
    超级用户更改他人头衔：头衔 @某人 头衔
    超级用户删他人头衔：删头衔 @某人

【管理员】permission=SUPERUSER | GROUP_OWNER
  gl+ @xxx 设置某人为管理员  
  管理员+ @xxx 设置某人为管理员
  管理员加 @xxx 设置某人为管理员
  加管理 @xxx 设置某人为管理员
  
  gl- @xxx 取消某人管理员
  管理员- @xxx 取消某人管理员
  管理员减 @xxx 取消某人管理员
  减管理 @xxx 取消某人管理员

  
【加群自动审批】：
群内发送 permission=GROUP_ADMIN | GROUP_OWNER | SUPERUSER
  查看词条 ： 查看本群审批词条   或/审批
  ct+ [词条] ：增加审批词条 或/审批+  
  词条+ [词条] ：增加审批词条 或/审批+
  ct- [词条] ：删除审批词条 或/审批-
  词条- [词条] ：删除审批词条 或/审批-
  按照黑名单自动拒绝：（当验证消息与黑名单内容匹配时，自动拒绝）
    添加示例：
      jj+管理员你好，请通过一下
      ctjj+管理员你好，请通过一下
      词条拒绝+管理员你好，请通过一下
      拒绝词条+管理员你好，请通过一下
      /spx+管理员你好，请通过一下
    删除示例：
      jj-管理员你好，请通过一下
      ctjj-管理员你好，请通过一下
      词条拒绝-管理员你好，请通过一下
      拒绝词条-管理员你好，请通过一下
      /spx-管理员你好，请通过一下

【superuser】：
  所有词条 ：  查看所有审批词条   或/su审批
  zdct+ [词条] ：增加审批词条 
  指定词条+ [群号] [词条] ：增加指定群审批词条
  指定词条加 [群号] [词条] ：增加指定群审批词条 或/su审批+
    zdct- [词条] ：删除审批词条
  指定词条- [群号] [词条] ：删除指定群审批词条 
  指定词条减 [群号] [词条] ：删除指定群审批词条 或/su审批- 
  自动审批处理结果将发送给superuser

【分群管理员设置】*分管：可以接受加群处理结果消息的用户
群内发送 permission=GROUP_ADMIN | GROUP_OWNER | SUPERUSER
  fg+ [user] ：user可用@或qq 添加分群管理员
  分管+ [user] ：user可用@或qq 添加分群管理员
  分管加 [user] ：user可用@或qq 添加分群管理员
  fg- [user] ：删除分群管理员
  分管- [user] ：删除分群管理员
  分管减 [user] ：删除分群管理员
  查看分管 ：查看本群分群管理员

群内或私聊 permission=SUPERUSER
  所有分管 ：查看所有分群管理员
  群管接收 ：打开或关闭超管消息接收（关闭则审批结果不会发送给superusers）
  
【群词云统计】
该功能所用库 wordcloud 未写入依赖，请自行安装
群内发送：
  记录本群 ： 开始统计聊天记录 permission=GROUP_ADMIN | GROUP_OWNER | SUPERUSER
  停止记录本群 ：停止统计聊天记录
  群词云 ： 发送词云图片
  更新mask : 更新mask图片
  增加停用词 停用词1 停用词2 ...
  删除停用词 停用词1 停用词2 ...
  停用词列表 ： 查看停用词列表

群发言排行
 - 日:
  - 日榜首：今日榜首, aliases={'今天谁话多', '今儿谁话多', '今天谁屁话最多'}
  - 日排行：今日发言排行, aliases={'今日排行榜', '今日发言排行榜', '今日排行'}
  - 昨日排行
 - 总
  - 总排行：排行, aliases={'谁话多', '谁屁话最多', '排行', '排行榜'}
 - 某人发言数
  - 日：今日发言数@xxx, aliases={'今日发言数', '今日发言', '今日发言量'}
  - 总：发言数@xxx, aliases={'发言数', '发言', '发言量'}
    
  
【被动识别】
涩图检测：
 - 图片检测偏向于涩图检测，90分以上色图禁言，其他基本不处理
 - 用户违禁一次等级+1 最高7级
 - 禁言时间（s）：
  - time_scop_map = {
        0: [0, 5*60],
        1: [5*60, 10*60],
        2: [10*60, 30*60],
        3: [30*60, 10*60*60],
        4: [10*60*60, 24*60*60],
        5: [24*60*60, 7*24*60*60],
        6: [7*24*60*60, 14*24*60*60],
        7: [14*24*60*60, 2591999]
    }

违禁词检测：
（如果要使用正则匹配，暂时需要用户自定编辑【机器人项目/config/违禁词.txt】，后续会优化，有需要请提issue催更）
 - 支持正则表达式(使用用制表符分隔)
 - 可定义触发违禁词操作(默认为禁言+撤回)
 - 可定义生效范围(排除某些群 or 仅限某些群生效)
 - 示例：
  - 加(群|君\S?羊|羣)\S*\d{6,}  $撤回$禁言$仅限123456789,987654321
  - 狗群主    $禁言$排除987654321

【功能开关】
群内发送：
  开关xx : 对某功能进行开/关  permission=SUPERUSER | GROUP_ADMIN | GROUP_OWNER
  开关状态 ： 查看各功能的状态
  xx in ：
    ['管理', '踢', '禁', '改', '基础群管']  #基础功能 踢、禁、改、管理员+-
    ['加群', '审批', '加群审批', '自动审批'] #加群审批
    ['词云', '群词云', 'wordcloud'] #群词云
    ['违禁词', '违禁词检测'] #违禁词检测
    ['图片检测', '图片鉴黄', '涩图检测', '色图检测'] #图片检测
    ['消息记录', '群消息记录', '发言记录'],
    ['早安晚安', '早安', '晚安'],
    ['广播消息', '群广播', '广播'],
    ['事件通知', '变动通知', '事件提醒'],
     ['防撤回', '防止撤回']
图片检测和违禁词检测默认关,其他默认开

【广播】permission = SUPERUSER
本功能默认关闭
   "发送【广播】/【广播+[消息]】可广播消息" 
   "发送【群列表】可查看能广播到的所有群" 
   "发送【排除列表】可查看已排除的群" 
   "发送【广播排除+】可添加群到广播排除列表" 
   "发送【广播排除-】可从广播排除列表删除群"
   "发送【广播帮助】可查看广播帮助"
   发送【开关广播】来开启/关闭（意义不大）
   
【特殊事件提醒】
包括管理员变动，加群退群等...
待完善
  发送【开关事件通知】来开启/关闭功能 permission=SUPERUSER | GROUP_ADMIN | GROUP_OWNER


【防撤回】
默认关闭
 发送【开关防撤回】开启或关闭功能 permission=SUPERUSER | GROUP_ADMIN | GROUP_OWNER

【群员清理】
群内发送 permission=SUPERUSER | GROUP_OWNER
该功能暂不被开关控制
发送【群员清理】可根据[等级] 或 [发言时间] 清理群员
在执行此命令时，当前群会对此操作加锁，防止其他人同时操作，如果出现问题，可执行【清理解锁】来手动解锁
```

## nonebot-plugin-updater

Source: <https://github.com/hanasa2023/nonebot-plugin-updater/>

### 🤖 指令表

⚠️ 此处示例中的"/"为 nb 默认的命令开始标志，若您设置了另外的标志，则请使用您设置的标志作为开头

|             指令              |    权限    | 需要@ |                           说明                            |               示例                |
| :---------------------------: | :--------: | :---: | :-------------------------------------------------------: | :-------------------------------: |
|        `获取插件列表`         |     无     |  无   |                   获取已安装的插件列表                    |          `/获取插件列表`          |
|        `检查插件更新`         |     无     |  无   |                    检查可用的插件更新                     |          `/检查插件更新`          |
| `更新插件 <需要更新的插件名>` | SUPERUSERS |  无   | 更新插件。若需更新的插件名为`all`，则更新所有已安装的插件 | `/更新插件 nonebot-pluign-status` |
| `安装插件 <需要安装的插件名>` | SUPERUSERS |  无   |                       安装指定插件                        | `/安装插件 nonebot-pluign-status` |
| `卸载插件 <需要卸载的插件名>` | SUPERUSERS |  无   |                       卸载指定插件                        | `/卸载插件 nonebot-pluign-status` |
|           `关闭nb`            | SUPERUSERS |  无   |                        远程关闭 nb                        |             `/关闭nb`             |
|           `重启nb`            | SUPERUSERS |  无   |                        远程重启 nb                        |             `/重启nb`             |

## nonebot-plugin-access-control

source: <https://github.com/bot-ssttkkl/nonebot-plugin-access-control>

### 指令一览

进行控制的指令为`/ac`，仅超级用户可用。（通过在配置文件中设置`SUPERUSERS`变量可设置超级用户）

（注意：0.3.0版本对指令进行了一次大的更改）

- 帮助
  - `/ac help`：显示此帮助
- 权限控制
  - `/ac permission allow --sbj <主体> --srv <服务>`：为主体启用服务
  - `/ac permission deny --sbj <主体> --srv <服务>`：为主体禁用服务
  - `/ac permission rm --sbj <主体> --srv <服务>`：为主体删除服务权限配置
  - `/ac permission ls`：列出所有已配置的权限
  - `/ac permission ls --sbj <主体>`：列出主体已配置的服务权限
  - `/ac permission ls --srv <服务>`：列出服务已配置的主体权限
  - `/ac permission ls --sbj <主体> --srv <服务>`：列出主体与服务已配置的权限
- 流量限制
  - `/ac limit add --sbj <主体> --srv <服务> --limit <次数> --span <时间间隔> [--overwrite]`：为主体与服务添加限流规则
  - `/ac limit rm <规则ID>`：删除限流规则
  - `/ac limit ls`：列出所有已配置的限流规则
  - `/ac limit ls --sbj <主体>`：列出主体已配置的限流规则
  - `/ac limit ls --srv <服务>`：列出服务已配置的限流规则
  - `/ac limit ls --sbj <主体> --srv <服务>`：列出主体与服务已配置的限流规则
  - `/ac limit reset`：重置限流计数
- 服务查看
  - `/ac service ls`：列出所有服务与子服务层级
  - `/ac service ls --srv <服务>`：列出服务的子服务层级
- 主体测试
  - `/ac subject`：列出消息发送者的所有主体

其中`<服务>`的格式如下：

- `nonebot`：对整个NoneBot进行开关
- `<插件名>`：对整个插件进行开关
- `<插件名>.<子服务名>.<子服务名>.....<子服务名>`：对插件内的某个子服务进行开关（需参照下文对插件进行配置）

## nonebot-plugin-fakemsg

Source: <https://github.com/Cvandia/nonebot-plugin-fakemsg>

### ⭐ 使用

> 指令如下

![效果图1](https://github.com/Cvandia/nonebot-plugin-fakemsg/raw/main/res/test_1.jpg)

> 效果如下

![效果图2](https://github.com/Cvandia/nonebot-plugin-fakemsg/raw/main/res/test_2.jpg)

> 效果如下

![效果图3](https://github.com/Cvandia/nonebot-plugin-fakemsg/raw/main/res/test_3.jpg)

**支持识别`@xxx`的消息,如`@群友1 说你好啊|@群友2 我很好！`**

## nonebot-plugin-revoke

source: <https://github.com/bot-ssttkkl/nonebot-plugin-revoke>

### 使用方法

对某条消息**回复**`/revoke`或`/撤回`

（注意：仅超级用户可用）

## nonebot-plugin-parser

source: <https://github.com/fllesser/nonebot-plugin-parser>

### 指令表

|   指令   |         权限          | 需要@ | 范围  |   说明   |
| :------: | :-------------------: | :---: | :---: | :------: |
| 开启解析 | SUPERUSER/OWNER/ADMIN |  是   | 群聊  | 开启解析 |
| 关闭解析 | SUPERUSER/OWNER/ADMIN |  是   | 群聊  | 关闭解析 |

## nonebot-plugin-autoreply

source: <https://github.com/lgc-NB2Dev/nonebot-plugin-autoreply>

### 💬 指令

`重载自动回复`

此命令用于重载自动回复配置，仅 `SUPERUSER` 可以执行

## nonebot-plugin-better-broadcast

source: <https://github.com/captain-wangrun-cn/nonebot-plugin-better-broadcast>

### 指令表

| 指令 | 权限 | 需要@ | 范围 | 说明 |
|:-----:|:----:|:----:|:----:|:----:|
| 发送广播 | 主人 | 否 | 私聊、群聊 | 顾名思义 |
| 撤回广播 | 主人 | 否 | 私聊、群聊 | 撤回上一条广播的消息 |

## nonebot-plugin-add-friends

source: <https://github.com/hakunomiko/nonebot-plugin-add-friends>

### 指令表

| 指令 | 权限 | 需要@ | 范围 | 说明 |
|:-----:|:----:|:----:|:----:|:----:|
| 查看申请 | 主人 | 否 | 私聊 | 查看待处理申请 |
| 同意/拒绝申请 <QQ号/群号> | 主人 | 否 | 私聊 | 同意/拒绝申请 |
| 同意/拒绝全部申请 | 主人 | 否 | 私聊 | 同意/拒绝全部申请 |
