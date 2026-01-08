# :material-new-box:{ .md .middle } Workers 和 Pages 安装 - 向导方式

为了简化安装过程并在创建过程中防止用户出错，我们推出了 [BPB Wizard](https://github.com/bia-pain-bache/BPB-Wizard) 项目。它同时支持 Workers 和 Pages 方法，高度推荐使用。

![向导应用](../images/wizard.jpg)

## 1. Cloudflare 账号

要使用此方法，您只需要一个 Cloudflare 账号。您可以[在这里注册](https://dash.cloudflare.com/sign-up/)，注册后别忘了检查邮件以验证您的账号。

## 2. 安装 BPB 面板

!!! warning "警告"
    如果您连接了 VPN，请先断开连接。

### Windows - Linux - macOS

根据您的操作系统，[下载 ZIP 文件](https://github.com/bia-pain-bache/BPB-Wizard/releases/latest)，解压并运行该程序。

### Android

手机上安装了 Termux 的 Android 用户可以通过将以下代码复制到 Termux 中来安装 BPB 面板：

```bash title="Termux - Linux"
bash <(curl -fsSL https://raw.githubusercontent.com/bia-pain-bache/BPB-Wizard/main/install.sh)
```

!!! warning "警告"
    请务必仅从[官方来源](https://github.com/termux/termux-app/releases/latest)下载并安装 Termux。通过 Google Play 安装可能会导致问题。

第一个问题会询问您是想创建一个新面板，还是修改账号中现有的面板。

然后它会登录您的 Cloudflare 账号，请求您的许可，返回终端并向您询问一系列问题。

如果您选择选项 1，它将询问一系列配置问题。您可以使用默认值或输入自己的值。最后，它会在浏览器中为您打开面板 —— 就这么简单。

!!! note "提示"
    对于它询问的每个设置，它都已经为您生成了一个安全的个人值。您可以直接按 Enter 键接受它并继续下一个问题，或者输入您自己的值。

如果您选择选项 2，它会列出已部署的 Workers 和 Pages 项目，您可以选择要修改的项目。

## 更新面板

只需运行向导并在第一个问题中选择选项 2。它会显示您账号中的项目名称列表 —— 您可以选择任何一个进行更新或删除。
