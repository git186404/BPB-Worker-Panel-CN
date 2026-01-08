# :material-cog-outline:{ .md .middle } Warp Pro 设置

本部分专门适用于 **Warp Pro** 订阅，详见[此处](../usage/warp-pro.md)。

![Warp Pro 设置](../images/warp-pro-settings.jpg)

## 定义

在所有 Warp 噪声 (Noise/非对称发包) 实现中使用了几个常用术语。包括 **Xray**、**Xray Knocker** 和 **Amnezia** 在内的大多数内核至少共享两个参数：

### 模式 (Mode)

每个 Warp 噪声实现都有一个特定的模式，决定了以何种形式向服务器发送噪声以混淆连接。

### 数量 (Count)

客户端向服务器发送的噪声数据包数量。

### 大小 (Size)

每个噪声数据包的大小，以字节 (bytes) 为单位。

### 延迟 (Delay)

发送噪声数据包之间的间隔。

## MahsaNG

### MahsaNG 模式

- **none**: 不应用噪声，等同于标准 Warp 配置。
- **quic**: 开发人员推荐在特殊网络环境下使用。
- **random**: 随机生成噪声。
- **Custom** (自定义) 模式：允许使用自定义 HEX 字符串（例如 `fe09ad5600bc...`）。

## Clash 和 Amnezia

本部分适用于 **Amnezia**、**WG Tunnel** 和 **Clash-Mihomo** 内核客户端，它们共享相同的设置。您可以指定噪声数据包的数量及其最小和最大大小。在 **Warp Pro** 订阅表格中，除了订阅链接外，您还可以下载 **Amnezia** 和 **WG Tunnel** 配置的压缩包。

这些设置是针对每个运营商通过反复试验得出的。

## v2rayNG 和 v2rayN

### v2ray 模式

**v2rayNG** 和 **v2rayN** 客户端有四种模式：**base64**、**string** (字符串)、**hex** (十六进制) 和 **random** (随机)。在 Noise Count（噪声数量）部分，您可以指定配置中包含多少个噪声数据包。可以添加不同类型的多个噪声；它们不需要统一。

### 噪声数据包 (Noise Packet)

数据包的值必须对应所选的模式：

- **Base64**: 需要有效的 Base64 值。
- **String**: 可以是任何字符串。
- **Random**: 指定字符串长度。
- **Hex**: 需要十六进制字符串。

示例：

```title="Base64"
NTUyMjU0NjItN2I4MC00YWFmLWE3NDgtNjZiYWZiNjlmNmQ2
```

```title="String" (字符串)
salamchetori123
```

```title="Random" (随机)
10-30
```

```title="Hex" (十六进制)
01d800f9373b2c418713aafde43021004ac3b89f
```

!!! tip "提示"
    - 使用[此工具](https://onlinebase64tools.com/base64-encode)将文本转换为 Base64。
    - 使用[此工具](https://onlinetools.com/random/generate-random-hexadecimal-numbers)生成十六进制字符串。

### 应用于 (Applies To)

指定噪声应用于哪种类型的 IP。默认是 IP，即同时应用于 IPv4 和 IPv6。
