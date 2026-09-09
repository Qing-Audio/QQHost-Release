# QQ Host 1.0.4 / 2026-09-09

## 中文

QQ Host｜性能桥接机架，一个可以将 DAW 内的单核处理分散成多核处理的效果器。保留轨道 Insert 工作流，由后台 Host 承载第三方效果器；不会自动并行化单个插件内部的算法。

### 1.0.4 更新

- 修复 Bridge 底部 **PDC / MISS / FB / SKIP** 一行的悬停提示。鼠标停留约 **0.7 秒**，即可查看后台最近/最大处理耗时、DAW 音频块时长及计数；不需要先出现 MISS。
- 修复提示文字频繁刷新导致提示一直不出现的问题。悬停期间显示数据快照，移开鼠标后再次悬停刷新；底部计数继续实时更新。
- 提示随 Bridge 窗口及 DAW 缩放显示，没有新增独立窗口或点击面板。

### 行为与已知边界

本版只改善诊断信息的显示，**不改变音频处理、线程调度、OFFLOAD/LIVE、PDC、侧链、预置、自动化或启动等待，不宣称已修复音频 MISS**。插件摆放与卡顿是否有关仍需对照测试。

**FL Studio 必须设置：** Wrapper > Troubleshooting > Use fixed size buffers，并在 More 中勾选 **Process maximum size buffers** 和 **Use maximum buffer size from host**，然后重新加载 Bridge。否则可能无法正常处理音频。

Cubase 中保存成功不代表 MediaBay 已立即收录；必要时对预置目录执行 **Quick Rescan Disk**。第三方插件的延迟与输入布局报告会影响侧链/PDC 对齐，不能保证所有插件参数都能完全兼容。macOS 包未经 Apple Developer ID 公证，安全处理见安装说明。

### 安装与附件

Windows 10/11 x64；macOS 11+。先关闭 DAW、插件扫描器及 QQ Host 后台，再安装同一版本的 Bridge 和后台 Host；不要保留扫描目录中的重复旧副本。1.0.3 旧 Release 保留，便于回退。

附件为本次桌面 Plan E 包中的四类成品和两份 1.0.4 安装说明，并随附**原版 1.0.3 中英文用户手册**。手册内容仍适用，版本标识保持真实；新增悬停用法在 1.0.4 安装说明中。QQ Host 是闭源软件，本页面不发布源码或内部资料。

## English

QQ Host is a performance bridge rack that moves CPU-intensive processing out of the DAW's real-time thread while preserving the Insert workflow. It does not parallelize an individual plug-in's internal algorithm.

### Changes in 1.0.4

- Restores hover diagnostics on the Bridge footer's **PDC / MISS / FB / SKIP** row. Hover for about **0.7 seconds** to see last/maximum background processing time, DAW block duration and counters, including when MISS is zero.
- Prevents frequent text updates from continually suppressing the tooltip. A snapshot is held while hovered; move away and hover again to refresh. Footer counters remain live.
- The tooltip follows the Bridge editor and DAW scaling. No separate native window or click panel is added.

### Behavior and known limitations

This release improves diagnostic display only. **Audio processing, thread scheduling, OFFLOAD/LIVE, PDC, sidechain, presets, automation and startup waits are unchanged. It does not claim to fix audio deadline misses.** Any relationship between plug-in placement and glitches still requires controlled testing.

**Required FL Studio settings:** Wrapper > Troubleshooting > Use fixed size buffers; under More, enable **Process maximum size buffers** and **Use maximum buffer size from host**, then reload the Bridge. Processing may fail without these settings.

A successful Cubase preset save does not guarantee immediate MediaBay discovery; use **Quick Rescan Disk** on the preset folder if needed. Third-party latency/input-layout reporting affects sidechain/PDC alignment, and universal plug-in parameter compatibility is not guaranteed. macOS packages are not Apple Developer ID notarized; consult the installation guide for safe handling.

### Installation and attachments

Windows 10/11 x64; macOS 11+. Fully quit DAWs, scanners and background QQ Host before upgrading. Install matching Bridge and Host versions and avoid duplicate old copies in scan paths. The previous 1.0.3 Release remains available for rollback.

Attachments come from the completed desktop Plan E package: four platform ZIPs, two 1.0.4 installation guides, and the **original 1.0.3 English/Chinese manuals**. Those manuals remain applicable and retain their true version labels; the 1.0.4 guides explain the new tooltip. QQ Host is closed-source; no source code or internal material is published here.

## Assets / 实际附件

- QQ.Host.1.0.4.Windows.x64.VST3.zip
- QQ.Host.1.0.4.macOS.Apple.Silicon.VST3.zip
- QQ.Host.1.0.4.macOS.Intel.x86_64.VST3.zip
- QQ.Host.1.0.4.macOS.Universal.2.AU.zip
- QQ.Host.1.0.4.Installation.Guide.Chinese.txt
- QQ.Host.1.0.4.Installation.Guide.English.txt
- QQ.Host.1.0.3.User.Manual.Chinese.pdf
- QQ.Host.1.0.3.User.Manual.English.Edition.pdf

Since the previous public 1.0.3 Release, this interval contains 1.0.4 and its same-day 1.0.3 local tooltip follow-up, now included in 1.0.4; no intermediate numbered version is omitted. 上次公开版为 1.0.3，本区间为其当日悬停提示本地修订及正式编号 1.0.4；未遗漏中间版本。
