# Mimo

基于 [mihomo](https://github.com/MetaCubeX/mihomo) 的原生 macOS 代理客户端。在熟悉的 Mac 界面里，管理配置、切换节点、设置分流，并查看网络状态。

[下载最新版](https://github.com/MimoProxy/Mimo/releases/latest) · [更新记录](https://github.com/MimoProxy/Mimo/releases) · [问题反馈](https://github.com/MimoProxy/Mimo/issues)

Mimo 需要你自行提供代理节点或订阅，不提供代理服务。

## 功能

- **配置管理**：导入 Clash / mihomo YAML 配置，或新建自定义配置；通过分类表单或 YAML 编辑，服务商配置更新后保留本地覆写。
- **节点与策略组**：节点切换、延迟测试、搜索与筛选，支持手动选择、自动测速、故障转移和负载均衡。
- **规则分流**：管理规则顺序与开关，查看规则集，编辑 DNS 与嗅探设置。
- **系统代理与增强模式**：按需选择系统代理或 TUN，支持 IPv4 与双栈配置。
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

## 更新与备份

- **应用更新**：在“关于”中点击“检查更新…”，也可开启“自动检查更新”。自动检查默认关闭，安装更新需要你确认；内核随应用一同更新。
- **订阅更新**：在“配置列表”中更新单份配置或点击“全部更新”；更新间隔在该页的“更新”区域设置。
- **完整备份**：在“设置 → 数据 → 备份与恢复”导出或恢复。恢复前会自动备份现有数据，并停止当前内核。
- **分享自定义配置**：使用“导出配置（保留订阅）”，生成可重新导入 Mimo 的 `.mimo.yaml` 文件。

配置与订阅凭据保存在本机，尚未加密存储。备份和保留订阅的导出文件也可能包含节点密码、订阅地址，请妥善保管。

## 常见问题

### 抓包与重写可以使用吗？

这两项功能仍在开发中，当前正式发行版暂不可启用。普通代理和分流功能不需要安装 HTTPS 证书。

### 如何退出或卸载？

从应用菜单或菜单栏面板退出 Mimo，会停止内核并恢复系统代理。关闭主窗口后仍可通过菜单栏使用。

若安装过增强服务，先在“关于”中点击“移除增强服务”，再退出并将 `Mimo.app` 移到废纸篓。删除应用不会自动清除本地配置；需要保留数据时可先导出备份。

## 反馈

请在 [GitHub Issues](https://github.com/MimoProxy/Mimo/issues) 中提供 Mimo 版本、macOS 版本、使用模式、复现步骤和错误提示。“设置 → 数据”可导出诊断包。

公开反馈前，请隐去订阅链接、节点密码、令牌等敏感信息。

## 致谢

感谢 [MetaCubeX / mihomo](https://github.com/MetaCubeX/mihomo)、[Sparkle](https://github.com/sparkle-project/Sparkle) 和 [Yams](https://github.com/jpsim/Yams) 及其贡献者。第三方组件的许可证随应用附带。

特别感谢 [Stash](https://stash.ws/)。这款设计出色的软件，为 Mimo 的设计与开发带来了许多启发。
