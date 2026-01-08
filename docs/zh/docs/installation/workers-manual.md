# :material-new-box:{ .md .middle } Workers 手动安装

强烈建议使用 [向导安装方式](./wizard.md) 以避免 Cloudflare 1101 错误、用户操作失误，并节省配置面板的时间。

## 安装步骤

### 1. 创建 Cloudflare 账号

如果您还没有 Cloudflare 账号，请[在这里](https://dash.cloudflare.com/sign-up)创建一个。注册只需要一个电子邮箱。由于 Cloudflare 的限制，请使用口碑良好的邮箱提供商（如 Gmail）。

### 2. 创建 Worker

首先，[从这里](https://github.com/bia-pain-bache/BPB-Worker-Panel/releases/latest/download/worker.js)下载 Worker 代码。

在您的 Cloudflare 账号中，导航至 `Developer Platform`（开发者平台）标签页，点击 `Create application`（创建应用程序），在 `Workers` 标签页下找到 `Start with Hello World!` 并点击 `Get started`（开始使用）。

输入一个您喜欢的名称（这将构造成面板的域名），然后点击 `Deploy`（部署）。

!!! danger "危险"
    请选择一个**不包含** `bpb` 字样的名称，否则可能会触发 Cloudflare 的检测并导致 `1101` 错误。

然后点击这里的 `Edit code`（编辑代码）。在左侧边栏中，删除 `worker.js` 文件并上传新文件。如果报错，请同时删除 `package-lock.json` 文件。由于代码较长，在手机上复制粘贴比较困难 —— 请参考下图并正确上传。在手机上，打开侧边菜单，长按 Explorer，然后点击 `Upload...`（上传）。

![手机端上传](../images/worker-mobile-upload.jpg)

最后，点击 `Deploy`（部署）该 Worker。

!!! tip "提示"
    注意，面板的更新过程完全相同 —— 删除旧文件，上传新文件，然后部署。之前的设置将保持不变，只有面板内容会更新。

首先，在控制面板顶部点击 `Visit`（访问）。您会看到一个错误，提示需要先设置 UUID 和 Trojan 密码。页面包含一个链接 (Secrets generator) —— 在浏览器中打开并保持打开状态以备下一步使用。

![生成密钥](../images/generate-secrets.jpg)

### 3. 创建 KV

返回 Worker 控制面板并按照以下步骤操作：

![Workers 控制面板](../images/nav-worker-dash.jpg)

从这里进入 `KV` 页面：

![KV 控制面板](../images/nav-dash-kv.jpg)

在 KV 部分，点击 `Create`（创建），设置一个名称（例如 Test），然后点击 `Add`（添加）。

再次前往 `Developer Platform`（开发者平台）部分，打开您刚才创建的 Worker，进入 `Settings`（设置） -> `Bindings`（绑定）。点击 `Add binding`（添加绑定）并选择 `KV Namespace`（KV 命名空间）。从下拉菜单中选择您刚才创建的 KV（例如 Test）。最关键的是第一个字段 —— **必须**设置为 `kv`（小写）。然后点击 `Deploy`（部署）。

![绑定 KV](../images/bind-kv.jpg)

### 4. 设置 UUID、Trojan 密码和订阅路径

在刚才打开的 `Secrets generator`（密钥生成器）页面中点击 `Copy all`（全部复制）。在 Cloudflare 控制面板中前往 `Settings`（设置）部分，找到 `Variables and Secrets`（变量与密钥）部分。点击 `Add`（添加）并将内容粘贴到 `Variable name`（变量名）字段中，然后点击 `Deploy`（部署）。这将自动向面板添加这 3 个参数。

再次在您的 Worker 控制面板点击 `Visit`（访问），您会在浏览器看到测速页面，只需在地址末尾添加 `/panel` 即可看到您的面板：

它会要求您设置新密码并登录 —— 就这么简单。
安装已完成，下方的其余信息并非所有人都有需要。
有关设置教程和提示，请参阅[主指南](../configuration/index.md)。

## 高级配置 (可选)

### 固定代理 IP (Proxy IP)

默认情况下，代码会随机使用多个代理 IP，每次连接 Cloudflare 地址（覆盖了大部分网页）时都会分配一个新的随机 IP。这种 IP 切换可能会导致问题，尤其是对交易用户。从 2.3.5 版本开始，您可以通过面板更改代理 IP 并更新订阅。不过，推荐使用以下方法：

!!! note "注意"
    通过面板更改代理 IP 后，如果 IP 失效，需要更新订阅。这可能会干扰通过捐赠获得的配置，因为没有活动订阅的用户无法更新。本方法仅限个人使用。其他方法不需要更新订阅。

要更改代理 IP，前往 `Workers & Pages`，打开您的 Worker，然后进入 `Settings`（设置） → `Variables and Secrets`（变量与密钥）：

![Workers 环境变量](../images/workers-variables.jpg)

点击 `Add`，在 `Variable name`（变量名）中输入 `PROXY_IP`（大写）。

您可以从以下链接获取 IP —— 它显示了多个 IP 及其地区和运营商。选择一个或多个：

```text
https://www.nslookup.io/domains/bpb.yousef.isegaro.com/dns-records/
```

![代理 IP](../images/proxy-ips.jpg)

!!! info "信息"
    要使用多个代理 IP，请输入逗号分隔的内容。
    ```title="示例"
    151.213.181.145, 5.163.51.41, bpb.yousef.isegaro.com
    ```

在 `Value`（值）字段输入 IP 并点击 `Deploy`（部署）。

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

在 `Value` 字段输入 IP 并点击 `Deploy`。

### 设置回落域名 (Fallback Domain)

默认情况下，访问 Worker 主域名会重定向到 Cloudflare 测速网站。要更改此设置，参照设置 Proxy IP 的步骤，但将变量名设为 `FALLBACK`，并将一个域名（不带 `https://` 或 `http://`）作为值，例如 `www.speedtest.net` 或 `npmjs.org`。

### 更改订阅路径 (Subscription Path)

默认订阅链接路径使用与 VLESS 相同的 UUID。为了增加隐私，您可以更改它。按照上述步骤，但将变量名设为 `SUB_PATH`。在 `/secrets` 路径下的密钥生成器提供了一个 `Random Subscription URI path`（随机订阅 URI 路径）值，您可以使用它或替换为自定义值（仅限允许的字符）。

### 添加自定义域名

前往您的 Cloudflare 控制面板，从 `Compute (Workers)` > `Workers & Pages` 打开您的 Worker。进入 `Settings`（设置），在顶部您会看到 `Domains & Routes`（域名与路由）。点击 `Add +`（添加），然后选择 `Custom domain`（自定义域名）。

输入一个域名（您必须拥有该域名并在同一账号下激活）。

假设您的域名是 `bpb.com`。您可以输入主域名或子域名，如 `xyz.bpb.com`，然后点击 `Add domain`（添加域名）。

Cloudflare 会将 Worker 连接到您的域名（这可能需要一些时间 —— 他们说最长可能需要 24 小时）。

然后再次点击 `Add +`，但这次选择 `Route`（路由）。从 `Zone`（区域）部分选择您的域名，并在 `Route`（路由）部分如下输入：

```title="路由"
*bpb.com/*
```

然后您就可以通过 `https://xyz.bpb.com/panel` 访问面板并获取新订阅。

!!! tip "提示"
    - 如果您将域名连接到 Worker，您的流量可能会变为无限。
    - Worker 面板支持 80、8080 等非 TLS 端口。但一旦添加自定义域名，这些端口将失效且在面板中不可用。

## 更新面板

要更新面板，[从这里](https://github.com/bia-pain-bache/BPB-Worker-Panel/releases/latest/download/worker.js)下载新的 `worker.js` 文件。在您的 Cloudflare 账号中，前往 `Compute (Workers)` > `Workers & Pages`，选择您的 Worker 项目，点击编辑，删除旧的 Worker，上传新的并点击 `Deploy`（部署）。
