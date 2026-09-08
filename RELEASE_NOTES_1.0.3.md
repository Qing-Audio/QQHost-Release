# QQ Host 1.0.3

**正式稳定版 / Stable · 2026-09-09**

**QQ Host｜性能桥接机架，一个可以将 DAW 内的单核处理分散成多核处理的效果器。**

**QQ Host | A performance bridge rack that moves CPU-intensive processing away from the DAW's single real-time thread so the work can be spread across more CPU cores.**

在轨道 Insert 中插入 QQ Host Bridge，再在 Bridge 里加载效果器；后台 QQ Host 接管处理，无需另建一个 Mixer。OFFLOAD 适合希望分担实时 CPU 压力的混音工作；LIVE 优先减少桥接等待，不提供与 OFFLOAD 相同的 CPU 卸载优势。它不会把单个插件内部的单线程算法自动变成多线程算法。

Insert QQ Host Bridge on a track, then load effects inside the Bridge. The background QQ Host handles processing without a separate mixer. OFFLOAD is for mixing workflows that benefit from reducing real-time CPU pressure; LIVE prioritizes less bridge waiting and does not provide OFFLOAD's CPU-relief advantage. It does not turn a plug-in's internally single-threaded algorithm into a multithreaded one.

## 下载与安装 / Download and install

只选择适合自己平台的 ZIP，并阅读随附安装说明及 1.0.3 用户手册：

Choose the ZIP for your platform and read the included installation guide and 1.0.3 user manual:

- [Windows x64 VST3](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.0.3/QQ.Host.1.0.3.Windows.x64.VST3.zip)
- [macOS Apple Silicon VST3](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.0.3/QQ.Host.1.0.3.macOS.Apple.Silicon.VST3.zip)
- [macOS Intel x86_64 VST3](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.0.3/QQ.Host.1.0.3.macOS.Intel.x86_64.VST3.zip)
- [macOS Universal 2 AU](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.0.3/QQ.Host.1.0.3.macOS.Universal.2.AU.zip)
- [中文安装说明 / Chinese installation guide](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.0.3/QQ.Host.1.0.3.Installation.Guide.Chinese.txt)
- [English installation guide](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.0.3/QQ.Host.1.0.3.Installation.Guide.English.txt)
- [中文用户手册 / Chinese user manual](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.0.3/QQ.Host.1.0.3.User.Manual.Chinese.pdf)
- [English user manual](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.0.3/QQ.Host.1.0.3.User.Manual.English.Edition.pdf)

升级前完全关闭 DAW 和插件扫描器，用同版本的 Bridge 与 QQ Host 后台应用成套替换旧版。Windows 下两者必须放在同一个 `QQ Host` 安装文件夹；macOS 请按安装说明分别放置插件与应用。不要保留会被重复扫描的旧版副本。

Fully quit the DAW and plug-in scanners before upgrading, and replace the Bridge and background QQ Host application together with matching versions. On Windows they must share the same `QQ Host` installation folder; on macOS follow the separate plug-in and application locations in the guide. Do not leave old copies where the DAW can scan them again.

> **FL Studio 必需设置：** Wrapper > Troubleshooting 中启用 **Use fixed size buffers**；在 More 中同时启用 **Process maximum size buffers** 和 **Use maximum buffer size from host**。否则 Bridge 可能没有音频或无法正常工作。
>
> **Required in FL Studio:** In Wrapper > Troubleshooting, enable **Use fixed size buffers**. Under More, enable both **Process maximum size buffers** and **Use maximum buffer size from host**. Otherwise the Bridge may produce no audio or fail to process correctly.

## 1.0.1 → 1.0.3 版本记录 / Version history

### 1.0.1 · 历史候选版 / Historical candidate

- 改善单插件预置保存：先完整写入与校验，再发布文件；修正原生 VST2 FXP 的长度字段。
- 在 SAVE 附近加入明确的保存结果。当时的 Cubase 列表可见性问题尚未解决，后续继续改进。

- Improved single-plug-in preset saving: files are fully written and checked before publication, and native VST2 FXP length fields are corrected.
- Added explicit save feedback beside SAVE. The reported Cubase list-visibility issue remained unresolved at this stage, prompting the subsequent updates.

### 1.0.2 · 历史候选版 / Historical candidate

- 为 VST3 预置补齐插件名称、厂商与效果器分类，帮助 MediaBay 识别。
- VST2 的 SAVE 默认保存兼容 Cubase 的 `.vstpreset`。需要原生 FXP 时，使用“…”菜单中的 **Export Native FXP**；旧 FXP/FXB 仍可导入。
- 不自动批量改写旧预置。VST2 的 `.vstpreset` 是预置容器，不代表把插件或参数转换为 VST3。

- Added plug-in name, vendor, and effect-category information to VST3 presets for MediaBay identification.
- VST2 SAVE now defaults to a Cubase-compatible `.vstpreset`. Use **Export Native FXP** in the “…” menu when native FXP is needed; existing FXP/FXB files remain importable.
- Existing presets are not rewritten in bulk. A VST2 `.vstpreset` is a preset container, not a conversion of the plug-in or its parameters to VST3.

### 1.0.3 · 正式稳定版 / Stable

- 按预置内部的插件身份及格式筛选列表，防止同名 VST2/VST3 插件的预置混用。
- 明确显示 `[VST3]`、`[VST2 / Cubase]`、`[VST2 / FXP]`、`[VST2 / FXB]` 格式标签。手动导入也会先检查兼容性；加载失败时不再留下误导性的预置名称。
- 修复中文保存、导入与错误提示乱码，不改变现有按钮风格。
- 保持已验证的音频、侧链、延迟补偿、自动化和启动恢复行为。

- Filters preset lists by internal plug-in and format identity, keeping incompatible presets for same-named VST2/VST3 editions apart.
- Adds clear `[VST3]`, `[VST2 / Cubase]`, `[VST2 / FXP]`, and `[VST2 / FXB]` labels. Manual imports are also checked, and failed loads no longer leave a misleading preset name selected.
- Fixes garbled Chinese save, import, and error feedback without changing the existing button style.
- Preserves the validated audio, sidechain, latency compensation, automation, and startup/restore behavior.

## 预置使用提醒 / Preset guidance

- 本轮 Cubase 测试中，新保存的 VST3 与 VST2 预置均可直接读取。此前间歇性收录延迟的触发条件还未确认；如新文件没有立即出现，请对预置目录执行 **MediaBay > Quick Rescan Disk**。保存成功不等于 MediaBay 一定立即更新。
- 同名插件的 VST2 与 VST3 版不一定能够互换预置。请使用与当前插件及格式匹配的文件。
- 旧版本保存的文件不会自动补齐信息；需要时可用新版重新保存。第三方插件的状态恢复仍受其实现影响，重要预置加载后请核对参数。
- 单插件预置使用顶部 SAVE；整条机架仍使用 Bridge 的 SAVE CHAIN / LOAD CHAIN 和 `.fxchainpreset`。

- In the latest Cubase test, newly saved VST3 and VST2 presets could both be read directly. The conditions behind earlier intermittent discovery delays remain unconfirmed. If a new file does not immediately appear, run **MediaBay > Quick Rescan Disk** on the preset folder. A successful save does not guarantee an immediate MediaBay update.
- Same-named VST2 and VST3 editions do not necessarily share compatible presets. Use a file matching the current plug-in and format.
- Files saved by older versions are not automatically enriched with new information; save them again with the current version when needed. Third-party state restoration also depends on the plug-in's implementation, so verify parameters after loading important presets.
- Use the hosted editor's SAVE for one plug-in. Whole racks still use the Bridge's SAVE CHAIN / LOAD CHAIN with `.fxchainpreset`.

## 兼容性与安全 / Compatibility and security

- 仅支持已获授权的原生 64-bit VST2/VST3 效果器；不支持 32-bit VST2 或乐器。macOS 插件与后台应用架构必须匹配所选包。
- 侧链和延迟对齐依赖第三方插件正确上报延迟与输入布局。性能收益取决于插件、Buffer Size、DAW 路由与电脑配置。
- macOS 包未经 Apple Developer ID 公证；如系统拦截，请按安装说明仅处理来自可信发布包的实际安装文件，不要全局关闭 Gatekeeper。

- Supports licensed native 64-bit VST2/VST3 audio effects only; 32-bit VST2 and instruments are unsupported. On macOS, use matching plug-in and background-app architectures from the selected package.
- Sidechain and latency alignment depend on accurate third-party latency and input-layout reporting. Performance benefits depend on plug-ins, buffer size, DAW routing, and the computer.
- macOS packages are not Apple Developer ID notarized. If blocked, follow the installation guide only for the actual installed files from this trusted release; do not disable Gatekeeper globally.

QQ Host 为闭源软件。本公开仓库只提供用户下载和说明；GitHub 自动生成的 **Source code (zip/tar.gz)** 是本下载页的资料快照，不是可安装的插件或项目源码。

QQ Host is closed-source software. This public repository provides user downloads and documentation only. GitHub's automatic **Source code (zip/tar.gz)** files are snapshots of this download page, not installable plug-ins or the project's source code.
