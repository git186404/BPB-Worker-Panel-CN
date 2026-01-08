# :material-cog-outline:{ .md .middle } 分片 (Fragment) 设置

分片 (Fragment) 方案通过对中间人 (MitM) 隐藏 SNI，几乎解决了 Cloudflare CDN 的优选 IP 问题。不过，设置应根据具体的运营商 (ISP) 来获取。另外请注意，虽然 sing-box 可以启用分片，但 sing-box 不使用这些分片设置，而是有自己的默认设置。

![分片设置](../images/fragment-settings.jpg)

默认设置如下：

- **长度 (Length)**: 100-200
- **间隔 (Interval)**: 1-1
- **数据包 (Packets)**: tlshello

您也可以根据网络状况切换分片模式进行测试。通常默认或 `Low`（低）模式即可。请注意，切换到 `Medium`（中）、`High`（高）或 `Severe`（严重）配置文件后，握手延迟会变高，但在极端环境下可以获得更好、更稳定的连接。`Best Fragment`（最佳分片）配置始终是最优且智能的方案，只需连接并等待至少 30 秒即可。

您可以根据自己运营商的情况设置参数。

!!! info "信息"
    数据包有多种模式。但是，`tlshello` 仅适用于 **TLS 配置**；80、8080 等端口不受影响。

!!! tip "提示"
    目前，在运行 **Xray Knocker 内核** 的客户端上，分片性能表现明显更高效，特别是 **MahsaNG** 和 **v2rayN PRO** 客户端。该内核是专门针对特殊网络环境开发和定制的。

!!! tip "提示"
    如果您找不到适合自己运营商的最佳分片设置，订阅中提供了一个 **Best fragment** 配置。只需连接它并稍等片刻；它会测试几乎所有有效的分片设置，并自动连接到最好的一个。

!!! note "注意"
    分片值有最大值限制。长度 (Length) 不能超过 500，间隔 (Interval) 不能超过 30ms。

!!! warning "警告"
    Max Split 功能最近才添加到 Xray 内核中，使用起来略显复杂，因此在设置任何值之前，请先阅读 Xray 文档。
