# BPB 面板

![面板概览](images/panel-overview.jpg)

## 简介

本项目旨在提供一个用户面板，用于访问 **免费**、**安全** 且 **私密** 的 **VLESS**、**Trojan** 和 **Warp** 配置。它确保即使在域名或 Warp 服务被运营商屏蔽的情况下也能保持连接，提供两种部署选项：

- **Workers** 部署
- **Pages** 部署

🌟 如果您觉得 **BPB 面板** 对您有帮助，您的捐赠将产生巨大影响 🌟

```title="USDT (BEP20)"
0xbdf15d41C56f861f25b2b11C835bd45dfD5b792F
```

## 功能特性

1. **免费且私密**：无需任何费用，且服务器是私有的。
2. **直观的面板**：界面精简，方便导航、配置和使用。
3. **多协议支持**：提供 VLESS、Trojan 和 Wireguard (Warp) 协议。
4. **Warp Pro 配置**：在关键时刻优化的 Warp 配置。
5. **分片 (Fragment) 支持**：在关键网络环境下支持分片功能。
6. **全面的路由规则**：绕过伊朗/中国/俄罗斯及局域网，屏蔽 QUIC、色情、广告、恶意软件、钓鱼网站，并支持绕过封锁。
7. **链式代理 (Chain Proxy)**：能够添加链式代理（VLESS、Trojan、Shadowsocks、socks 和 http）以固定 IP。
8. **广泛的客户端兼容性**：为 Xray、Sing-box 和 Clash-Mihomo 内核客户端提供订阅链接。
9. **密码保护面板**：受密码保护，确保面板的安全和私密。
10. **完全可定制**：支持设置优选 IP/域名、代理 IP、DNS 服务器、选择端口和协议、Warp 端点等。

## 限制说明

1. **UDP 传输**：Workers 上的 VLESS 和 Trojan 协议无法妥善处理 **UDP**，因此默认禁用（影响 Telegram 视频通话等功能），且不支持 UDP DNS。默认启用 DoH 以增强安全性。
2. **请求限制**：每个 Worker 每天支持 10 万次 VLESS 和 Trojan 请求，适合 2-3 名用户使用。Warp 配置则没有限制。

## 快速入门

- [安装方法](installation/wizard.md)
- [配置说明](configuration/index.md)
- [如何使用](usage/index.md)
- [常见问题](faq.md)

## 支持的客户端

|       客户端        |      版本      | 分片支持 | Warp Pro 支持 |
| :----------------: | :------------: | :------: | :-----------: |
|     **v2rayNG**     |  1.10.26 或更高 | :material-check: | :material-check: |
|     **MahsaNG**     |    14 或更高    | :material-check: | :material-check: |
|     **v2rayN**      |  7.15.4 或更高  | :material-check: | :material-check: |
|   **v2rayN-PRO**    |   1.9 或更高   | :material-check: | :material-check: |
|    **Sing-box**     |  1.12.0 或更高  | :material-check: | :material-close: |
|    **Streisand**    |  1.6.64 或更高  | :material-check: | :material-check: |
|   **Clash Meta**    |                | :material-close: | :material-check: |
| **Clash Verge Rev** |                | :material-close: | :material-check: |
|     **FLClash**     |                | :material-close: | :material-check: |
|   **AmneziaVPN**    |                | :material-close: | :material-check: |
|    **WG Tunnel**    |                | :material-close: | :material-check: |

## 环境变量

|   变量   |               用途                |     必填项      |
| :------: | :------------------------------: | :------------: |
|   **UUID**   |             VLESS UUID           | :heavy_check_mark: |
| **TR_PASS**  |          Trojan 密码             | :heavy_check_mark: |
| **PROXY_IP** | 代理 IP 或域名 (VLESS, Trojan)    |        :x:         |
|  **PREFIX**  |   NAT64 前缀 (VLESS, Trojan)     |        :x:         |
| **SUB_PATH** |         订阅 URI                 |        :x:         |
| **FALLBACK** |  回落域名 (VLESS, Trojan)         |        :x:         |
| **DOH_URL**  |              核心 DOH            |        :x:         |

---

## 星标增长趋势

[![星标增长趋势](https://starchart.cc/bia-pain-bache/BPB-Worker-Panel.svg?variant=adaptive)](https://starchart.cc/bia-pain-bache/BPB-Worker-Panel)
