# QQ Host 1.1.5 Stable / Power

发布日期 / Release date: 2026-10-12
上一稳定版本 / Previous Stable: 1.1.4

## 中文

- 将原 OFFLOAD Buffer 与 Processing 合并为 Mode 与 SC 之间的 Power 星级按钮，单击循环切换五档。
- 五档依次为：1 buffer 串行；2 buffers 串行；2 buffers 两阶段优化；3 buffers 两阶段优化；4 buffers 两阶段优化。
- 新建默认两星（2 buffers + 串行）；已有工程及重新打开的界面保留原档位。LIVE 下 Power 文字和星级变灰且不可点击，切回 OFFLOAD 保留选择。
- 悬停说明：★越大，性能节省越强，代价是延迟也更高。星形用矢量绘制，中文显式 UTF-8。
- 中英文手册更新了主界面、Power 操作、默认值、保存与 LIVE 状态，替换旧菜单说明。
- 本版延续已有 Refresh、Waves 与预置修复，没有额外独立故障修复声明。

## English

- Replaces the separate OFFLOAD Buffer and Processing menus with a Power star button between Mode and SC; a click cycles five levels.
- Levels map to: 1 buffer serial; 2 buffers serial; 2 buffers with two-stage optimization; 3 buffers with two-stage optimization; 4 buffers with two-stage optimization.
- New instances default to two stars (2 buffers + serial). Saved projects and reopened editors retain their choice. Power is gray and disabled in LIVE, and returning to OFFLOAD retains the selection.
- A short Chinese tooltip explains the performance/latency trade-off. Stars use vector geometry and Chinese text uses explicit UTF-8.
- Chinese and English manuals update the main window, Power operation, defaults, saving and LIVE behavior, replacing the old menu instructions.
- Existing Refresh, Waves and preset fixes are retained; no additional standalone defect fix is claimed in this release.

## 兼容与升级 / Compatibility and upgrade

Windows 10/11 x64 VST3; macOS 12+ Apple Silicon VST3, Intel x86_64 VST3, Universal 2 AU.
升级前退出 DAW 与 QQ Host，成对升级 Bridge 和后台程序。/ Quit the DAW and QQ Host before upgrading both the Bridge and background app together.
三星至五星选择两阶段优化，但实际启用仍取决于机架、路由及测量；两星与三星同为 2 buffers。旧工程的 3/4 buffers 串行设置保持有效，按钮显示短横线，首次点击进入一星。
Three to five stars select two-stage optimization, subject to rack, routing and profiling eligibility. Two and three stars both use 2 buffers. Legacy 3/4-buffer serial settings remain valid and display a dash until the first click selects one star.

## 验证 / Validation

复用已通过的 Windows Release、音频状态/PDC/实时与离线回归、171 项离屏界面检查和本机安装哈希。三套 Mac 成品的架构、版本、签名与编码检查通过；不将编译通过宣称为所有 DAW 的界面或听感验收。
Reuses the passing Windows Release, audio/state/PDC/realtime/offline regressions, 171 offscreen UI checks and local installation hashes. All three Mac packages passed architecture, version, signature and encoding checks; builds are not claimed as GUI/listening acceptance in every DAW.

## 安装与附件 / Installation and assets

退出 DAW 和 QQ Host 后成对升级 Bridge 与后台程序。Mac 使用 ad-hoc 签名，未公证；详细安装步骤见双语指南。源码保持私有，附件仅包含四种成品、两份安装说明及两份新版手册。
Quit the DAW and QQ Host before upgrading the Bridge and background app together. Mac bundles use ad-hoc signatures and are not notarized; follow the bilingual guides. Source stays private; the eight assets contain four platform packages, two guides and two updated manuals.

- [Windows x64 VST3](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.5/QQ.Host.1.1.5.Windows.x64.VST3.zip)
- [macOS Apple Silicon VST3](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.5/QQ.Host.1.1.5.macOS.Apple.Silicon.VST3.zip)
- [macOS Intel x86_64 VST3](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.5/QQ.Host.1.1.5.macOS.Intel.x86_64.VST3.zip)
- [macOS Universal 2 AU](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.5/QQ.Host.1.1.5.macOS.Universal.2.AU.zip)
- [中文安装说明 / Chinese installation guide](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.5/QQ.Host.1.1.5.Installation.Guide.Chinese.txt)
- [English installation guide](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.5/QQ.Host.1.1.5.Installation.Guide.English.txt)
- [中文用户手册 / Chinese user manual](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.5/QQ.Host.1.1.5.User.Manual.Chinese.pdf)
- [English user manual](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.5/QQ.Host.1.1.5.User.Manual.English.Edition.pdf)
