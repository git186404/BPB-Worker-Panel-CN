# :material-new-box:{ .md .middle } Pages 手动安装 (直接上传)

强烈建议使用 [向导安装方式](./wizard.md) 以避免 Cloudflare 1101 错误、用户操作失误，并节省配置面板的时间。

## 安装步骤

### 1. 创建 Cloudflare 账号

如果您还没有 Cloudflare 账号，请[在这里](https://dash.cloudflare.com/sign-up)创建一个。注册只需要一个电子邮箱。由于 Cloudflare 的限制，请使用口碑良好的邮箱提供商（如 Gmail）。

### 2. 创建 Pages 项目

[从这里](https://github.com/bia-pain-bache/BPB-Worker-Panel/releases/latest/download/worker.zip)下载 Worker 压缩包文件。

在您的 Cloudflare 账号中，导航至 `Developer Platform`（开发者平台）部分，点击 `Create application`（创建应用程序），选择 `Pages` 标签页，然后选择 `Use direct upload`（使用直接上传） > `Get started`（开始使用）。

输入 `Project Name`（项目名称），这将构造成面板的域名。

!!! danger "危险"
    请选择一个**不包含** `bpb` 字样的名称，否则可能会触发 Cloudflare 的检测并导致 `1101` 错误。

点击 `Create Project`（创建项目），然后点击 `Select from computer`（从电脑选择）并选择 `Upload zip`（上传 zip），上传下载好的压缩包。

现在点击 `Deploy site`（部署站点），然后点击 `Continue to project`（继续前往项目）。

您的项目已创建，但尚未运行。在 `Deployment`（部署）页面中，点击 `Production`（生产）部分的 `Visit`（访问）。

!!! warning "警告"
    Cloudflare 可能需要最多 5 分钟来设置 Pages 域名。如果 URL 无法立即访问，请不要担心。

您会遇到一个错误，提示必须设置 UUID 和 Trojan 密码。页面会提供一个链接（Secrets generator）；在浏览器中打开它并保存以备下一步使用。

![Pages 应用](../images/generate-secrets.jpg)

### 3. 创建 KV

从左侧菜单进入 `Storage and Databases`（存储与数据库） > `KV`：

![Pages 应用](../images/nav-dash-kv.jpg)

点击 `Create`（创建），分配一个您喜欢的名称，然后点击 `Add`（添加）。

返回 `Workers & Pages` 部分并打开您的 Pages 项目。进入 `Settings`（设置） -> `Functions`（函数），找到 `Binding`（绑定）部分，如下图所示：

![Pages 应用](../images/settings-functions.jpg)

在 `Bindings` 部分，点击 `Add`（添加）并选择 `KV Namespace`（KV 命名空间）。将 `Variable name`（变量名）设置为 `kv`（**必须完全一致**），并选择刚才创建的 KV 命名空间。点击 `Save`（保存）。

![Pages 应用](../images/bind-kv.jpg)

KV 设置现已完成。

### 4. 设置 UUID、Trojan 密码和订阅路径

在刚才提供的 `Secrets generator`（密钥生成器）页面点击 `Copy all`（全部复制）。在 Cloudflare 控制面板中前往 `Settings`（设置）部分，找到 `Variables and Secrets`（变量与密钥）部分。点击 `Add`（添加）并将内容粘贴到 `Variable name`（变量名）字段中，然后点击 `Save`（保存）。这将自动向面板添加这 3 个参数。

点击页面顶部的 `Create deployment`（创建部署），再次上传相同的 zip 文件。

返回 `Deployments`（部署）页面，点击 `Production`（生产）部分的 `Visit`（访问），在 URL 末尾添加 `panel/` 即可访问面板。

更多配置和提示请参阅[主指南](../configuration/index.md)。安装已完成，接下来的高级设置是可选的。

## 高级配置 (可选)

### 固定代理 IP (Proxy IP)

默认情况下，代码会随机使用多个代理 IP，每次连接 Cloudflare 地址（覆盖了大部分网页）时都会分配一个新的随机 IP。这种 IP 切换可能会导致问题，尤其是对交易用户。从 2.3.5 版本开始，您可以通过面板更改代理 IP 并更新订阅。不过，推荐使用以下方法：

!!! note "注意"
    通过面板更改代理 IP 后，如果 IP 失效，需要更新订阅。这可能会干扰通过捐赠获得的配置，因为没有活动订阅的用户无法更新。本方法仅限个人使用。其他方法不需要更新订阅。

在项目的 `Settings`（设置）部分，打开 `Variables and Secrets`（变量与密钥）：

![Pages 应用](../images/pages-env-vars.jpg)

点击 `Add`（添加），在第一个框中输入 `PROXY_IP`（大写）。从以下链接获取 IP，该链接列出了来自不同地区和运营商的 IP：

```text
https://www.nslookup.io/domains/bpb.yousef.isegaro.com/dns-records/
```

![Pages 应用](../images/proxy-ips.jpg)

!!! info "信息"
    要使用多个代理 IP，请用逗号分隔。
    ```title="示例"
    151.213.181.145, 5.163.51.41, bpb.yousef.isegaro.com
    ```

在 `Value`（值）字段输入 IP 并点击 `Save`（保存）。点击页面顶部的 `Create deployment`（创建部署）并再次上传 zip 文件。更改将生效。

### 固定 NAT64 前缀

默认情况下，代码会随机使用多个 NAT64 前缀。这种 IP 切换可能会导致问题，尤其是对交易用户。从 3.4.2 版本开始，您可以通过面板更改前缀并更新订阅。不过，推荐使用以下方法：

!!! note "注意"
    通过面板更改 NAT64 前缀后，如果 IP 失效，需要更新订阅。这可能会干扰捐赠配置。本方法仅限个人使用。

在项目的 `Settings` 部分，打开 `Variables and Secrets`，点击 `Add` 并输入 `NAT64_PREFIX`（大写）。从以下链接获取 IP：

```text
https://github.com/bia-pain-bache/BPB-Worker-Panel/blob/main/NAT64Prefixes.md
```

!!! info "信息"
    要使用多个 IP，请用逗号分隔。
    ```title="示例"
    [2602:fc59:b0:64::], [2602:fc59:11:64::]
    ```

在 `Value` 字段输入 IP 并点击 `Save`。点击页面顶部的 `Create deployment` 并再次上传 zip 文件。更改将生效。

### 设置回落域名 (Fallback Domain)

默认情况下，访问 Pages 主域名会重定向到 Cloudflare 测速网站。要更改此设置，参照设置 Proxy IP 的步骤，但将变量名设为 `FALLBACK`，并将一个域名（不带 `https://` 或 `http://`）作为值，例如 `www.speedtest.net` 或 `npmjs.org`。

### 更改订阅路径 (Subscription Path)

默认订阅链接路径使用与 VLESS 相同的 UUID。为了增加隐私，您可以更改它。按照上述步骤，但将变量名设为 `SUB_PATH`。密钥生成器页面提供了一个 `Random Subscription URI path`（随机订阅 URI 路径）值，您可以使用它或替换为自定义值（仅限允许的字符）。

### 添加自定义域名

在 Cloudflare 控制面板中，导航至 `Compute (Workers)` -> `Workers & Pages` 并选择您的面板。在 `Custom domains`（自定义域名）标签页中，点击 `Set up a custom domain`（设置自定义域名）。输入一个域名（您必须拥有该域名并在同一账号下激活）。例如，如果您拥有 `bpb.com`，您可以使用该域名本身或子域名如 `xyz.bpb.com`。点击 `Continue`（继续）然后点击 `Activate domain`（激活域名）。

在您的域名区域 (Zone) 中，为 `xyz.bpb.com` 添加一条指向您 Pages 域名的 CNAME 解析记录。稍等片刻，Cloudflare 会将 Pages 连接到您的域名。之后您就可以通过 `https://xyz.bpb.com/panel` 访问面板并获取新订阅。

## 更新面板

要更新面板，[从这里](https://github.com/bia-pain-bache/BPB-Worker-Panel/releases/latest/download/worker.zip)下载新的 zip 文件。在您的 Cloudflare 账号中，前往 `Compute (Workers)` -> `Workers & Pages`，选择您的 Pages 项目，点击 `Create deployment`（创建部署），并上传新的 zip 文件。
