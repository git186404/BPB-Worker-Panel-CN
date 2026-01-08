# :material-cog-outline:{ .md .middle } 常规设置

![常规设置](../images/common-settings.jpg)

本部分提供了所有订阅和协议之间共享的设置。

## 本地 DNS (Local DNS)

本地 DNS 主要用于路由绕过规则。默认情况下，本地 DNS 服务器设置为 Google DNS。

许多 DNS 服务器可以作为 IP 形式的本地 DNS 使用，您也可以使用 **localhost**，它将使用您的运营商 (ISP) DNS 服务器，这对于路由目的来说已经足够。

## 虚假 DNS (Fake DNS)

您可以启用虚假 DNS 以减少 DNS 查询延迟，但请谨慎使用，它可能与某些应用程序不兼容或干扰系统 DNS。如果您不确定其功能，请避免启用。

## 反制封锁 DNS (Anti Sanction DNS)

此 DNS 服务器用于[此处说明](./routing-rules.md)的**反制封锁/制裁规则**。默认 DNS 服务器是 [Shecan](https://shecan.ir/)（针对伊朗用户）。在设置路由规则之前，您应该检查它是否支持您所需的域名。

!!! info "信息"
    DNS 服务器可以是 IP 形式（UDP DNS）、TCP DNS、DOT 或 DoH。

## 启用 IPv6

面板默认提供 IPv6 的 VLESS/Trojan 配置。如果您的运营商不支持 IPv6，请禁用它以减少配置数量，并优化 VLESS、Trojan 和 Warp 配置的 DNS 和路由设置。

## 允许局域网连接 (Allow connections from LAN)

如果您启用此功能，网络中的其他人（例如 WiFi 网络下）可以通过您的设备本地 IP 使用您的代理。他们可以在其设备上设置 socks 代理，将您的本地 IP 设置为地址，并根据您使用的客户端设置以下端口：

- v2ray: 10808
- sing-box: 2080
- Clash: 7890

请注意，在办公室或公共网络中使用此功能可能存在风险。

## 日志级别 (Log Level)

指定客户端日志的级别。通常为 "warning"（警告），这足以调试问题；但在提交 Github Issue 或检查代理活动时，您可能需要将其更改。
