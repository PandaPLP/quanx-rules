# 网络分流规则与 Loon 插件

这个仓库保存 Quantumult X 和 Loon 使用的网络规则。仓库是公开的，请勿提交订阅地址、节点密码、证书或私钥。

## 文件说明

- [`apple-services.list`](apple-services.list)：Quantumult X 的 Apple 相关服务分流规则，规则将列出的域名交给代理策略；是否正在使用需要在 Quantumult X 中确认。
- [`loon/AppleFlow-PROXY-fixed.plugin`](loon/AppleFlow-PROXY-fixed.plugin)：Loon 的 AppleFlow 兼容修正版，将插件中的 PROXY 绑定到 Loon 中选择的策略。包含 Siri 直连和 Apple Intelligence 等服务的分流规则。基于 [AppleFlow](https://github.com/Kianuni/AppleFlow)，原作者 Kianuni；许可说明保留在插件中。

## 使用与维护

导入 Loon 插件时，将插件的 PROXY 绑定到需要的策略组。配置中的规则不等于实际命中结果；使用时请在 Loon 的请求记录中核对。两份文件分别针对不同客户端，不保证互相等价。

现有文件路径可能已被客户端订阅使用；移动或重命名前请先检查并更新引用。规则会随服务变化而失效，修改后应测试，必要时恢复原版本。
