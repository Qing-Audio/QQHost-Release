# QQ Host 1.1.3 Stable — 2026-10-10

## 1.1.3 — 提示文字编码 / Preset feedback encoding

中文：修复原生 VST3 预置加载到 VST2 实例时，格式不匹配提示中的中文乱码；同一工具栏的 AU 保存成功提示也显式按 UTF-8 解码。Windows 提示气泡与 macOS 提示气泡/原生警告共用正确的 Unicode 字符串。本次不改变预置内容、匹配规则、音频处理或用户操作。用户已确认 1.1.2 所处理的问题解决，并授权本次设为 Stable。当前稳定版 1.1.3，上一 Stable 回滚版 1.1.0；Bridge 与后台 Host 必须一起升级。

English: Fixes garbled Chinese in the format-mismatch feedback when loading a native VST3 preset into a VST2 instance. AU save-success feedback in the same toolbar also explicitly decodes UTF-8. Windows bubbles and macOS bubbles/native alerts share the correct Unicode strings. Preset contents, matching rules, audio processing and user operations are unchanged. The owner confirmed the issues addressed by 1.1.2 were resolved and authorized Stable promotion. Current Stable is 1.1.3; the previous Stable rollback is 1.1.0. Upgrade the Bridge and background Host together.

## 1.1.2 — Waves 身份与状态恢复 / Waves identity and state restoration

中文：测试版，2026-10-10。VST3 实例按固定 Class ID 创建，避免工厂列表顺序改变后点选与实际打开的插件不一致；Windows WaveShell 加载后核对实际身份。打开机架电源或取消 Bypass 时清除 VST3 标准内部 Bypass 残留，保留独立机架 Bypass 及厂商 Comp Off 参数。增加单插件预置身份诊断及 VST2/VST3 格式提示。可控工厂错配回归、CLA-76 Stereo 音频恢复及真实 Cubase/QQHost 预置加载通过；用户随后反馈问题解决。

English: Test build, 2026-10-10. VST3 components are created by stable Class ID so factory-list reordering cannot substitute another plug-in; Windows WaveShell loads also validate the actual identity. Power-on and un-bypass clear residual standard VST3 native bypass while preserving independent Rack Bypass and vendor Comp Off controls. Added single-preset identity diagnostics and VST2/VST3 format feedback. Controlled factory-reorder, CLA-76 Stereo audio-restoration and real Cubase/QQHost preset checks passed; the owner subsequently reported the issues resolved.

## 1.1.1 — Waves 扫描与 Cubase 电源状态 / Waves scanning and Cubase power state

中文：测试版，2026-10-09。Windows WaveShell VST3 从工厂元数据读取插件目录，避免逐个实例化所有效果器；缓存完整身份并直接加载所选效果器。Cubase FX Chain 的电源与 Bypass 独立导入/导出，不再把关闭电源合并为 Bypass。扫描成功已获用户反馈；后续身份错配和内部 Bypass 残留由 1.1.2 修复。

English: Test build, 2026-10-09. Windows WaveShell VST3 scanning reads factory metadata instead of instantiating every effect, caches complete identities and directly loads the selected effect. Cubase FX Chain power and Bypass are imported/exported independently instead of collapsing power-off into Bypass. The owner confirmed scanning worked; subsequent identity substitution and residual native bypass were addressed by 1.1.2.

## Compatibility / 兼容性

Windows x64 VST3; macOS 12+ Apple Silicon VST3, Intel x86_64 VST3 and Universal 2 AU. Use the matching plug-in format for native presets; same product names do not guarantee VST2/VST3 state interchange. No licensing or third-party plug-in files are modified. This release does not promise compatibility with every WaveShell version or third-party installation.

Windows x64 VST3；macOS 12+ Apple Silicon VST3、Intel x86_64 VST3、Universal 2 AU。原生预置应加载到匹配格式的插件，同名 VST2/VST3 不代表状态可互换。本次不修改授权机制或第三方插件文件，也不承诺覆盖所有 WaveShell 版本与安装环境。

## 安装与资产 / Installation and assets

完全退出 DAW 和后台 QQ Host，再成对替换 Bridge 与后台程序，确认 1.1.3 后重新扫描。Windows 包为 x64；Mac 只选择一套匹配宿主架构的 VST3，或使用 Universal 2 AU。Mac 为 ad-hoc 签名，未公证；详细安全与扫描步骤见中英文安装说明。

Fully quit the DAW and QQ Host before replacing the Bridge/background-app pair, then confirm 1.1.3 and rescan. Windows is x64; choose the matching Mac VST3 architecture or Universal 2 AU. Mac bundles are ad-hoc signed, not notarized. See the bilingual installation guides for security and rescan steps.

- [Windows x64 VST3](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.3/QQ.Host.1.1.3.Windows.x64.VST3.zip)
- [macOS Apple Silicon VST3](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.3/QQ.Host.1.1.3.macOS.Apple.Silicon.VST3.zip)
- [macOS Intel x86_64 VST3](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.3/QQ.Host.1.1.3.macOS.Intel.x86_64.VST3.zip)
- [macOS Universal 2 AU](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.3/QQ.Host.1.1.3.macOS.Universal.2.AU.zip)
- [中文安装说明 / Chinese installation guide](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.3/QQ.Host.1.1.3.Installation.Guide.Chinese.txt)
- [English installation guide](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.3/QQ.Host.1.1.3.Installation.Guide.English.txt)

- [中文 1.1.0 用户手册 / Chinese user manual](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.3/QQ.Host.1.1.0.User.Manual.Chinese.pdf)
- [English 1.1.0 user manual](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.3/QQ.Host.1.1.0.User.Manual.English.Edition.pdf)

本次八个附件包含四个平台安装包、两份安装说明和两份 PDF 用户手册，不含源码或内部验证资料；源码保持私有。手册沿用 1.1.0 并保留真实版本标注，已直接附在本次 Release 中。

These eight assets include four platform packages, two installation guides and two PDF user manuals, with no source or internal verification material. Source remains private. The manuals retain their original 1.1.0 labels and are directly attached to this release.
