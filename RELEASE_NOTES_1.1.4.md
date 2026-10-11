# QQ Host 1.1.4 Stable — 2026-10-12

## 中文

用户明确将当前版本设为 Stable。上一稳定回滚版本为 1.1.3。

- 修复打开或切换工程时，首次后台连接失败后无法继续恢复插件的问题。连接失败会重试，并保留等待恢复的工程状态。
- Refresh 可重新尝试当前 Host 的连接，即使旧恢复请求仍在等待，也不会被同一队列挡住；重复点击会合并，避免恢复完成后又重建一次。
- Refresh 等待时间较长时会说明正在等待连接、后台处理或插件恢复，并指引用户选择已有的“Restart Agent (All Hosts)”操作。局部 Refresh 不会自动重启其他 Host。
- QQ Host 自身控件的悬停说明改为中文，覆盖推子、声像、按钮、插件浏览器、插件窗口顶部工具栏，以及主题、旁通、Refresh、延迟诊断等动态说明。
- 中文显式使用 UTF-8 解码，Windows 与 macOS 共用 Unicode 文本路径。保留产品名、格式名、对应英文菜单名和未识别诊断原文；第三方插件自身界面语言不变。

兼容性与升级：Windows x64 VST3；macOS 12+ Apple Silicon VST3、Intel x86_64 VST3 和 Universal 2 AU。Bridge 与 QQ Host 后台必须成对更新。升级前完全退出所有 DAW 和 QQ Host。原生预置仍须匹配插件格式；第三方插件授权与安装要求不变。

验证范围：复用已完成的 Windows Release 编译、编码/安装哈希核验及隔离恢复回归。回归覆盖连接失败重试、重复 Refresh、缓慢恢复，以及其他 Host 的音频连续性。三类 macOS 发布构建及架构、版本、签名、编码检查均通过；不把构建或静态验证描述为真实 DAW 图形界面验收。无法保证所有第三方插件无响应情况均可由局部 Refresh 修复。

本次只新增一个真实版本 1.1.4；上一次公开版是 1.1.3，期间没有遗漏的其他版本。随包继续提供保留真实 1.1.0 标识的中英文基础手册；1.1.4 的新行为以本说明和安装说明为准。

## English

The owner explicitly designated this build Stable. The previous Stable rollback is 1.1.3.

- Repairs recovery after an initial background connection failure when opening or switching projects. Failed connections are retried while pending project state is preserved.
- Refresh can retry the current Host connection even when an earlier restore request is waiting. Repeated clicks are coalesced to avoid another rebuild after recovery completes.
- A prolonged Refresh explains whether it is waiting for the connection, background processing, or plug-in restoration, and points to the existing “Restart Agent (All Hosts)” command. Local Refresh does not automatically restart other Hosts.
- QQ Host's own hover descriptions are now Chinese, including the fader, pan, buttons, plug-in browser, hosted-window toolbar, and dynamic theme, bypass, Refresh and timing explanations.
- Chinese text is explicitly decoded as UTF-8 on the shared Windows/macOS Unicode path. Product/format names, corresponding English menu names and unrecognized diagnostics are preserved. Third-party plug-in interfaces retain their own language.

Compatibility and upgrade: Windows x64 VST3; macOS 12+ Apple Silicon VST3, Intel x86_64 VST3 and Universal 2 AU. Update the Bridge and QQ Host background application together, with all DAWs and QQ Host closed. Native presets still require the matching plug-in format. Third-party installation and licensing requirements are unchanged.

Validation scope: reuse the completed Windows Release build, encoding/installed-file hash checks and isolated recovery regressions. These cover failed-connection retries, repeated Refresh, slow restores and uninterrupted audio in neighbouring Hosts. All three macOS release builds and architecture, version, signature and encoding checks passed; build/static checks are not real-DAW GUI acceptance. Local Refresh cannot be guaranteed to repair every unresponsive third-party plug-in.

1.1.4 is the only new version since public 1.1.3; no intermediate version is omitted. The included Chinese/English reference manuals retain their actual 1.1.0 labels; these notes and the installation guides describe the new 1.1.4 behaviour.

## 安装与附件 / Installation and assets

退出所有 DAW 和 QQ Host，再成对升级 Bridge 与后台程序。Mac 成品使用 ad-hoc 签名，未公证。具体安装与安全步骤见双语安装说明。
Quit all DAWs and QQ Host, then update the Bridge and background application together. Mac bundles are ad-hoc signed, not notarized. Follow the bilingual guides for installation and security steps.

- [Windows x64 VST3](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.4/QQ.Host.1.1.4.Windows.x64.VST3.zip)
- [macOS Apple Silicon VST3](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.4/QQ.Host.1.1.4.macOS.Apple.Silicon.VST3.zip)
- [macOS Intel x86_64 VST3](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.4/QQ.Host.1.1.4.macOS.Intel.x86_64.VST3.zip)
- [macOS Universal 2 AU](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.4/QQ.Host.1.1.4.macOS.Universal.2.AU.zip)
- [中文安装说明 / Chinese installation guide](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.4/QQ.Host.1.1.4.Installation.Guide.Chinese.txt)
- [English installation guide](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.4/QQ.Host.1.1.4.Installation.Guide.English.txt)
- [中文基础手册 / Chinese reference manual (1.1.0)](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.4/QQ.Host.1.1.0.User.Manual.Chinese.pdf)
- [English reference manual (1.1.0)](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.4/QQ.Host.1.1.0.User.Manual.English.Edition.pdf)

本次八个附件只含四类平台成品、双语安装说明和双语基础手册，源码保持私有。
These eight assets contain four platform packages, bilingual installation guides and bilingual reference manuals. Source remains private.
