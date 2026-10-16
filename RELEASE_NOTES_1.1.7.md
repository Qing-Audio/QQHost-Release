# QQ Host 1.1.7

Qing Audio · Stable · 2026-10-16

## 本次更新 / Changes

### 1.1.7 — Add Plugin 悬停说明 / Add Plugin tooltip — 2026-10-16

中文：Add Plugin 新增“左键添加插件；右键可新增标签（Divider）。”悬停说明。
侧链添加入口显示“点击添加侧链插件。”。中文使用显式 UTF-8；点击行为、工程状态和音频处理保持原样。
插件和后台程序统一升级至 1.1.7。双语说明书原样沿用 1.1.6 的 20261014 修订版，保留原版本标识。

English: Add Plugin now explains left-click to add a plug-in and right-click to add
a Divider label. The sidechain add entry has an add-only hint. Chinese uses explicit UTF-8;
click behavior, project state and audio processing are unchanged. Both plug-in and background
app report 1.1.7. The unchanged 20261014 Chinese and English manuals for 1.1.6 retain their original labels.

## 兼容性与安装 / Compatibility and installation

Windows 10/11 x64 VST3；macOS 12+ Apple Silicon VST3、Intel x86_64 VST3 与 Universal 2 AU。
升级前完全退出 DAW、扫描器及 QQ Host，成对替换 Bridge 和后台程序，然后重新扫描。
Mac 使用 ad-hoc 签名，未公证；具体安装路径、安全处理和故障排查见随包双语安装说明。

Windows 10/11 x64 VST3; macOS 12+ Apple Silicon VST3, Intel x86_64 VST3 and Universal 2 AU.
Fully quit DAWs, scanners and QQ Host before replacing both Bridge and background app, then rescan.
Mac bundles use ad-hoc signatures and are not notarized. See the bilingual guides for exact paths, security handling and troubleshooting.

## 验证与已知限制 / Validation and known limits

Windows 成品复用已核验的 1.1.7 构建与安装结果；三套 Mac 成品通过版本、架构、签名和中文编码检查。
本版仅增加操作提示，没有新增音频或点击行为修复。仅支持原生 64-bit 效果器；不支持乐器或 32-bit 插件。
构建检查不能替代每个 DAW/第三方插件的界面和声音实测，也不保证全部第三方安装兼容。

Windows reuses the verified 1.1.7 build and installation. All three Mac packages pass version, architecture, signature and compiled Chinese-text checks.
This version adds usage hints without new audio or click-behavior fixes. Native 64-bit effects only; instruments and 32-bit plug-ins are unsupported.
Build checks do not replace GUI/audio acceptance in every DAW or guarantee compatibility with every third-party installation.

## 附件与说明书 / Assets and manuals

四类平台安装包、两份安装说明、两份上一版原样说明书，共八个附件。手册保留 1.1.6 / 20261014 原标识。
Four platform packages, two installation guides and two unchanged previous-edition manuals: eight assets. Manuals retain their 1.1.6 / 20261014 labels.

闭源软件，源码保持私有；本发布不含源码或内部资料。旧 Release 保留供回退。
Closed-source software; source remains private. No source or internal material is included. Earlier releases remain available for rollback.

- [Windows x64 VST3](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.7/QQ.Host.1.1.7.Windows.x64.VST3.zip)
- [macOS Apple Silicon VST3](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.7/QQ.Host.1.1.7.macOS.Apple.Silicon.VST3.zip)
- [macOS Intel x86_64 VST3](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.7/QQ.Host.1.1.7.macOS.Intel.x86_64.VST3.zip)
- [macOS Universal 2 AU](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.7/QQ.Host.1.1.7.macOS.Universal.2.AU.zip)
- [中文安装说明 / Chinese installation guide](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.7/QQ.Host.1.1.7.Installation.Guide.Chinese.txt)
- [English installation guide](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.7/QQ.Host.1.1.7.Installation.Guide.English.txt)
- [中文用户手册 / Chinese user manual (1.1.6, 20261014)](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.7/QQ.Host.1.1.6.20261014.User.Manual.Chinese.pdf)
- [English user manual (1.1.6, 20261014)](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.7/QQ.Host.1.1.6.20261014.User.Manual.English.Edition.pdf)
