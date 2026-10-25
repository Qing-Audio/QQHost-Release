# QQ Host 1.3.13

Qing Audio · Stable · 2026-10-25

## 本次更新 / Changes since 1.3.9

### 1.3.13

中文：修复从 Cubase 历史撤销插件移除后，ChainScope Group 名称出现“(副本)”的问题。恢复插入、移除或排序操作时保留仍在机架中的插件及其当前状态，恢复缺失的插件。多步撤销和重做也保留正确的链接关系。用户已确认本次修复有效。

English: Fixes the unwanted copy suffix on a ChainScope Group after restoring a removed plug-in through Cubase history. Structural undo and redo preserve surviving plug-ins and their current state while restoring missing slots, including across multiple history steps. The user confirmed the fix.

### 1.3.12

中文：修复恢复 C Mixboard 后与原 Group 断开、变成 Standalone 的问题。恢复已有机架时保留匹配的插件实例和链接关系。QQ Host 内部撤销已能保留 Group 名称；Cubase 撤销仍出现的副本名称由 1.3.13 继续修复。

English: Fixes C Mixboard losing its original Group and appearing as Standalone after restoration. Matching plug-in instances and rack links are retained. Internal undo preserves Group names; the remaining Cubase-undo copy-suffix issue is addressed in 1.3.13.

### 1.3.11

中文：修正机架编辑通知，使 Cubase 历史能够记录并撤销 QQ Host 内的插件插入、移除。保留旧工程和参数映射兼容性。

English: Corrects rack edit notifications so Cubase history can record and undo plug-in insertion and removal within QQ Host, while retaining existing project and parameter-mapping compatibility.

### 1.3.10

中文：加入向 DAW 报告机架插入、移除、复制、排序和加载插件链操作的历史支持。QQ Host 内部撤销可用；此版仍未在 Cubase 历史中出现记录，后续由 1.3.11 修正。

English: Introduces DAW history support for rack insertion, removal, duplication, reordering and chain loading. Internal undo worked, but Cubase did not yet show history entries in this version; 1.3.11 corrects that issue.


## 下载 / Downloads

- [Windows x64 VST3](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.3.13/QQ.Host.1.3.13.Windows.x64.VST3.zip)
- [macOS Apple Silicon VST3](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.3.13/QQ.Host.1.3.13.macOS.Apple.Silicon.VST3.zip)
- [macOS Intel x86_64 VST3](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.3.13/QQ.Host.1.3.13.macOS.Intel.x86_64.VST3.zip)
- [macOS Universal 2 AU](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.3.13/QQ.Host.1.3.13.macOS.Universal.2.AU.zip)
- [中文安装说明 / Chinese installation guide](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.3.13/QQ.Host.1.3.13.Installation.Guide.Chinese.txt)
- [English installation guide](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.3.13/QQ.Host.1.3.13.Installation.Guide.English.txt)
- [中文用户手册（沿用 1.3.6）/ Chinese manual (1.3.6)](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.3.13/QQ.Host.1.3.6.User.Manual.Chinese.pdf)
- [English user manual (unchanged 1.3.6 edition)](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.3.13/QQ.Host.1.3.6.User.Manual.English.Edition.pdf)

本次沿用已批准的 1.3.6 中英文手册，PDF 内容与版本标识保持不变。

The approved 1.3.6 Chinese and English manuals are reused unchanged with their original version labels.

Each platform package contains the Bridge and matching background app. Upgrade both together.
每个平台包包含 Bridge 和配套后台，请成对升级。

## 安装与使用 / Installation and use

退出 DAW、扫描器和 QQ Host，**同时升级 Bridge 和后台程序为 1.3.13**，避免混用旧后台。Windows 将 `QQ Host Bridge.vst3` 与 `QQ Host.exe` 相邻安装到 `C:\Program Files\Common Files\VST3\QQ Host\`。Mac VST3 将 Bridge 与配套 app 一起放到 `~/Library/Audio/Plug-Ins/VST3/QQ Host/`；AU 放到 `~/Library/Audio/Plug-Ins/Components/QQ Host/`。重开 DAW 并扫描；完整安装和 Mac 安全处理步骤见双语安装说明。

Quit the DAW, scanners and QQ Host. **Upgrade both the Bridge and background app to 1.3.13**. On Windows, keep `QQ Host Bridge.vst3` beside `QQ Host.exe` in `C:\Program Files\Common Files\VST3\QQ Host\`. On Mac, place the Bridge and companion app together in `~/Library/Audio/Plug-Ins/VST3/QQ Host/` for VST3 or `~/Library/Audio/Plug-Ins/Components/QQ Host/` for AU. Reopen and rescan in the DAW. The bilingual installation guides include complete steps and Mac security handling.

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

Mac 成品为 ad-hoc 签名，未公证。Windows 已完成构建、成对安装、30 组旁通连续性和 24 组分段侧链对比，以及保存方案回归；完整原生窗口回归仍保留此前未完成记录。三套 Mac 成品已核对架构、版本、可执行权限、签名和 UTF-8 中文文字，尚未完成原生 Mac DAW 界面及声音实测。性能改善仍取决于插件负载、路由、缓冲和电脑配置。

Mac bundles are ad-hoc signed and not notarized. Windows build, paired installation, 30 bypass continuity cases, 24 staged sidechain comparisons and saved-plan regressions passed. The inherited full native-window regression remains incomplete. The three Mac packages have passed architecture, version, executable-permission, signature and UTF-8 text checks; native Mac DAW GUI/audio acceptance has not been performed. Performance benefits depend on the plug-ins, routing, buffering and computer.

1.3.13 的六项 Windows 回归通过，覆盖真实 VST3 历史通知、实际 ChainScope A/B/C 恢复、机架上下文、已保存方案及旁通连续性；用户已确认 Cubase 中的 Group 恢复问题解决。本轮未重跑 Windows 原生窗口回归，未进行原生 Mac DAW 界面和声音验收。

Six focused Windows regressions passed for 1.3.13, including native VST3 history notifications, actual ChainScope A/B/C restoration, rack context, saved plans and bypass continuity. The user confirmed the Cubase Group-restoration fix. Native Windows window tests were not rerun in this task; native Mac DAW GUI/audio acceptance was not performed.

QQ Host 为闭源专有软件，本下载仓库只提供公开成品与说明，源码保持私有。
QQ Host is proprietary software. This repository contains public binaries and documentation; source remains private.
GitHub 自动生成的 Source code ZIP/TAR 仅包含本下载仓库的页面资料。
GitHub's automatic Source code ZIP/TAR contains this download repository's pages.
