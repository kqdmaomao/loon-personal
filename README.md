# 自用 Loon 规则与插件

仓库按两个 Git 分支独立维护：

- [rules](https://github.com/kqdmaomao/loon-personal/tree/rules)：分流规则与可复制的配置片段。
- [plugins](https://github.com/kqdmaomao/loon-personal/tree/plugins)：Loon 插件、JavaScript 和安装说明。

这是公开仓库，适合 Loon 使用无需登录的 Raw 下载地址。完整手机配置、账号 Cookie、代理订阅、MITM 证书及私钥/密码请保留在本地，不提交到这里。

## 当前规则

[NodeSeek.lsr](https://raw.githubusercontent.com/kqdmaomao/loon-personal/rules/NodeSeek.lsr) 只含 NodeSeek 域名匹配。添加为 Loon 远程规则时，请自行选择有效策略组，例如现有的“美国”。

原手机配置已包含 `DOMAIN-SUFFIX,nodeseek.com,美国`；已有此规则时无需再重复添加。

`NodeSeek_example.conf` 只是一段配置参考，不是完整手机配置，不应直接替代现有配置。远程规则和插件可以分别添加；插件本身不强制改变已有分流。

## 自用本地规则迁移

按 2026-10-12 手机截图保留 7 条规则的原匹配类型，按策略分成两个订阅：

| 文件 | 条数 | 在 Loon 中选择的策略 |
|---|---:|---|
| [Personal_DIRECT.lsr](https://raw.githubusercontent.com/kqdmaomao/loon-personal/rules/Personal_DIRECT.lsr) | 30 | DIRECT |
| [Personal_US.lsr](https://raw.githubusercontent.com/kqdmaomao/loon-personal/rules/Personal_US.lsr) | 6 | 美国（现有策略组） |
| [Personal_DE.lsr](https://raw.githubusercontent.com/kqdmaomao/loon-personal/rules/Personal_DE.lsr) | 7 | 德国（现有策略组） |

DIRECT：`DOMAIN-KEYWORD,luxshare`、`DOMAIN-KEYWORD,emby.789256.xyz`，另加香港银行 App 相关域名 26 条直连（汇丰、恒生、中银香港、渣打、星展、花旗、东亚、工银亚洲、建行亚洲、招商永隆、富邦、大新、信银国际、OCBC、ZA Bank、WeLab、livi、天星、Mox、蚂蚁银行、iFAST、Wise），以及兴业银行 2 条（cib.com.cn、95561.com.cn），域名清单见文件内按银行分组的注释。

美国：`DOMAIN-KEYWORD,younoair.de`、`DOMAIN-KEYWORD,lite.liminalnet.com`、`DOMAIN-KEYWORD,lite.cn2gias.uk`、`DOMAIN-SUFFIX,api.199347.xyz`、`DOMAIN-SUFFIX,nodeseek.com`、`DOMAIN-KEYWORD,dqx99999`。

德国：Bybit App 相关域名 7 条（`bybit.com`、`bytick.com`、`byhkbit.com`、`bybit-tr.com`、`bybit.kz`、`bybit.nl`、`bybit.id`）。

在 Loon 的订阅规则入口分别添加两个 Raw 链接，设置上表对应策略，并将这两份自用订阅置于其它规则订阅之前。`Personal_US.lsr` 已包含 NodeSeek，无需再重复添加单独的 `NodeSeek.lsr`。

上传只是备份和提供订阅文件，不会自动修改手机的本地规则。迁移前先备份原配置；保留本地规则时本地规则仍优先，不能据此验证订阅是否命中。确认文件下载、策略设置正确后，如要迁移，再删除对应的 7 条本地规则，并在请求详情中核对实际命中的规则和策略；异常时恢复本地规则。

[官方匹配优先级](https://nsloon.app/docs/Rule/)为：本地规则 > 插件规则 > 订阅规则。因此搬为订阅后相对插件的优先级会改变；把订阅排在最上面也不能超过插件。若需要严格保留原优先级，可仅将这里作为备份，继续使用手机本地规则。
