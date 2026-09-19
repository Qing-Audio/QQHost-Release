# QQ Host 1.0.10

**Stable · 2026-09-19 · Qing Audio**

QQ Host｜性能桥接机架，一个可以将 DAW 内的单核处理分散成多核处理的效果器。

QQ Host is a performance bridge rack that moves processing away from the DAW's real-time thread, allowing work to use more CPU cores while keeping the familiar Insert workflow. It does not rewrite an individual plug-in's internal algorithm for multithreading.

## 本次更新 / What's new

本次公开更新从 1.0.4 升级到 1.0.10。主要增加 Classic / Light / Dark 外观切换，改善预置与离线导出，并修复 Ozone 9 / 11 独立 Imager 的准备阶段卡住问题。恢复操作改为由用户手动控制，不再因为超时或其他机架变化反复自动刷新。

This public update moves from 1.0.4 to 1.0.10. It adds Classic / Light / Dark themes, improves presets and offline rendering, and fixes a preparation hang affecting standalone Ozone 9/11 Imager. Recovery is now user-controlled rather than repeatedly triggered by timeouts or changes in other racks.

## 逐版本变化 / Changes by version

### 1.0.5 — 预置与机架操作 / Presets and rack operation

改善兼容身份下的 VST2/VST3 预置发现与加载、Control Room 状态恢复保护及复制轨道时的局部恢复。插件可以跨 Divider 拖动。Cubase 未列出预置时，提示使用同一文件名覆盖保存两次，必要时再执行 Quick Rescan Disk。

Improves discovery and loading of compatible VST2/VST3 presets, Control Room restoration safeguards and local recovery during track duplication. Plug-ins can move across dividers. If Cubase does not list a preset, try saving twice under the same filename with overwrite confirmation, then Quick Rescan Disk if needed.

### 1.0.6 — Classic / Light / Dark

保留 Classic，增加 Light 和 Dark；只需点击 Bridge 顶部的 UI 按钮循环切换，下次打开记住上次选择。Host 工具栏跟随，不另设切换按钮。字体、Meter、推子和按钮跟随主题，并改善插件启用与关闭状态的对比。

Keeps Classic and adds Light and Dark. Click the UI button at the top of the Bridge to cycle themes; your last choice is remembered. Hosted toolbars follow without a second switch. Typography, meters, faders and buttons follow the theme, with clearer enabled/off contrast.

### 1.0.7 — 离线渲染 / Offline rendering

离线导出改用精确音频块处理，不再沿用实时调度的跳块或回退策略作为正常导出路径。

Adds exact-block processing for offline rendering instead of using realtime skip/fallback scheduling as the normal export path.

### 1.0.8 — 离线性能与故障提示 / Offline performance and fault reporting

使用事件唤醒减少等待开销，保护连续渲染的重置与旁通状态。异常时提供延迟匹配回退并标记 RENDER DEGRADED；这不代表效果处理导出成功。

Uses event-driven completion to reduce waiting overhead and protects render-pass reset and bypass state. Faults use latency-matched fallback and display RENDER DEGRADED; this is not a successful processed export.

### 1.0.9 — 局部刷新 / Local refresh

REFRESH 只恢复当前 Bridge；全局后台重启独立为需要明确确认的 Restart Agent (All Hosts)，减少其他机架被牵连的情况。

REFRESH restores only the current Bridge. Restart Agent (All Hosts) is a separate, explicitly confirmed global operation, reducing disruption to other racks.

### 1.0.10 — Imager 与手动恢复 / Imager and manual recovery

修正插件准备阶段的线程锁顺序，解决已复现的 Ozone 9 / 11 独立 Imager 卡住问题。不再因看门狗超时、机架拓扑变化或后台退出自动重启、反复恢复或自动关闭插件。保留初次启动、正常工程/预置恢复、局部 REFRESH 和明确确认的全局重启。

Fixes preparation lock ordering behind the reproduced standalone Ozone 9/11 Imager hang. Watchdog timeouts, rack-topology changes and Agent loss no longer automatically restart the Agent, repeatedly restore racks or power off plug-ins. Initial startup, normal project/preset restoration, local REFRESH and explicitly confirmed global restart remain available.

## 使用变化 / How to use the changes

- UI：点击 Bridge 顶部 UI，循环切换 Classic / Light / Dark。/ Click UI in the Bridge to cycle Classic / Light / Dark.
- 恢复：先保存工程，点击故障 Bridge 的 REFRESH。如果第三方插件完全卡住共享后台，局部刷新可能无法完成；必要时在“...”中选择 Restart Agent (All Hosts)，停止播放并保存后再确认，因为这会影响所有 Bridge。/ Save your project and use REFRESH on the affected Bridge. A plug-in that completely hangs the shared Agent may also prevent local refresh. If needed, stop playback, save, and explicitly confirm Restart Agent (All Hosts) in “...”; it affects every Bridge.
- 预置：覆盖保存两次指相同文件名并确认覆盖，不是另存两个名字；若仍未出现，在 MediaBay 对相应目录 Quick Rescan Disk。/ Saving twice means the same filename with overwrite confirmation, not two different names. If still missing, use MediaBay's Quick Rescan Disk on that folder.

## 兼容性、安装与升级 / Compatibility, installation and upgrade

- Windows 10/11 x64 VST3；macOS 11.0+ Apple Silicon VST3、Intel VST3、Universal 2 AU。VST3 包须匹配 DAW 的运行架构，Rosetta 下用 Intel 包。/ Windows 10/11 x64 VST3; macOS 11.0+ Apple Silicon VST3, Intel VST3 and Universal 2 AU. Match VST3 to the DAW's running architecture; use Intel for Rosetta.
- 安装前完全退出 DAW 与扫描器，把旧版移到不扫描的位置；Bridge 与后台 QQ Host 必须成套更新。Windows 把完整 QQ Host 文件夹放入 `C:\Program Files\Common Files\VST3\`；macOS 将 Bridge 放到对应 VST3/Components 目录，QQ Host.app 放到 Applications，然后重扫。详细路径与安全操作见双语安装说明。/ Quit DAWs/scanners, move old copies outside scan paths, and update Bridge and background Host together. On Windows copy the whole QQ Host folder into `C:\Program Files\Common Files\VST3\`. On macOS put Bridge in the matching VST3/Components folder and QQ Host.app in Applications, then rescan. See the guides for exact paths and safety steps.
- FL Studio：必须启用 **Use fixed size buffers**，并在 More 中同时启用 **Process maximum size buffers** 和 **Use maximum buffer size from host**，然后重载 Bridge。/ FL Studio requires **Use fixed size buffers**, plus **Process maximum size buffers** and **Use maximum buffer size from host** under More, then reload Bridge.
- macOS 包未经 Apple Developer ID 公证。仅对确认可信来源的实际安装文件按指南处理隔离属性，不要全局关闭 Gatekeeper。/ macOS packages are not Apple Developer ID notarized. Follow the guide only for trusted installed files; do not disable Gatekeeper globally.
- 手册沿用真实标为 1.0.6 的中英文 PDF，其中包含 UI、自动化与预置说明；1.0.10 安装说明补充手动恢复。/ The bilingual 1.0.6 PDFs retain their actual version labels and cover themes, automation and presets. The 1.0.10 guides supplement manual recovery.
- 旧版 [1.0.4](https://github.com/Qing-Audio/QQHost-Release/releases/tag/v1.0.4) 保留供回退；升级前备份重要工程。/ [1.0.4](https://github.com/Qing-Audio/QQHost-Release/releases/tag/v1.0.4) remains available for rollback; back up important sessions before upgrading.

## 已知限制 / Known limitations

性能改善依赖插件、DAW、Buffer 和电脑配置；低总 CPU 占用不能保证没有实时超时。侧链/PDC 依赖插件正确报告输入和延迟。跨格式预置兼容依赖真实身份和状态格式，不保证任意同名 VST2/VST3 都能互换。Cubase 的即时预置收录仍可能需要覆盖保存或重扫。出现 RENDER DEGRADED 时应处理故障后重新导出。第三方插件完全挂起共享后台时可能仍需全局重启。

Results depend on plug-ins, DAW, buffers and hardware; low total CPU use does not guarantee no realtime deadline misses. Sidechain/PDC depend on correct plug-in input and latency reports. Cross-format presets require compatible identities and state formats; matching names alone are insufficient. Cubase may still require overwrite-saving or rescanning for immediate discovery. Resolve RENDER DEGRADED before rendering again. A plug-in hanging the shared Agent may still require global restart.

## 下载附件 / Download assets

- [Windows x64 VST3](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.0.10/QQ.Host.1.0.10.Windows.x64.VST3.zip)
- [macOS Apple Silicon VST3](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.0.10/QQ.Host.1.0.10.macOS.Apple.Silicon.VST3.zip)
- [macOS Intel x86_64 VST3](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.0.10/QQ.Host.1.0.10.macOS.Intel.x86_64.VST3.zip)
- [macOS Universal 2 AU](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.0.10/QQ.Host.1.0.10.macOS.Universal.2.AU.zip)
- [中文安装说明 / Chinese installation guide](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.0.10/QQ.Host.1.0.10.Installation.Guide.Chinese.txt)
- [English installation guide](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.0.10/QQ.Host.1.0.10.Installation.Guide.English.txt)
- [1.0.6 中文手册 / Chinese manual](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.0.10/QQ.Host.1.0.6.User.Manual.Chinese.pdf)
- [1.0.6 English manual](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.0.10/QQ.Host.1.0.6.User.Manual.English.Edition.pdf)

QQ Host 为闭源软件。本仓库只提供公开成品及用户文档；源码保持私有。GitHub 自动附带的 Source code ZIP/TAR 是下载页资料快照，不是插件安装包。

QQ Host is closed-source. This repository provides public binaries and user documentation only; source stays private. GitHub's automatic Source code ZIP/TAR files are download-page snapshots, not plug-in installers.
