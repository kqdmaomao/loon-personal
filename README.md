# 自用 Loon 规则与插件

仓库按两个 Git 分支独立维护：

- [rules](https://github.com/kqdmaomao/loon-personal/tree/rules)：分流规则与可复制的配置片段。
- [plugins](https://github.com/kqdmaomao/loon-personal/tree/plugins)：Loon 插件、JavaScript 和安装说明。

这是公开仓库，适合 Loon 使用无需登录的 Raw 下载地址。完整手机配置、账号 Cookie、代理订阅、MITM 证书及私钥/密码请保留在本地，不提交到这里。

## NodeSeek 自动签到

插件链接（在 Loon 中添加插件）：

https://raw.githubusercontent.com/kqdmaomao/loon-personal/plugins/NodeSeek.plugin

JS 链接（在 Loon 中从 URL 下载或直接作为脚本路径）：

https://raw.githubusercontent.com/kqdmaomao/loon-personal/plugins/nodeseek_checkin.js

### 安装

1. 在 Loon 添加上方插件 URL。它包含浏览器凭证获取、每日签到和手动签到三个条目。
2. 如果已经导入先前的 NodeSeek 合并配置，先删除或关闭那三条重复脚本，再添加本插件，避免双重定时执行。
3. 开启 Loon 与 MITM，确认现有 Loon 证书已完全信任。沿用证书，不用重新生成。
4. 用 Safari 登录 `https://www.nodeseek.com/`，通过网页验证后刷新首页，保存浏览器凭证。
5. 执行“NodeSeek 手动签到”，看到成功或已签到提示后到论坛核对结果，再关闭“NodeSeek Cookie 获取”条目。保留每日和手动签到。
6. 凭证失效后临时开启获取条目，重新登录和验证，再关闭获取条目。

默认手机当前时区每天 08:00 执行、随机奖励。非随机模式可将定时和手动条目的参数都改为 `random=false`。iOS 后台调度不保证每天准点。

### 凭证与排查

Cookie 在 Loon 本机保存，仅发往固定的 NodeSeek HTTPS 签到地址。新脚本不输出 Cookie、原始请求头、原始响应或异常，并禁止自动跟随重定向。捕获脚本放行原请求。

401 需要重新登录；403 或非 JSON 响应可能是网页验证或节点问题，先用 Safari 访问论坛处理。失败不会写入当日成功记录。服务器明确成功或确认今天已签到才保存完成记录。

清除本脚本的本地凭证：将手动条目的参数临时改为 `action=clear`，运行一次后恢复 `random=true`。只删除本脚本的数据，不清除其他脚本。

JS 为按此前功能描述重建的版本，39 个离线场景检查通过；真实账号需在手机上验证。旧对话生成文件未迁移，本版本未复用旧脚本存储键。
