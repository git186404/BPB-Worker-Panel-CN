# :material-playlist-check:{ .md .middle } 分片订阅 (Fragment)

![分片订阅](../images/fragment-sub.jpg)

!!! tip "**分片 (Fragment) 配置的优势**"
    - 即使自定义域名或 Worker 域名被运营商屏蔽，也能保持连接。
    - 增强所有运营商网络的稳定性和速度，特别是那些 Cloudflare 连接受阻的网络。

## 适用于 Xray 的分片

这适用于使用 Xray 内核的客户端，如 v2rayNG、MansaNG 和 v2rayN PRO。导入的配置名称中会带有 `F` 标志。此订阅提供的配置数量与 **Normal**（普通）订阅相同，并增强了可在面板中调整的分片设置，此外还提供了 **Best Fragment**（最佳分片）和 **Workerless**（无 Worker）配置。任何面板设置更改都将在订阅更新时应用于所有配置。

???+ question "什么是 Workerless 配置？"
    Workerless 配置无需通过 Worker 即可解锁许多受限网站和应用（如 YouTube、Twitter、Google Play...）。请注意，此配置不会更改您的本地 IP，因此请避免在需要安全或匿名性的活动中使用它。除了链式代理 (Chain Proxy) 外，分片设置更改也适用于此配置。

???+ question "什么是 Best Fragment 配置？"
    Best Fragment 配置会测试 18 种不同的分片设置，并根据您运营商的性能选择最快的一种。这些模式旨在覆盖所有主要场景，配置每 30 秒测试一次所有模式并连接到最优模式。高级分片设置[在此说明](../configuration/fragment.md)。

## 适用于 sing-box 的分片

从 1.12.0 版本开始，sing-box 内核及相关客户端支持分片功能。您可以通过 sing-box 官方客户端（如 husi）或内置了 sing-box 内核的 v2rayN 使用此订阅。
