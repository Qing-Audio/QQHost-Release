# QQ Host 1.3.6

Qing Audio · Stable · 2026-10-22

## 本次更新 / This release

1.3.6 完善同一 Host 内的多线程分段与 ChainScope 对齐。本次公开更新还包含 1.1.8 以来的缺失插件预置链恢复、Cubase 后台释放兼容、Search 和快捷键、测试与增加余量、右键菜单及电平表修正。中英文手册同步为 38 页，保留原配色并按使用顺序整理。

1.3.6 improves multi-threaded chain splitting with ChainScope alignment. This public update also includes the changes since 1.1.8 for missing plug-ins in chains, Cubase background-driver release, Search and shortcuts, Test and Add Headroom, popup menus and meters. Both manuals now have 38 matching pages, using the original palette and a task-based chapter order.

## 新增功能与行为 / Features and behavior

- 测试后自动选择缓冲与链内分段，出现新瓶颈时增加余量 / Measured buffer and multi-stage plans, with extra headroom after new bottlenecks.
- LIVE 低延迟录音监听 / LIVE for recording and immediate monitoring.
- 每个 Bridge 最多 16 个主插件槽、2 个侧链效果器槽 / Up to 16 main plug-in slots and two Sidechain FX slots per Bridge.
- Divider、格式筛选、收藏及扫描目录管理 / Dividers, format filters, favorites and scan-path management.
- 自动 PDC、侧链对齐与 Latency Rescue / Automatic PDC, sidechain alignment and Latency Rescue.
- 插件预置、Cubase 预置链、DAW 工程恢复与自动化 / Plug-in presets, Cubase chain presets, project recall and automation.
- 插件内部撤销重做、DAW 保存及空格转发 / Plug-in Undo/Redo with DAW Save and Space forwarding.
- Fader、Pan、Polarity、电平表及主链/单槽试听 / Fader, Pan, Polarity, meters and whole-chain or per-slot bypass auditioning.

## 安装与升级 / Installation and upgrades

退出 DAW、扫描器和 QQ Host，**同时升级 Bridge 和后台程序为 1.3.6**，避免混用旧后台。Windows 将 `QQ Host Bridge.vst3` 与 `QQ Host.exe` 相邻安装到 `C:\Program Files\Common Files\VST3\QQ Host\`。Mac VST3 将 Bridge 与配套 app 一起放到 `~/Library/Audio/Plug-Ins/VST3/QQ Host/`；AU 放到 `~/Library/Audio/Plug-Ins/Components/QQ Host/`。重开 DAW 并扫描；完整安装和 Mac 安全处理步骤见双语安装说明。

Quit the DAW, scanners and QQ Host. **Upgrade both the Bridge and background app to 1.3.6**. On Windows, keep `QQ Host Bridge.vst3` beside `QQ Host.exe` in `C:\Program Files\Common Files\VST3\QQ Host\`. On Mac, place the Bridge and companion app together in `~/Library/Audio/Plug-Ins/VST3/QQ Host/` for VST3 or `~/Library/Audio/Plug-Ins/Components/QQ Host/` for AU. Reopen and rescan in the DAW. The bilingual installation guides include complete steps and Mac security handling.

混音时让 LIVE 保持关闭，加载插件后播放有声、负载较重的片段，点击“测试”；测量结束后停止播放，应用方案。标题下方显示 buffer、处理段数和延迟。出现瓶颈、“增加余量”亮起时，点击一次并停止播放以应用；按钮会变灰，遇到新的瓶颈后可再次使用。换插件后重新测试。DAW 工程及 DAW 保存的 Bridge 预置保留应用后的方案；LOAD CHAIN / SAVE CHAIN 继续加载、保存插件链。

For mixing, leave LIVE off, load effects and play an audible, demanding passage. Click Test and stop after measurement finishes to apply the plan. The header shows buffers, processing stages and latency. When a bottleneck enables Add Headroom, click once and stop to apply. It dims until another bottleneck occurs. Retest after changing plug-ins. DAW projects and DAW-saved Bridge presets retain the applied plan; LOAD CHAIN / SAVE CHAIN exchange plug-in chains.

LIVE 用于录音和实时监听，QQ Host 不再额外等待整块缓冲。1 buffer / 1 段则由一个后台线程运行插件链，并在 DAW 原有缓冲基础上增加一个音频块的时间余量。buffer 越高，通常越容易稳定运行，同时延迟也更高。旧工程可以继续打开；升级后先试听，再根据当前插件链重新测试。

Use LIVE for recording or immediate monitoring, with no added whole-block buffering delay. With 1 buffer / 1 stage, one background thread runs the chain with one extra audio block of timing headroom beyond the DAW's existing buffering. Higher buffer counts usually improve stability while adding latency. Existing projects remain loadable; audition after upgrading, then retest for the current chain.

左键点击 + Add Plugin 添加插件；右键选择 Insert Divider 创建标签，双击命名。Search 旁边可筛选格式；Manage 可扫描单个文件或按格式增量扫描，Folders 可移除扫描目录。

Left-click + Add Plugin to load an effect; right-click and choose Insert Divider to add a label, then double-click to name it. Filter formats beside Search. Manage scans a file or incrementally scans a format; Folders removes scan paths.

卡在启动或恢复时，先点主界面 REFRESH；仍无效则停止播放，在右上角“...”中选择“重启全部 QQ Host”，确认“重启全部”。共用后台的其他 Host（包括其他 DAW）也会暂时断开并恢复。浏览器 Refresh 用于增量扫描。

For stuck startup or recovery, try the main REFRESH. If needed, stop playback and use “重启全部 QQ Host” (Restart All QQ Hosts) in the top-right “...” menu, then confirm. Other instances sharing the background app, including other DAWs, also disconnect temporarily and restore. Browser Refresh scans incrementally.

## 兼容性、验证和已知限制 / Compatibility, validation and known limitations

Windows 10/11 x64 VST3；macOS 12+ Apple Silicon VST3、Intel x86_64 VST3、Universal 2 AU。VST3 按宿主架构选择；AU 包包含 arm64 与 x86_64。托管原生 64-bit VST2/VST3 效果器，macOS 另支持 AUv2/AUv3；不支持 32-bit 插件或乐器。

Windows 10/11 x64 VST3; macOS 12+ Apple Silicon VST3, Intel x86_64 VST3 and Universal 2 AU. Match VST3 to the host architecture; AU includes arm64 and x86_64. Hosts native 64-bit VST2/VST3 effects, plus AUv2/AUv3 on macOS; 32-bit plug-ins and instruments are unsupported.

ChainScope 跨段对齐需要另行安装配套的 ChainScope 1.8.1，四个模块须一起升级。完整且位于同一 QQ Host 内的 A/B/C 组可以分段；旧版、不完整、跨 Host 或包含 D 的组保留保护。本 Release 不包含 ChainScope。

Cross-stage ChainScope alignment requires the separate matching ChainScope 1.8.1 installation; upgrade all four modules together. Complete A/B/C groups within one QQ Host can be split. Older, incomplete, cross-Host or D-containing groups retain protection. ChainScope is not included in this release.

Mac 成品为 ad-hoc 签名，未公证。Windows 已完成构建、回归和安装核对；三套 Mac 成品已核对架构、版本、可执行权限、签名和 UTF-8 中文文字，尚未完成原生 Mac DAW 界面及声音实测。性能改善仍取决于插件负载、路由、缓冲和电脑配置。

Mac bundles are ad-hoc signed and not notarized. Windows build, regression and installation checks are complete. The three Mac packages have passed architecture, version, executable-permission, signature and UTF-8 text checks; native Mac DAW GUI/audio acceptance has not been performed. Performance benefits depend on the plug-ins, routing, buffering and computer.

## 下载附件 / Downloads

- [Windows x64 VST3](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.3.6/QQ.Host.1.3.6.Windows.x64.VST3.zip)
- [macOS Apple Silicon VST3](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.3.6/QQ.Host.1.3.6.macOS.Apple.Silicon.VST3.zip)
- [macOS Intel x86_64 VST3](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.3.6/QQ.Host.1.3.6.macOS.Intel.x86_64.VST3.zip)
- [macOS Universal 2 AU](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.3.6/QQ.Host.1.3.6.macOS.Universal.2.AU.zip)
- [中文安装说明 / Chinese installation guide](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.3.6/QQ.Host.1.3.6.Installation.Guide.Chinese.txt)
- [English installation guide](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.3.6/QQ.Host.1.3.6.Installation.Guide.English.txt)
- [中文用户手册 / Chinese user manual](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.3.6/QQ.Host.1.3.6.User.Manual.Chinese.pdf)
- [English user manual](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.3.6/QQ.Host.1.3.6.User.Manual.English.Edition.pdf)

中英文手册均为本版 38 页版本。插件安装包内包含 Bridge 与配套后台，二者需一起更新。QQ Host 为闭源软件；本仓库只提供公开下载资料，源码未公开。GitHub 自动生成的 Source code ZIP/TAR 包含本下载仓库的页面资料。

Both manuals are the matching 38-page editions. Each platform package includes the Bridge and companion background app; upgrade them together. QQ Host is closed-source; this repository contains public download materials and no private source. GitHub's automatic Source code ZIP/TAR contains this download repository's pages.

## 自上次公开版本 1.1.7 以来的逐版本记录 / Every version since public release 1.1.7

### 1.3.6

中文：接入 ChainScope 1.8.1 的跨段音频标记，完整本地组可以安全分段；中英文手册按原配色整理章节，补齐测量、缓冲、分段、LIVE 和 Divider 用法。

English: Use ChainScope 1.8.1 block identity to safely split complete local groups. Reorganize the Chinese and English manuals in the original palette, covering testing, buffers, stages, LIVE and Dividers.

### 1.3.5

中文：修正测量负载判断、完成包观察和增加余量触发，避免持续给出不合理的低缓冲方案。

English: Correct load measurement, completion observation and headroom eligibility under overload.

### 1.3.4

中文：电平表直接读取音频块峰值，提高更新速度和瞬态响应。

English: Read accumulated block peaks directly for faster, more responsive output meters.

### 1.3.3

中文：修正 Metric AB 的 Delete Cue 等弹出菜单被提前关闭。

English: Keep hosted plug-in popup menus such as Metric AB Delete Cue open.

### 1.3.2

中文：修正测量结束、停止播放时方案应用的锁和顺序，避免卡死。

English: Fix locking and ordering when applying a measured plan after transport stops.

### 1.3.1

中文：LIVE 改为独立按钮；Stage 移至底部并从新 DAW 状态中移除。

English: Add the LIVE toggle; show Stage in the footer and omit it from newly saved DAW state.

### 1.3.0

中文：测试后自动选择缓冲和链内分段；按新瓶颈增加余量，并随 DAW 状态保存；新实例默认收起 SC。

English: Measure and apply a buffered multi-stage plan, add headroom on fresh bottlenecks and save it with DAW state; SC starts hidden.

### 1.2.6

中文：插件内部撤销、重做留给插件；保留保存和空格转发。

English: Keep Undo/Redo inside the plug-in while retaining host Save and transport forwarding.

### 1.2.5

中文：补齐原生窗口的组合键转发和修饰键状态。 本版曾将插件撤销、重做转发给宿主，此行为在 1.2.6 修正。

English: Add native-frame shortcut forwarding with correct modifier and key-up handling. This version also forwarded plug-in Undo/Redo to the host; 1.2.6 corrects that behavior.

### 1.2.4

中文：修正打开、关闭和重开插件时的应用激活及后台释放通知。

English: Preserve consistent Cubase activation during editor creation, closure and reopening.

### 1.2.3

中文：保护 Search 输入，修正新打开插件时首次空格播放。

English: Protect browser text input from host accelerators and restore first-Space forwarding.

### 1.2.2

中文：校验后台 EXE 的版本和身份，避免连接错误安装版本。

English: Verify Agent executable version and identity to avoid selecting the wrong installation.

### 1.2.1

中文：补齐插件内部点击和控件激活的窗口交接。

English: Handle editor mouse activation and internal controls in the native frame.

### 1.2.0

中文：Windows Cubase 的插件窗口由 DAW 外层窗口承接，处理仍在后台，改善释放后台驱动时的激活。

English: DAW-owned native editor frames preserve Cubase activation while DSP stays in the Agent.

### 1.1.8

中文：Cubase 预置链遇到缺失插件时提示并继续加载其他插件；中文详情可滚动和复制。

English: Continue importing available plug-ins after missing entries; scrollable, copyable Chinese error details.
