# AppleFlow Loon 插件说明

## 这是什么

[AppleFlow-PROXY-fixed.plugin](AppleFlow-PROXY-fixed.plugin) 是基于 [Kianuni / AppleFlow](https://github.com/Kianuni/AppleFlow) 的 Loon 兼容修正版，用于为列出的 Apple、Siri 和 AI 服务设置不同的分流策略。它不是上游官方发行版；原作者及 MIT 许可保留在插件文件内。

当前文件只有 General 和 Rule 配置，没有脚本、重写或 MITM 配置。规则命中不等于 Apple Intelligence 功能、设备资格或所有网络请求已验证成功。

## 读懂规则

- `DOMAIN`：匹配指定的完整域名。
- `DOMAIN-SUFFIX`：匹配指定域名及其子域名。
- `DIRECT`：直连。
- `PROXY`：交给插件在 Loon 中绑定的策略；它不是写死的具体节点。

例如 `DOMAIN-SUFFIX, siri.apple.com, DIRECT` 是对该域名及子域名设置直连；`DOMAIN-SUFFIX, openai.com, PROXY` 是交给插件绑定的代理策略。

## 配置分组

### General：与系统服务相关的设置

- `skip-proxy = guzzoni.apple.com`：让该域名绕过 HTTP Proxy；这不等于绕过所有 VPN 或所有 Loon 功能。
- `real-ip`：为列出的 Siri、Apple 系统服务及推送相关域名返回真实 IP，而不是 Fake IP；真实 IP 不等于一定直连。

### 直连规则

`guzzoni.apple.com`、`siri.apple.com`、`dejavu.apple.com`、`sequoia.apple.com` 和 `smoot.apple.com` 按文件中各自的精确或后缀匹配方式设为 DIRECT。具体完整范围以插件文件为准。

### 代理规则

1. Apple 相关：位置、issuer、ropes、iCloud mask、app.apple.com 和 Apple relay 等域名交给 PROXY。部分后缀覆盖范围较广，不应假设只影响单一 AI 功能。
2. AI 服务相关：OpenAI、ChatGPT、Sora、Google Lens/Gemini/AI Studio、Anthropic/Claude 等列出的域名交给 PROXY；具体是精确匹配还是后缀匹配，以插件文件为准。

这些是插件作者归纳的分流意图，并非逐域名的官方用途或功能效果验证。

## 使用与检查

1. 在 Loon 中导入原文件，绑定插件的 PROXY 到所需策略组；策略组内再选择节点。
2. 在请求记录中检查目标域名实际命中的规则及策略。截图或分享日志前，请遮盖账号、令牌、订阅地址和其他私人信息。
3. 如果效果不符合预期，先检查插件是否开启、策略绑定、其他规则的优先级及实际节点；不要仅凭一个检测页面的结果断定全部功能正常。
4. 修改前保留可恢复版本，一次改一项并测试。不要移动或重命名原插件，否则已有导入链接可能失效。

[官方 General 文档](https://nsloon.app/docs/General/) · [规则优先级](https://nsloon.app/docs/Rule/) · [插件文档](https://nsloon.app/docs/Plugin/)
