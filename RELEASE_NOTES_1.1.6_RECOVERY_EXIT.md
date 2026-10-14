# QQ Host 1.1.6 — 2026-10-14 恢复与退出修订 / Recovery and Exit Revision

状态 / Status: Stable. 发布标签 / Release tag: v1.1.6-recovery-exit-20261014.
产品仍显示 1.1.6，协议仍为 137。本次使用日期修订标签，保留原 v1.1.6 发布。
The product still reports 1.1.6 / protocol 137. This dated revision keeps the original v1.1.6 release intact.

## 逐修订记录 / Revision history

### 1.1.6 中文恢复提示候选 / Chinese recovery feedback candidate — 2026-10-14
中文：将启动、连接、刷新恢复状态以及“重启全部 QQ Host”菜单与确认提示改为中文，使用显式 UTF-8 解码。只调整提示，恢复逻辑和音频处理未改。Windows 编译与 9 项编译后中文检查通过；候选阶段未完成 Mac 原生构建。
English: Translates startup, connection and Refresh recovery feedback, plus the restart-all menu and confirmation, into Chinese with explicit UTF-8 decoding. Recovery logic and audio processing are unchanged. Windows compilation and nine compiled-text checks passed; native Mac builds were not complete at this candidate checkpoint.

### 1.1.6 Windows 后台退出保护候选 / Windows Agent exit guard candidate — 2026-10-14
中文：加强最后一个宿主退出后的后台退出保护，并在正常清理结束后直接结束 Windows 后台进程，避免再次进入可能卡住的第三方 DLL 退出清理。仍保留存活宿主保护；关闭插件窗口不会结束仍在处理音频的后台。3 项隔离退出场景与 54 项格式/生命周期检查通过。macOS 退出行为不变，不能据此宣称修复了第三方插件自身的卡死。
English: Hardens Windows Agent exit after the last host closes and ends the process directly after normal cleanup, avoiding another potentially blocked third-party DLL detach. Live hosts remain protected; closing an editor does not stop active audio processing. Three isolated exit scenarios and 54 format/lifetime checks passed. macOS exit behavior is unchanged; this does not establish a fix for a third-party plug-in's own hang.

### 1.1.6 Stable 恢复与退出修订 / Stable Recovery and Exit Revision — 2026-10-14
中文：合并上述两项修订并设为 Stable；中英文说明书同步中文恢复提示、当前 Host 刷新与全部 Host 重启的区别，以及 Windows 后台退出保护。扫描管理、格式筛选、Power 和音频处理保留原行为。新增宿主工程的界面/声音验收尚未报告。
English: Promotes both changes to Stable. The revised Chinese and English manuals explain current recovery labels, local Refresh versus restarting all Hosts, and Windows exit protection. Scan management, format filtering, Power and audio processing retain their behavior. Additional in-DAW GUI/audio acceptance has not been reported.

## 使用与升级 / Use and upgrade

中文：卡在启动或恢复时，先使用主界面 REFRESH；仍无法恢复时，停止播放，再打开右上角“…”菜单，选择“重启全部 QQ Host”并确认“重启全部”。这会重启共用后台，其他已连接 Host（包括其他 DAW）也会暂时断开并恢复。浏览器内的 Refresh 用于增量扫描。
English: If startup or recovery is stuck, try the main REFRESH first. If recovery still fails, stop playback and use the top-right “…” menu: “重启全部 QQ Host” (Restart all QQ Hosts), then confirm “重启全部” (Restart all). The shared background app restarts, so other connected Hosts, including those in other DAWs, also disconnect temporarily and recover. Browser Refresh performs an incremental scan.

中文：Windows 10/11 x64 VST3；macOS 12+ Apple Silicon VST3、Intel x86_64 VST3 和 Universal 2 AU。升级前完全退出 DAW、扫描器与 QQ Host，成对替换 Bridge 和后台程序，保留旧包以便回退。Mac 使用 ad-hoc 签名，未公证。仅支持原生 64-bit 效果器。产品闭源，源码保持私有。
English: Windows 10/11 x64 VST3; macOS 12+ Apple Silicon VST3, Intel x86_64 VST3 and Universal 2 AU. Fully quit DAWs, scanners and QQ Host, then replace the Bridge and background app together. Keep the previous package for rollback. Mac bundles use ad-hoc signatures and are not notarized. Native 64-bit effects only. The product is closed-source; source remains private.

中文：构建及隔离测试不能代替每个 DAW/第三方插件的实际验收，也不能保证第三方插件不会卡死。
English: Builds and isolated tests do not replace acceptance in every DAW or third-party plug-in, and do not guarantee that third-party plug-ins cannot hang.

## 验证与附件 / Validation and assets

Windows 成品复用已核验构建，Mac 三套成品通过编译、版本、架构、ad-hoc 签名和中文编码检查。中英文手册修订页已检查排版，中文字体已嵌入。每个 DAW/第三方插件的界面和声音实测仍需分别验收。
Windows reuses the verified build. All three Mac packages pass compilation, version, architecture, ad-hoc signature and compiled Chinese-text checks. Revised manual pages were visually checked and Chinese fonts embedded. GUI/audio behavior still requires individual DAW and third-party plug-in acceptance.

本次发布含以下 8 个附件，不含源码或内部资料。旧 Release 保留。
This release contains these eight assets, with no source or internal material. The earlier release is preserved.

- [Windows x64 VST3](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.6-recovery-exit-20261014/QQ.Host.1.1.6.20261014.Windows.x64.VST3.zip)
- [macOS Apple Silicon VST3](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.6-recovery-exit-20261014/QQ.Host.1.1.6.20261014.macOS.Apple.Silicon.VST3.zip)
- [macOS Intel x86_64 VST3](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.6-recovery-exit-20261014/QQ.Host.1.1.6.20261014.macOS.Intel.x86_64.VST3.zip)
- [macOS Universal 2 AU](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.6-recovery-exit-20261014/QQ.Host.1.1.6.20261014.macOS.Universal.2.AU.zip)
- [中文安装说明 / Chinese installation guide](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.6-recovery-exit-20261014/QQ.Host.1.1.6.20261014.Installation.Guide.Chinese.txt)
- [English installation guide](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.6-recovery-exit-20261014/QQ.Host.1.1.6.20261014.Installation.Guide.English.txt)
- [中文用户手册 / Chinese user manual](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.6-recovery-exit-20261014/QQ.Host.1.1.6.20261014.User.Manual.Chinese.pdf)
- [English user manual](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.6-recovery-exit-20261014/QQ.Host.1.1.6.20261014.User.Manual.English.Edition.pdf)
