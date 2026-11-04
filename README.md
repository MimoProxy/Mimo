<div align="center">

<img src="docs/images/mimo-logo.png" alt="Mimo Logo" width="160" height="160" />

<h1>Mimo</h1>

<p><strong>English</strong> · <a href="README.zh-CN.md">简体中文</a></p>

<p>A native macOS proxy client powered by <a href="https://github.com/MetaCubeX/mihomo">mihomo</a></p>

<p>
  <a href="https://github.com/MimoProxy/Mimo/releases/latest"><strong>Download</strong></a> ·
  <a href="https://github.com/MimoProxy/Mimo/releases">Release Notes</a> ·
  <a href="https://github.com/MimoProxy/Mimo/issues">Report an Issue</a>
</p>

<p>
  Mimo takes its name from the Russian word “Мимо,” meaning “passing by.”<br />
  May every connection glide past obstacles and carry you freely to wherever you wish to go.
</p>

</div>

Manage configurations, switch nodes, set up routing rules, and monitor your network in a familiar Mac interface.

Mimo requires your own proxy nodes or subscription. It does not provide a proxy service.

## Features

- **Configuration management**: Import Clash / mihomo YAML configurations or create your own. Edit through categorized forms or YAML, and keep local overrides when provider configurations update.
- **Nodes and proxy groups**: Switch nodes, test latency, search and filter. Supports manual selection, automatic latency testing, failover, and load balancing.
- **Rule-based routing**: Reorder and toggle rules, inspect rule sets, and configure DNS and traffic sniffing.
- **System Proxy and Enhanced Mode (TUN)**: Use the system proxy or TUN with IPv4-only or IPv4/IPv6 dual-stack networking.
- **Network overview**: View live traffic rates, connections, daily and monthly usage, outbound IP information, and diagnostics for internet connectivity, gateway, DNS, and proxies.
- **Remote controller**: Inspect connections, proxy chains, and DNS records on local or remote mihomo instances, and close connections as needed.
- **Everyday tools**: Menu bar controls, launch at login, global shortcuts, app updates, backup and restore, and custom JavaScript tiles.
- **Native interface**: Light and dark appearances with the system accent color.

## Screenshots

### Dashboard · Light

![Mimo dashboard in light mode](docs/images/mimo-dashboard-light-hd.png)

### Dashboard · Dark

![Mimo dashboard in dark mode](docs/images/mimo-dashboard-dark-hd.png)

### Remote Controller

![Mimo remote controller](docs/images/mimo-controller-hd.png)

### Proxies and Groups

![Mimo proxies and groups](docs/images/mimo-proxies-hd.png)

## Download and Installation

Requires **macOS 14 or later**. Current release packages are available for **Apple silicon Macs (M1 and later)**.

1. Visit [Releases](https://github.com/MimoProxy/Mimo/releases/latest) and download the attached ZIP package.
2. Unzip it, drag `Mimo.app` into Applications, and open it.
3. The mihomo core is bundled. No separate core or development tools are required.

If macOS cannot verify the developer on first launch, confirm that you downloaded the app from the release page above. Then follow [Apple's instructions](https://support.apple.com/en-us/102445) to choose **Open Anyway** in **System Settings → Privacy & Security**.

## Choosing a Configuration

| Approach | Best for |
| --- | --- |
| Provider configuration | Using the nodes, DNS, proxy groups, and rules supplied by a subscription. Local changes are preserved when the subscription updates. |
| Custom configuration + remote proxy sets | Managing your own DNS, proxy groups, and rules while fetching only nodes from subscriptions. Multiple proxy sets can be added. |

Remote proxy sets are available from the toolbars on the Proxies and Configurations pages. They contribute nodes to custom configurations without importing the provider's DNS or rules.

To add individual nodes, use the Proxies category in the configuration editor. You can paste node share links or Base64 text, or enter the settings manually. Subscription URLs and node share links use separate import options.

## Updates and Backups

- **App updates**: Choose **Check for Updates** in About, or enable automatic update checks. Automatic checks are off by default, and installation requires your confirmation. The core is updated with the app.
- **Subscription updates**: Update a single configuration or choose **Update All** on the Configurations page. Set the interval in that page's Update section.
- **Full backups**: Export or restore under **Settings → Data → Backup & Restore**. A backup of your current data is created before restoration, and the running core is stopped.
- **Sharing custom configurations**: Use **Export Configuration (Keep Subscriptions)** to create a `.mimo.yaml` file that can be imported back into Mimo.

Configurations and subscription credentials are stored locally without encryption. Backups and exports that retain subscriptions may also contain node passwords and subscription URLs. Keep these files secure.

## FAQ

### Are traffic capture and rewrites available?

These features are still in development and cannot currently be enabled in release builds. Regular proxying and rule-based routing do not require an HTTPS certificate to be installed.

### How do I quit or uninstall Mimo?

Quit Mimo from the app menu or menu bar panel to stop the core and restore system proxy settings. Closing the main window keeps Mimo available in the menu bar.

If you installed the Enhanced Service, remove it from About first. Then quit Mimo and move `Mimo.app` to the Trash. Deleting the app does not automatically remove local configurations; export a backup first if you want to keep your data.

## Feedback

When opening a [GitHub issue](https://github.com/MimoProxy/Mimo/issues), include your Mimo and macOS versions, proxy mode, steps to reproduce, and any error messages. You can export a diagnostic report from **Settings → Data**.

Before posting publicly, redact subscription URLs, node passwords, tokens, and other sensitive information.

## Acknowledgments

Thanks to [MetaCubeX / mihomo](https://github.com/MetaCubeX/mihomo), [Sparkle](https://github.com/sparkle-project/Sparkle), [Yams](https://github.com/jpsim/Yams), and their contributors. Third-party licenses are included with the app.

Special thanks to [Stash](https://stash.ws/). Its outstanding design has been a source of inspiration for Mimo's design and development.
