# :material-cog-outline:{ .md .middle } 路由规则

![路由规则](../images/routing-rules.jpg)

## 预定义规则

使用预定义的路由规则，您可以将以下设置应用于配置：

* 直接连接到伊朗地址，不经过代理。
* 直接访问中国网站。
* 直接访问俄罗斯网站。
* 拦截伊朗和国外的广告，拦截率最高达 90%。
* 拦截色情内容网站。
* 拦截 QUIC 连接（由于网络不稳定）。
* 拦截恶意软件 (Malware)（请阅读警告）。
* 拦截钓鱼网站 (Phishing)（请阅读警告）。
* 拦截加密货币矿工 (Cryptominers)（请阅读警告）。

配置中默认设置了直接访问本地地址（如 127.0.0.1），无需手动添加。

!!! warning "警告"
    v2ray 用户如果想使用 `Malware`（恶意软件）、`Phishing`（钓鱼网站）和 `Cryptominers`（矿工）规则，应将 Geo 资源更改为 **Chocolate4U** 并下载资源，否则配置将无法连接。

!!! warning "警告"
    如果您启用了路由规则但客户端无法连接，主要原因是 Geo 资源未更新。进入 v2rayNG 菜单中的 Geo 资产设置，点击云端或下载图标进行更新。如果更新过程不成功，您将无法连接。如果您尝试了所有方法仍无法更新，请从下方链接下载这两个文件，不要点击更新按钮，而是点击添加按钮手动导入这两个文件：

```title="GeoIP"
https://github.com/Loyalsoldier/v2ray-rules-dat/releases/latest/download/geoip.dat
```

```title="GeoSite"
https://github.com/Loyalsoldier/v2ray-rules-dat/releases/latest/download/geosite.dat
```

## 自定义规则

在某些情况下，预定义规则可能无法满足需求。例如，如果您屏蔽了色情内容，但某个特定网站不在列表中且未被屏蔽，您就需要使用自定义规则。

您可以在此部分使用三种不同的格式：**域名 (Domain)**、**IP** 和 **IP/CIDR**。

请注意，如果您输入 `google.com`，其所有子域名也将被拦截或直接路由，例如 `drive.google.com` 或 `mail.google.com`。示例：

```title="域名"
google.com
```

```title="IPv4"
192.168.1.1
```

```title="IPv6"
2606:4700::6810:85e5
```

```title="IPv4 CIDR"
192.168.1.1/32
```

```title="IPv6 CIDR"
2606:4700::6810:85e5/128
```

## 制裁规则 (Sanction Rules)

如果您需要某些网站仅绕复制裁并直接连接（不经过代理），可以使用此部分。
您可以在[常规设置](./common.md)中设置所需的 DNS 服务器（该服务器也应是一个透明代理），选择预置规则或填写自定义地址。您甚至可以使用像 `WorkerLess` 这样的配置，它不使用任何代理即可访问受制裁的网站。

!!! info "信息"
    请注意，如果您在自定义规则中输入 `google.com`，其所有子域名也将直接路由，例如 `drive.google.com` 或 `mail.google.com`。

!!! note "注意"
    激活这些规则时，应确保 DNS 支持该域名。例如，如果您激活了 `Microsoft` 规则但 DNS 不支持，您将无法连接到 Microsoft 域名。请检查 DNS 目录并确保您的目标规则或域名受支持。
