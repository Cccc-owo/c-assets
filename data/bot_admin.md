# Bot 管理帮助

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
