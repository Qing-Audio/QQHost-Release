# QQ Host 1.0.14 · Stable

**中文 | English · 2026-10-01**

QQ Host｜性能桥接机架，一个可以将 DAW 内的单核处理分散成多核处理的效果器。

QQ Host | A performance bridge rack that moves CPU-heavy processing away from the DAW's single real-time thread so the work can use more CPU cores.

## 本版变化 / What's new

版本区间：**1.0.13 → 1.0.14**。上一版保留：[1.0.13](https://github.com/Qing-Audio/QQHost-Release/releases/tag/v1.0.13)。

Version interval: **1.0.13 → 1.0.14**. The [previous release](https://github.com/Qing-Audio/QQHost-Release/releases/tag/v1.0.13) remains available for rollback.

- 新建 Bridge 默认 **2 buffers + Optimize into 2 stages**。旧工程及预置保留原有缓冲深度；没有两段设置的旧状态按串行恢复。
- 右上角 **…** 中，**OFFLOAD Buffer (manual)** 设置缓冲深度，**OFFLOAD Processing (test)** 在两段处理与 **Use serial processing** 之间选择。
- 两段模式在播放时采样耗时，停止播放后尝试安排安全的分界点，减少某些高占用机架的串行处理压力。播放及离线渲染期间不切换配置。
- 更新中英文用户手册，补充新默认值、两段处理入口与使用步骤。

- New Bridges default to **2 buffers + Optimize into 2 stages**. Existing projects and presets keep their saved buffer depth; older states without a two-stage setting restore as serial processing.
- Under **…**, **OFFLOAD Buffer (manual)** sets buffering depth, while **OFFLOAD Processing (test)** offers two-stage processing or **Use serial processing**.
- Two-stage mode measures processing time during playback and attempts to choose a safe boundary after playback stops, reducing serial processing pressure in suitable CPU-heavy racks. Configuration changes are blocked during playback and offline rendering.
- Updated Chinese and English manuals explain the defaults, menu location and two-stage workflow.

## 使用边界 / Before you enable two stages

选中 **Optimize into 2 stages** 不等于已经启用并行。短链、不可拆分链与兼容性限制可能使机架仍按串行处理；LIVE 不采用这套 OFFLOAD 两段调度。缓冲增加会增加延迟，不能弥补持续算力不足。实际效果取决于插件、DAW Buffer Size、路由与电脑配置，不承诺所有机架零 MISS。

Selecting **Optimize into 2 stages** does not guarantee that parallel processing is active. Short or unsplittable chains and compatibility constraints may remain serial; LIVE does not use this OFFLOAD two-stage scheduler. More buffers add latency and cannot compensate for sustained insufficient processing capacity. Results depend on plug-ins, DAW buffer size, routing and hardware; zero MISS for every rack is not promised.

QQ ChainScope 跨两段对齐需要相关模块均支持 Host 音频块标识扩展；不兼容的旧模块会保守地保留在同一段。**本包不包含 ChainScope 更新**，不能仅凭 ChainScope 版本号判断该扩展可用。

QQ ChainScope alignment across stages requires all relevant modules to support the Host audio-block identity extension. Incompatible older modules are conservatively kept in one stage. **This package does not include a ChainScope update**; a ChainScope version number alone does not establish extension support.

## 下载与安装 / Downloads and installation

附件包含四个平台包、两份安装说明与两份用户手册。只需下载与你的平台和格式对应的 ZIP。安装前完全退出 DAW 和插件扫描器；Bridge 与后台 Host 必须成对更新至 **1.0.14 / Protocol 128**，不要混用旧版。

The eight attachments contain four platform packages, two installation guides and two manuals. Download only the ZIP matching your platform and format. Fully quit the DAW and plug-in scanners before installation. Update Bridge and background Host together to **1.0.14 / Protocol 128**; do not mix versions.

| 平台 / Platform | 下载 / Download |
|---|---|
| Windows 10/11 x64 · VST3 | [Windows x64 VST3](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.0.14/QQ.Host.1.0.14.Windows.x64.VST3.zip) |
| macOS 12+ · Apple Silicon VST3 | [Apple Silicon VST3](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.0.14/QQ.Host.1.0.14.macOS.Apple.Silicon.VST3.zip) |
| macOS 12+ · Intel x86_64 VST3 | [Intel x86_64 VST3](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.0.14/QQ.Host.1.0.14.macOS.Intel.x86_64.VST3.zip) |
| macOS 12+ · Universal 2 AU | [Universal 2 AU](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.0.14/QQ.Host.1.0.14.macOS.Universal.2.AU.zip) |
| 中文安装说明 / Chinese guide | [TXT](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.0.14/QQ.Host.1.0.14.Installation.Guide.Chinese.txt) |
| English installation guide | [TXT](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.0.14/QQ.Host.1.0.14.Installation.Guide.English.txt) |
| 中文用户手册 / Chinese manual | [PDF](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.0.14/QQ.Host.1.0.14.User.Manual.Chinese.pdf) |
| English user manual | [PDF](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.0.14/QQ.Host.1.0.14.User.Manual.English.Edition.pdf) |

macOS 包未经 Apple Developer ID 公证，安装和可信来源说明见指南。 / macOS packages are not Apple Developer ID notarized; see the guides for installation and trusted-source guidance.

**FL Studio 必须设置每个 Bridge 的 Wrapper：** Troubleshooting → **Use fixed size buffers**；More → **Process maximum size buffers** 与 **Use maximum buffer size from host**。

**Required for each Bridge in FL Studio:** Wrapper → Troubleshooting → **Use fixed size buffers**, plus **Process maximum size buffers** and **Use maximum buffer size from host** under More.

Cubase 如果没有立即列出已保存预置，可尝试**同一文件名覆盖保存两次**；必要时打开 MediaBay，对相应预置文件夹执行 **Quick Rescan Disk**，不是 Refresh Views。

If Cubase does not immediately list a saved preset, try **saving twice with the same filename and overwriting it**. If needed, open MediaBay and run **Quick Rescan Disk** on the preset folder, not Refresh Views.

QQ Host 为闭源软件。GitHub 自动生成的 Source code ZIP/TAR 是此下载页仓库的快照，并非插件安装包。

QQ Host is closed-source software. GitHub's automatic Source code ZIP/TAR files are snapshots of this download-page repository, not plug-in installers.
