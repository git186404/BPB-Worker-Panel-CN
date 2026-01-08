# :material-cloud-question-outline:{ .lg .middle } 常见问题解答

??? question "为什么 v2ray 配置无法连接？"
    如果您启用了 `Routing rules`（路由规则）且 VPN 无法连接，唯一的原因是 Geo 资源文件未更新。在 v2rayN(G) 客户端菜单中，进入 `Asset files`（资源文件）部分，点击云端或下载图标进行更新。请注意更新需要一些时间，您需要等所有文件显示 `success`（成功）。如果更新失败，将无法连接。如果您尝试了各种方法仍无法更新，请从以下链接下载这两个文件，并点击添加按钮手动导入：
    ```title="GeoIP"
    https://github.com/Loyalsoldier/v2ray-rules-dat/releases/latest/download/geoip.dat
    ```
    ```title="GeoSite"
    https://github.com/Loyalsoldier/v2ray-rules-dat/releases/latest/download/geosite.dat
    ```

??? question "为什么配置可以在 v2rayNG 中连接，但不能在 Streisand 等客户端中连接？"
    BPB 会尽可能快地集成新内核的功能，而某些开发人员可能只是将内核升级到最新版本，而不进行完整的功能适配和优化。因此，您可以向相关客户端的开发人员反馈此类问题。

??? question "为什么分片 (Fragment) 配置在我的运营商网络下速度很慢？"
    每个运营商都有其偏好的分片设置。大多数情况下使用面板默认设置即可，但以下数值在您的网络下可能效果更好。您可能需要将分片配置文件更改为 `Medium`（中）、`High`（高），甚至在 `Custom`（自定义）配置文件中手动更改设置以获得更好的效果。此外，建议使用 MahsaNG 连接分片配置。

??? question "我按照教程提取并使用了代理 IP，为什么某些网站或应用（如 X/Twitter）仍无法使用？"
    目前有很多公共 IP，其中一些可能不稳定。您需要通过测试来寻找好用的 IP。

??? question "设置代理 IP 后原本可以正常工作，但现在不行了！"
    如果您使用的是单一 IP，它可能会在一段时间后失效，导致许多网站无法打开。您需要重新执行提取步骤。如果不需要固定 IP，建议直接使用面板默认设置，不要使用单一代理 IP。

??? question "为什么我访问 `panel/` 地址时报错？"
    请遵循安装指南或使用 **Wizard**（向导）；这通常是因为 KV、UUID 或 Trojan 密码未配置正确。

??? question "我部署后 Cloudflare 返回错误 1101！"
    您的 Cloudflare 账号可能已被标记。请使用官方邮箱（如 Gmail）创建一个新的 Cloudflare 账号。此外，请确保项目名称中不包含 "bpb" 字样。
    建议使用 **Wizard**（向导）进行安装。

??? question "我可以将其用于炒股或交易吗？"
    如果您的 Cloudflare IP 位于德国（通常如此），使用单一的德国代理 IP 应该是可以的。但建议使用链式代理 (Chain Proxy) 方法来稳定 IP。

??? question "为什么我在面板中看不到非 TLS 端口？"
    要使用非 TLS 配置，您必须通过 Workers 方式部署且不使用自定义域名。

??? question "为什么最佳分片配置无法连接或无法正常工作？"
    请在设置中关闭 `Prefer IPv6`（优先使用 IPv6）。

??? question "为什么 Telegram 通话或 Clubhouse 无法使用？"
    Cloudflare 无法妥善处理 UDP 流量。目前尚无有效的解决方案。请改用 Warp 配置。

??? question "为什么无法打开 ChatGPT？"
    因为面板默认的代理 IP 是公共的，其中许多可能被 ChatGPT 视为可疑。请使用以下链接搜索并测试适合您的 IP：
    ```link
    https://www.nslookup.io/domains/bpb.yousef.isegaro.com/dns-records/
    ```
    或者在面板的路由设置部分启用 `Bypass ChatGPT`（绕过 ChatGPT）选项。

??? question "我忘记了面板密码，该怎么办？"
    前往您的 Cloudflare 控制面板，找到为 Worker 或 Pages 创建的 KV，点击查看，进入 KV Pairs 部分。在表格中，您会看到一个 `pwd` 键，旁边的值即为您的密码。

??? question "如果不更改 UUID 和 Trojan 密码会发生什么？"
    从 2.7.7 版本开始，必须设置这两个参数，否则面板将无法运行。

??? question "我使用了 Pages 上传方法，但返回 404 错误。"
    Cloudflare 大约需要 4-5 分钟来注册 Pages 域名。请稍等片刻，刷新后即可正常工作。

??? question "为什么面板没有显示屏蔽广告 (Block Ads) 的复选框？"
    `uBlock`、`AdGuard` 等扩展程序甚至某些带有内置广告拦截设置的浏览器可能会将其隐藏。请针对该面板禁用这些功能。

??? question "为什么向导 (Wizard) 会被 Windows 识别为病毒？"
    向导程序缺少“代码签名证书”，并且需要下载 worker.js 到您的电脑、进行自定义并部署到 Cloudflare，这种行为被杀毒软件视为可疑行为（如木马/下载器）。因此，您需要暂时禁用 Windows Defender 或其他杀毒软件。

??? question "为什么 v2rayN 无法对配置进行 Ping 测试？"
    目前 v2rayN 对自定义配置存在一些问题，而 BPB 面板配置均为自定义。不用担心，直接启用并使用即可。所有订阅中都有“最佳 Ping 配置”，会自动连接到最佳 IP，因此您无需每次都测试所有配置。

??? question "为什么 sing-box 在导入订阅时报错？"
    BPB 仅支持 sing-box 1.12.0 或更高版本。
