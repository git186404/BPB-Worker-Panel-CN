# :material-playlist-check:{ .md .middle } Warp 订阅

![Warp 订阅](../images/warp-sub.jpg)

此订阅包括：

- 一个 **Warp** 配置，节点 IP 来自您所在地区的 Cloudflare IP。
- 一个 **Warp on Warp (WoW)** 配置，节点 IP 来自海外 Cloudflare IP（主要是德国）。
- 一个 **Warp Best Ping** 配置，连接到最快的 Warp 配置。
- 一个 **WoW Best Ping** 配置，连接到最快的 WoW 配置。

默认情况下包含一个 Warp 和一个 WoW 配置。在 `Warp General`（Warp 常规）设置中编辑 `Endpoints`（端点）后，会根据指定的端点添加额外的 Warp 和 WoW 配置。

您可以下载 Warp WireGuard 配置的压缩包并将其导入 WireGuard 客户端。请注意，大多数运营商通常会屏蔽 Warp，因此请仅在您的网络环境允许 WireGuard 协议时使用。

为了获得最佳性能，请使用扫描器识别适合您运营商的端点。面板中提供了扫描脚本；您可以将其复制并在 Android 的 Termux 或 Linux 终端中运行。普通 Warp 订阅在某些运营商（如伊朗的 MTN-Irancell）上表现良好，但对于其他运营商，建议使用 **Warp Pro** 订阅。
