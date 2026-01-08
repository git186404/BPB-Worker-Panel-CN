# :material-cog-outline:{ .md .middle } Warp 常规设置

这些设置适用于 **Warp** 和 **Warp Pro** 订阅。

![Warp 常规设置](../images/warp-settings.jpg)

## 远程 DNS (Remote DNS)

出于性能和兼容性考虑，Warp 远程 DNS 只能是 IPv4 类型。默认 DNS 是 Cloudflare 公共 DNS，它是完美的选择。如果您坚持要更改，强烈建议使用 Cloudflare DNS 服务器，因为它们与 Cloudflare Warp 配合使用时具有最佳的兼容性和效率，例如：

- 1.1.1.2, 1.0.0.2 (Cloudflare 安全 DNS)
- 1.1.1.3, 1.0.0.3 (Cloudflare 成人过滤 DNS)

## 端点 (Endpoints) - 扫描器

Warp 的端点功能类似于 VLESS 和 Trojan 的优选 IP。面板提供了一个扫描器，您可以在 Termux (Android)、Windows、macOS 或 Linux 上运行，并将结果输入此处。请注意，结果并非 100% 可靠，因此需要进行测试。另外请注意，在测试之前必须退出任何代理软件；如果您使用 v2rayN，应从系统托盘完全退出，仅清除代理是不够的。

!!! info "信息"
    - 端点格式为 `IP:端口` 或 `域名:端口`，每行输入一个。
    - 对于 IPv6 地址，请使用方括号括起来。参考以下示例：

    ```title="IPv4"
    123.45.8.6:1701
    ```
    ```title="IPv6"
    [2a06:98c1:3120::3]:939
    ```
    ```title="域名"
    engage.cloudflareclient:2408
    ```  

## 虚假 DNS (Fake DNS)

您可以为 Warp 配置启用虚假 DNS 以减少 DNS 延迟。不过请谨慎操作，因为它可能与某些应用程序不兼容或干扰系统 DNS。如果您不确定其功能，请避免启用。

## 启用 IPv6

如果您的运营商不支持 IPv6，请禁用它以优化 DNS 和代理性能。

## 最佳间隔 (Best Interval)

**Warp** 和 **Warp Pro** 订阅包含 **Best Ping**（最佳 Ping）配置。默认情况下，这些配置每 30 秒进行一次测试，以识别连接的最优配置或端点。在较慢的网络上，此间隔可能会导致视频串流或游戏时出现延迟。您可以在 10 到 90 秒之间调整该间隔。

## Warp 账号

更新账号会从 **Cloudflare** 获取新的 Warp 账号。此过程不会影响连接速度或其他设置。
