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

Manage configurations, switch nodes, set up routing rules, connect private networks, and inspect HTTP/HTTPS traffic in a familiar Mac interface.

Mimo requires your own proxy nodes or subscription. It does not provide a proxy service.

## Features

- **Configuration management**: Import Clash / mihomo YAML configurations or create your own. Edit through categorized forms or YAML, and keep local overrides when provider configurations update.
- **Nodes and proxy groups**: Switch nodes, test latency, search and filter. Supports manual selection, automatic latency testing, failover, and load balancing.
- **Rule-based routing**: Reorder and toggle rules, inspect rule sets, and configure DNS and traffic sniffing.
- **System Proxy and Enhanced Mode (TUN)**: Use the system proxy or TUN with IPv4-only or IPv4/IPv6 dual-stack networking.
- **Private networks and NAT traversal**: Share a Mac's local IPv4 network through Zeno, or access an existing Tailnet through Tailscale / Headscale. Configure both independently.
- **MITM capture and rewrites**: Inspect HTTP/HTTPS and WebSocket traffic, preview captured media, and apply HTTP rewrites or scripts with Loon and Surge HTTP modules.
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

## Private Networks and NAT Traversal

Open **Private Network** in the sidebar to configure two independent services:

- **Zeno**: Use the Mac as a sharing endpoint for its local IPv4 networks. Pair it with Mimo on Android to access NAS devices, routers and other local services by their private IP addresses.
- **Tailscale / Headscale**: Access devices and configured subnets in an existing Tailnet. Set the hostname, authentication key, HTTPS control-server address and destination subnets.

To use Zeno:

1. Enable Zeno on the Mac, save, and turn on System Proxy or Enhanced Mode. Keep the Mac online and awake.
2. Copy the **Peer ID** and **Local Subnets** into **Tools → Private Network** in Mimo for Android, enable Zeno, and save.
3. Connect from the Android home screen, then access the devices by their local IP addresses.

Zeno and Tailscale can be enabled together. They run while Mimo's proxy connection is active; stopping the connection or quitting Mimo stops the services.

## Capture (MITM) and Rewrites

Use **Capture** to inspect HTTP/1.1, HTTP/2 and WebSocket traffic, including request and response headers, bodies, status codes and timing. Search and filter records, copy requests as curl, export HAR files, and preview saved images, audio and video. Each request or response body has a configurable **1–64 MiB** saving limit; the default is **1 MiB**.

Use **Rewrites** for URL, header and body rewrites, local responses and JavaScript request/response scripts. Import Loon plugins or Surge HTTP modules (`.sgmodule`), preview their contents, and enable the modules you need. This covers supported HTTP module features rather than full Loon or Surge configurations.

For HTTPS decryption, first generate, install and trust this Mac's certificate in **Settings → MITM**, then start capture. MITM runs in **Rule mode** with System Proxy or Enhanced Mode. HTTP/3 is not decrypted, and apps with certificate pinning may need to be excluded. Ordinary proxying and routing do not require installing the certificate.

## Updates and Backups

- **App updates**: Choose **Check for Updates** in About, or enable automatic update checks. Automatic checks are off by default, and installation requires your confirmation. The core is updated with the app.
- **Subscription updates**: Update a single configuration or choose **Update All** on the Configurations page. Set the interval in that page's Update section.
- **Full backups**: Export or restore under **Settings → Data → Backup & Restore**. A backup of your current data is created before restoration, and the running core is stopped.
- **Sharing custom configurations**: Use **Export Configuration (Keep Subscriptions)** to create a `.mimo.yaml` file that can be imported back into Mimo.

Configurations and subscription credentials are stored locally without encryption. Backups and exports that retain subscriptions may also contain node passwords and subscription URLs. Keep these files secure.

## FAQ

### Are traffic capture and rewrites available?

Yes. Release builds include [MITM capture and HTTP rewrites](#capture-mitm-and-rewrites). HTTPS inspection requires trusting Mimo's certificate; ordinary proxying and rule-based routing do not.

### How do I quit or uninstall Mimo?

Quit Mimo from the app menu or menu bar panel to stop the core and restore system proxy settings. Closing the main window keeps Mimo available in the menu bar.

If you installed Mimo's MITM certificate, remove it in **Settings → MITM** before uninstalling. If you installed the Enhanced Service, remove it from About first. Then quit Mimo and move `Mimo.app` to the Trash. Deleting the app does not automatically remove local configurations; export a backup first if you want to keep your data.

## Feedback

When opening a [GitHub issue](https://github.com/MimoProxy/Mimo/issues), include your Mimo and macOS versions, proxy mode, steps to reproduce, and any error messages. You can export a diagnostic report from **Settings → Data**.

Before posting publicly, redact subscription URLs, node passwords, tokens, and other sensitive information.

## Acknowledgments

Thanks to [MetaCubeX / mihomo](https://github.com/MetaCubeX/mihomo), [Sparkle](https://github.com/sparkle-project/Sparkle), [Yams](https://github.com/jpsim/Yams), and their contributors. Third-party licenses are included with the app.

Mimo's MITM backend is based on [gtoxlili/mihomo-capture](https://github.com/gtoxlili/mihomo-capture), with adaptations for Mimo's managed runtime and native interface. Thanks to gtoxlili and the project's contributors. The upstream [MIT license](https://github.com/gtoxlili/mihomo-capture/blob/1bddd4282dfdc43f2c0a320e1500204bfcc7779c/LICENSE), original copyright notice, dependency notices and modified backend source are included in the app under `Contents/Resources/ThirdParty/MimoCapture`.

Special thanks to [Stash](https://stash.ws/). Its outstanding design has been a source of inspiration for Mimo's design and development.
