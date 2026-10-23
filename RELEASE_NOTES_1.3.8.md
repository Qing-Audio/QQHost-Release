# QQ Host 1.3.8

Qing Audio · Stable · 2026-10-24

## 本次更新 / Changes since 1.3.7

### 1.3.8

中文：针对 Windows 下 Overloud TH-U 的内嵌右键菜单加入窗口兼容处理，修复菜单打开后立即消失、无法选择移除单块的问题。同时适配插件窗口激活、关闭、移动和快捷键传递，保留后台释放兼容逻辑及插件内部撤销/重做。其他插件继续使用原有窗口处理方式。沿用 1.3.6 中文、英文手册。

English: Adds window compatibility for Overloud TH-U embedded context menus on Windows, addressing menus disappearing before an effect can be removed. Editor activation, closing, movement and shortcut forwarding are adapted together, retaining background-driver compatibility and plug-in-local Undo/Redo. Other plug-ins keep their existing window handling. The 1.3.6 Chinese and English manuals are reused unchanged.

## 下载 / Downloads

- [Windows x64 VST3](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.3.8/QQ.Host.1.3.8.Windows.x64.VST3.zip)
- [macOS Apple Silicon VST3](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.3.8/QQ.Host.1.3.8.macOS.Apple.Silicon.VST3.zip)
- [macOS Intel x86_64 VST3](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.3.8/QQ.Host.1.3.8.macOS.Intel.x86_64.VST3.zip)
- [macOS Universal 2 AU](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.3.8/QQ.Host.1.3.8.macOS.Universal.2.AU.zip)
- [中文安装说明 / Chinese installation guide](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.3.8/QQ.Host.1.3.8.Installation.Guide.Chinese.txt)
- [English installation guide](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.3.8/QQ.Host.1.3.8.Installation.Guide.English.txt)
- [中文用户手册（沿用 1.3.6）/ Chinese manual (1.3.6)](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.3.8/QQ.Host.1.3.6.User.Manual.Chinese.pdf)
- [English user manual (unchanged 1.3.6 edition)](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.3.8/QQ.Host.1.3.6.User.Manual.English.Edition.pdf)

本次按用户要求沿用 1.3.6 中英文手册，PDF 内容和版本标识保持不变。1.3.8 的菜单兼容修复见本页更新说明。

The approved 1.3.6 bilingual manuals are reused without changing their contents or version labels. The 1.3.8 menu compatibility fix is described on this page.

Each platform package contains the Bridge and matching background app. Upgrade both together.
每个平台包包含 Bridge 和配套后台，请成对升级。

## 安装与使用 / Installation and use

退出 DAW、扫描器和 QQ Host，**同时升级 Bridge 和后台程序为 1.3.8**，避免混用旧后台。Windows 将 `QQ Host Bridge.vst3` 与 `QQ Host.exe` 相邻安装到 `C:\Program Files\Common Files\VST3\QQ Host\`。Mac VST3 将 Bridge 与配套 app 一起放到 `~/Library/Audio/Plug-Ins/VST3/QQ Host/`；AU 放到 `~/Library/Audio/Plug-Ins/Components/QQ Host/`。重开 DAW 并扫描；完整安装和 Mac 安全处理步骤见双语安装说明。

Quit the DAW, scanners and QQ Host. **Upgrade both the Bridge and background app to 1.3.8**. On Windows, keep `QQ Host Bridge.vst3` beside `QQ Host.exe` in `C:\Program Files\Common Files\VST3\QQ Host\`. On Mac, place the Bridge and companion app together in `~/Library/Audio/Plug-Ins/VST3/QQ Host/` for VST3 or `~/Library/Audio/Plug-Ins/Components/QQ Host/` for AU. Reopen and rescan in the DAW. The bilingual installation guides include complete steps and Mac security handling.

混音时让 LIVE 保持关闭，加载插件后播放有声、负载较重的片段，点击“测试”；测量结束后停止播放，应用方案。标题下方显示 buffer、处理段数和延迟。出现瓶颈、“增加余量”亮起时，点击一次并停止播放以应用；按钮会变灰，遇到新的瓶颈后可再次使用。换插件后重新测试。DAW 工程及 DAW 保存的 Bridge 预置保留应用后的方案；LOAD CHAIN / SAVE CHAIN 继续加载、保存插件链。

For mixing, leave LIVE off, load effects and play an audible, demanding passage. Click Test and stop after measurement finishes to apply the plan. The header shows buffers, processing stages and latency. When a bottleneck enables Add Headroom, click once and stop to apply. It dims until another bottleneck occurs. Retest after changing plug-ins. DAW projects and DAW-saved Bridge presets retain the applied plan; LOAD CHAIN / SAVE CHAIN exchange plug-in chains.

LIVE 用于录音和实时监听，QQ Host 不再额外等待整块缓冲。1 buffer / 1 段则由一个后台线程运行插件链，并在 DAW 原有缓冲基础上增加一个音频块的时间余量。buffer 越高，通常越容易稳定运行，同时延迟也更高。旧工程可以继续打开；升级后先试听，再根据当前插件链重新测试。

Use LIVE for recording or immediate monitoring, with no added whole-block buffering delay. With 1 buffer / 1 stage, one background thread runs the chain with one extra audio block of timing headroom beyond the DAW's existing buffering. Higher buffer counts usually improve stability while adding latency. Existing projects remain loadable; audition after upgrading, then retest for the current chain.

左键点击 + Add Plugin 添加插件；右键选择 Insert Divider 创建标签，双击命名。Search 旁边可筛选格式；Manage 可扫描单个文件或按格式增量扫描，Folders 可移除扫描目录。

Left-click + Add Plugin to load an effect; right-click and choose Insert Divider to add a label, then double-click to name it. Filter formats beside Search. Manage scans a file or incrementally scans a format; Folders removes scan paths.

卡在启动或恢复时，先点主界面 REFRESH；仍无效则停止播放，在右上角“...”中选择“重启全部 QQ Host”，确认“重启全部”。共用后台的其他 Host（包括其他 DAW）也会暂时断开并恢复。浏览器 Refresh 用于增量扫描。

For stuck startup or recovery, try the main REFRESH. If needed, stop playback and use “重启全部 QQ Host” (Restart All QQ Hosts) in the top-right “...” menu, then confirm. Other instances sharing the background app, including other DAWs, also disconnect temporarily and restore. Browser Refresh scans incrementally.

## 兼容性与验证 / Compatibility and validation

Windows 10/11 x64 VST3；macOS 12+ Apple Silicon VST3、Intel x86_64 VST3、Universal 2 AU。VST3 按宿主架构选择；AU 包包含 arm64 与 x86_64。托管原生 64-bit VST2/VST3 效果器，macOS 另支持 AUv2/AUv3；不支持 32-bit 插件或乐器。

Windows 10/11 x64 VST3; macOS 12+ Apple Silicon VST3, Intel x86_64 VST3 and Universal 2 AU. Match VST3 to the host architecture; AU includes arm64 and x86_64. Hosts native 64-bit VST2/VST3 effects, plus AUv2/AUv3 on macOS; 32-bit plug-ins and instruments are unsupported.

ChainScope 跨段对齐需要另行安装配套的 ChainScope 1.8.1，四个模块须一起升级。完整且位于同一 QQ Host 内的 A/B/C 组可以分段；旧版、不完整、跨 Host 或包含 D 的组保留保护。本 Release 不包含 ChainScope。

Cross-stage ChainScope alignment requires the separate matching ChainScope 1.8.1 installation; upgrade all four modules together. Complete A/B/C groups within one QQ Host can be split. Older, incomplete, cross-Host or D-containing groups retain protection. ChainScope is not included in this release.

Mac 成品为 ad-hoc 签名，未公证。Windows 已完成构建与安装核对，Search 通过 16 项检查；完整原生窗口回归尚未完成。三套 Mac 成品已核对架构、版本、可执行权限、签名和 UTF-8 中文文字，尚未完成原生 Mac DAW 界面及声音实测。性能改善仍取决于插件负载、路由、缓冲和电脑配置。

Mac bundles are ad-hoc signed and not notarized. Windows build and installation checks are complete; Search passed 16 checks. Full native-window regression remains unfinished. The three Mac packages have passed architecture, version, executable-permission, signature and UTF-8 text checks; native Mac DAW GUI/audio acceptance has not been performed. Performance benefits depend on the plug-ins, routing, buffering and computer.

QQ Host 为闭源专有软件，本下载仓库只提供公开成品与说明，源码保持私有。
QQ Host is proprietary software. This repository contains public binaries and documentation; source remains private.
GitHub 自动生成的 Source code ZIP/TAR 仅包含本下载仓库的页面资料。
GitHub's automatic Source code ZIP/TAR contains this download repository's pages.
