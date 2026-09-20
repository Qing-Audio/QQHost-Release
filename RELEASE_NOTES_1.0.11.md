# QQ Host 1.0.11

## 中文

QQ Host｜性能桥接机架，一个可以将 DAW 内的单核处理分散成多核处理的效果器。

本次为 1.0.10 之后的维护更新，没有新增音频处理功能。

- 修正旧后台进程记录被误认为仍在运行，导致 Host 无法正常启动的问题，包括已报告的 Plugin Doctor 情形。
- 后台不存在时，不再一直误显示 HOST RESTORING；启动、恢复和就绪状态分别显示。
- 手动重启后台时增加进程身份核验，避免仅凭进程编号判断。
- 保留手动刷新策略：初次加载与正常工程恢复仍执行；不会因为其他机架变化而恢复自动刷新。

### 安装与兼容性

完全退出 DAW、Plugin Doctor 与扫描器后，成套更新 QQ Host Bridge 和后台 QQ Host。两者均应为 1.0.11，Protocol 125。请阅读附件中的安装说明，勿保留重复旧版。

提供 Windows x64 VST3、macOS Apple Silicon VST3、macOS Intel VST3、macOS Universal 2 AU；macOS 最低构建目标为 11.0。VST3 架构必须匹配宿主运行架构，Rosetta 宿主使用 Intel 包。macOS 包未经过 Apple Developer ID 公证。

FL Studio 仍需在 Wrapper > Troubleshooting 启用 Use fixed size buffers，并在 More 启用 Process maximum size buffers 与 Use maximum buffer size from host，然后重新加载 Bridge。

### 已知限制

第三方插件完全卡住共享后台时，局部 REFRESH 仍可能无法完成；必要时先停止播放并保存工程，再明确选择 Restart Agent (All Hosts)。该操作影响所有 Bridge。

Cubase 暂未列出新预置时，可尝试用同一文件名覆盖保存两次；仍未出现，再在 MediaBay 对对应目录执行 Quick Rescan Disk。

双语 PDF 沿用 1.0.6 的真实版本标识。此版不包含 ChainScope 安装包。软件闭源，本下载仓库不提供源码。自动化测试及平台构建核验不代表所有 DAW 和工程均经过实测。

## English

QQ Host is a performance bridge rack that moves CPU-intensive processing away from the DAW's real-time thread, allowing work to use more CPU cores.

This is a maintenance update after 1.0.10, with no new audio-processing features.

- Fixes a stale background-process record being mistaken for a running Agent, preventing normal startup, including the reported Plugin Doctor case.
- An absent Agent no longer remains mislabeled HOST RESTORING. Startup, restoration and readiness have distinct status displays.
- Adds process-identity verification to explicit background restarts rather than trusting a process ID alone.
- Preserves manual recovery: initial loading and normal project restoration still run; changes in other racks do not re-enable automatic refresh.

### Installation and compatibility

Fully quit DAWs, Plugin Doctor and scanners, then update QQ Host Bridge and the background QQ Host application together. Both must show 1.0.11, Protocol 125. Read the included installation guide and avoid duplicate old copies.

Packages: Windows x64 VST3, macOS Apple Silicon VST3, macOS Intel VST3 and macOS Universal 2 AU. The macOS deployment target is 11.0. Match VST3 architecture to the running host; Rosetta hosts need the Intel package. macOS packages are not Apple Developer ID notarized.

FL Studio still requires Use fixed size buffers in Wrapper > Troubleshooting, plus Process maximum size buffers and Use maximum buffer size from host under More; reload the Bridge afterward.

### Known limits

A third-party plug-in that completely hangs the shared Agent can prevent local REFRESH from completing. If necessary, stop playback and save the project before explicitly selecting Restart Agent (All Hosts), which affects every Bridge.

If Cubase does not list a newly saved preset, try saving twice with the same filename and overwrite confirmation. If still absent, use Quick Rescan Disk on its folder in MediaBay.

The bilingual PDFs retain their genuine 1.0.6 labels. No ChainScope installer is included. QQ Host is closed-source; this download repository does not provide its source. Automated tests and platform build checks are not certification of every DAW and session.

## Assets / 附件

- QQ.Host.1.0.11.Windows.x64.VST3.zip
- QQ.Host.1.0.11.macOS.Apple.Silicon.VST3.zip
- QQ.Host.1.0.11.macOS.Intel.x86_64.VST3.zip
- QQ.Host.1.0.11.macOS.Universal.2.AU.zip
- QQ.Host.1.0.11.Installation.Guide.Chinese.txt
- QQ.Host.1.0.11.Installation.Guide.English.txt
- QQ.Host.1.0.6.User.Manual.Chinese.pdf
- QQ.Host.1.0.6.User.Manual.English.Edition.pdf
