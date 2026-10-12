# 自用 Loon 规则与插件

仓库按两个 Git 分支独立维护：

- [rules](https://github.com/kqdmaomao/loon-personal/tree/rules)：分流规则与可复制的配置片段。
- [plugins](https://github.com/kqdmaomao/loon-personal/tree/plugins)：Loon 插件、JavaScript 和安装说明。

这是公开仓库，适合 Loon 使用无需登录的 Raw 下载地址。完整手机配置、账号 Cookie、代理订阅、MITM 证书及私钥/密码请保留在本地，不提交到这里。

## 当前规则

[NodeSeek.lsr](https://raw.githubusercontent.com/kqdmaomao/loon-personal/rules/NodeSeek.lsr) 只含 NodeSeek 域名匹配。添加为 Loon 远程规则时，请自行选择有效策略组，例如现有的“美国”。

原手机配置已包含 `DOMAIN-SUFFIX,nodeseek.com,美国`；已有此规则时无需再重复添加。

`NodeSeek_example.conf` 只是一段配置参考，不是完整手机配置，不应直接替代现有配置。远程规则和插件可以分别添加；插件本身不强制改变已有分流。
