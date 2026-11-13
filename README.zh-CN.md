<div align="center">

<img src="docs/images/mimo-logo.png" alt="Mimo Logo" width="160" height="160" />

<h1>Mimo</h1>

<p><a href="README.md">English</a> · <strong>简体中文</strong></p>

<p>基于 <a href="https://github.com/MetaCubeX/mihomo">mihomo</a> 的原生 macOS 代理客户端</p>

<p>
  <a href="https://github.com/MimoProxy/Mimo/releases/latest"><strong>下载最新版</strong></a> ·
  <a href="https://github.com/MimoProxy/Mimo/releases">更新记录</a> ·
  <a href="https://github.com/MimoProxy/Mimo/issues">问题反馈</a>
</p>

<p>
  Mimo 的名字源自俄语「Мимо」，有「从旁经过」之意。<br />
  愿每一次连接，都能轻巧地绕过阻碍，自在抵达你想去的地方。
</p>

</div>

在熟悉的 Mac 界面里，管理配置、切换节点、设置分流、连接内网，并抓取和改写 HTTP／HTTPS 流量。

Mimo 需要你自行提供代理节点或订阅，不提供代理服务。

## 功能

- **配置管理**：导入 Clash / mihomo YAML 配置，或新建自定义配置；通过分类表单或 YAML 编辑，服务商配置更新后保留本地覆写。
- **节点与策略组**：节点切换、延迟测试、搜索与筛选，支持手动选择、自动测速、故障转移和负载均衡。
- **规则分流**：管理规则顺序与开关，查看规则集，编辑 DNS 与嗅探设置。
- **系统代理与增强模式**：按需选择系统代理或 TUN，支持 IPv4 与双栈配置。
- **内网互联与穿透**：通过 Zeno 共享 Mac 所在的 IPv4 内网，或使用 Tailscale／Headscale 访问已有 Tailnet；两项服务可独立配置。
- **MITM 抓包与重写**：查看 HTTP／HTTPS 与 WebSocket 流量、预览抓包媒体，支持 HTTP 重写、脚本及 Loon／Surge HTTP 模块。
- **网络状态**：查看实时速率、连接、今日与本月流量、出口 IP，以及互联网、网关、DNS 和代理诊断。
- **远程控制器**：查看本机或远程 mihomo 的连接、代理链与 DNS 记录，按需断开连接。
- **日常使用**：菜单栏快捷操作、登录启动、全局快捷键、应用更新、备份与恢复，以及自定义 JavaScript 面板。
- **原生界面**：支持浅色与深色外观，跟随系统强调色。

## 界面预览

### 仪表盘 · 浅色

![Mimo 浅色仪表盘](docs/images/mimo-dashboard-light-hd.png)

### 仪表盘 · 深色

![Mimo 深色仪表盘](docs/images/mimo-dashboard-dark-hd.png)

### 远程控制器

![Mimo 远程控制器](docs/images/mimo-controller-hd.png)

### 代理与策略组

![Mimo 代理与策略组](docs/images/mimo-proxies-hd.png)

## 下载与安装

需要 **macOS 14 或更新版本**。目前发布的安装包适用于 **Apple silicon Mac（M1 及更新芯片）**。

1. 前往 [Releases](https://github.com/MimoProxy/Mimo/releases/latest)，下载附件中的 `Mimo-…zip` 安装包。
2. 解压后，将 `Mimo.app` 拖入“应用程序”文件夹并打开。
3. 应用已内置 mihomo，无需另外安装内核或开发工具。

首次打开如果 macOS 提示无法验证开发者，请确认文件来自上面的发布页，再按 [Apple 的说明](https://support.apple.com/zh-cn/102445)，在“系统设置 → 隐私与安全性”中选择“仍要打开”。

## 配置怎么选

| 方式 | 适合谁 |
| --- | --- |
| 服务商配置 | 希望直接使用订阅提供的节点、DNS、策略组与规则；本地修改会在订阅更新后保留 |
| 自定义配置 + 远程代理集 | 希望自行维护 DNS、策略组与规则，只从订阅获取节点；可添加多个代理集 |

“远程代理集”入口位于“代理”和“配置列表”的工具栏。它只向自定义配置提供节点，不会带入服务商的 DNS 或规则。

单独的节点可在配置编辑器的“代理”分类中添加，支持粘贴节点分享链接、Base64 文本或手动填写。订阅 URL 导入与节点链接导入是不同入口。

## 内网互联与穿透

在侧边栏打开「内网互联」，分别配置两项服务：

- **Zeno**：Mac 作为共享端，提供本机可访问的 IPv4 内网。配合 Android 端 Mimo，通过内网 IP 访问 NAS、路由器等设备。
- **Tailscale／Headscale**：访问已有 Tailnet 中的设备和已配置的网段，可设置设备名、认证密钥、HTTPS 控制服务器地址和访问网段。

使用 Zeno：

1. 在 Mac 上启用 Zeno 并保存，再开启系统代理或增强模式；保持 Mac 联网、不休眠。
2. 复制「Peer ID」和「本机网段」，填入 Android 端 Mimo 的「工具 → 内网互联」，启用 Zeno 并保存。
3. 在 Android 首页连接，随后通过内网 IP 访问设备。

Zeno 与 Tailscale 可以同时启用，随 Mimo 的代理连接运行；关闭连接或退出 Mimo 时停止。

## MITM 抓包与重写

在「抓包」中查看 HTTP/1.1、HTTP/2 和 WebSocket 流量，包括请求／响应头、正文、状态码和耗时。支持搜索筛选、复制 curl、导出 HAR，以及已保存图片、音频和视频的预览。每个请求或响应正文的保存上限可设为 **1–64 MiB**，默认 **1 MiB**。

在「重写」中配置 URL、请求头／响应头和正文改写、本地响应，以及 JavaScript 请求／响应脚本。支持导入 Loon 插件和 Surge HTTP 模块（`.sgmodule`），预览内容后按需启用；兼容范围为已支持的 HTTP 模块功能。

解密 HTTPS 前，先在「设置 → MITM」生成、安装并信任本机证书，再开始抓包。MITM 在系统代理或增强模式的**规则模式**下运行，不解密 HTTP/3；使用证书固定的应用可能需要加入排除列表。普通代理与分流不需要安装此证书。

## 更新与备份

- **应用更新**：在“关于”中点击“检查更新…”，也可开启“自动检查更新”。自动检查默认关闭，安装更新需要你确认；内核随应用一同更新。
- **订阅更新**：在“配置列表”中更新单份配置或点击“全部更新”；更新间隔在该页的“更新”区域设置。
- **完整备份**：在“设置 → 数据 → 备份与恢复”导出或恢复。恢复前会自动备份现有数据，并停止当前内核。
- **分享自定义配置**：使用“导出配置（保留订阅）”，生成可重新导入 Mimo 的 `.mimo.yaml` 文件。

配置与订阅凭据保存在本机，尚未加密存储。备份和保留订阅的导出文件也可能包含节点密码、订阅地址，请妥善保管。

## 常见问题

### 抓包与重写可以使用吗？

可以。正式版已支持 [MITM 抓包与 HTTP 重写](#mitm-抓包与重写)。解密 HTTPS 需要信任 Mimo 的本机证书；普通代理和分流不需要安装证书。

### 如何退出或卸载？

从应用菜单或菜单栏面板退出 Mimo，会停止内核并恢复系统代理。关闭主窗口后仍可通过菜单栏使用。

若安装过 Mimo 的 MITM 证书，请先在「设置 → MITM」中移除。若安装过增强服务，先在“关于”中点击“移除增强服务”，再退出并将 `Mimo.app` 移到废纸篓。删除应用不会自动清除本地配置；需要保留数据时可先导出备份。

## 反馈

请在 [GitHub Issues](https://github.com/MimoProxy/Mimo/issues) 中提供 Mimo 版本、macOS 版本、使用模式、复现步骤和错误提示。“设置 → 数据”可导出诊断包。

公开反馈前，请隐去订阅链接、节点密码、令牌等敏感信息。

## 致谢

感谢 [MetaCubeX / mihomo](https://github.com/MetaCubeX/mihomo)、[Sparkle](https://github.com/sparkle-project/Sparkle) 和 [Yams](https://github.com/jpsim/Yams) 及其贡献者。第三方组件的许可证随应用附带。

Mimo 的 MITM 后端基于 [gtoxlili/mihomo-capture](https://github.com/gtoxlili/mihomo-capture) 适配，加入了 Mimo 的受管运行方式和原生界面。感谢 gtoxlili 及项目贡献者。应用的 `Contents/Resources/ThirdParty/MimoCapture` 中保留了上游 [MIT 许可证](https://github.com/gtoxlili/mihomo-capture/blob/1bddd4282dfdc43f2c0a320e1500204bfcc7779c/LICENSE)、原作者版权声明、依赖声明及修改后的后端源码。

特别感谢 [Stash](https://stash.ws/)。这款设计出色的软件，为 Mimo 的设计与开发带来了许多启发。
