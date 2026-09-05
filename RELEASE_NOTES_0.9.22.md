# QQ Host 0.9.22

**发布日期 / Release date:** 2026-09-05
**状态 / Status:** Stable
**授权 / Licensing:** 闭源专有软件 / Closed-source proprietary software

QQ Host 是专门针对 DAW 混音插件链设计的性能桥接机架。它保留轨道 Insert + Bridge 的使用方式，把第三方效果器交给后台 Host 处理，帮助 CPU 占用较多的处理链更充分地利用多核 CPU。

QQ Host is a performance bridge rack designed specifically for DAW mixing plug-in chains. It preserves the familiar track Insert + Bridge workflow while moving hosted effects to the background Host so CPU-heavy chains can make better use of a multi-core CPU.

## 本次版本重点 / Highlights

- 修复 DAW 原生 Bypass 时的 PDC 误报，让旁路音频继续经过与 Bridge 报告延迟一致的 Dry 路径。
- 加固 Duplicate、Move、Add、恢复事务与故障隔离，减少插件消失、错误 Power Off 或 Host 恢复异常。
- 降低隐藏插件编辑器的重复自动化扫描和尺寸轮询，减少长时间工程的后台 UI 与锁竞争。
- 改进 Cubase FX Chain 保存与加载；支持包含 VST2/VST3 的混合 Chain，并为 MediaBay 首次发现问题提供明确提示。
- 加入 VST2 原生 `.fxp/.fxb` 预设与侧链路由，包括固定 4-in/2-out VST2 在单声道 DAW 轨道上的侧链输入。
- 0.9.22 只在完整且播放格式稳定的 Bridge Cohort 上启用快速恢复；条件不足时自动保留较保守的启动路径。

- Fixes DAW-native Bypass PDC mismatch by keeping bypassed audio on the latency-matched Dry path.
- Hardens Duplicate, Move, Add, restore transactions, and fault isolation to reduce disappearing plug-ins, unintended Power Off, and Host recovery failures.
- Reduces duplicate automation scanning and aggressive size polling in hidden hosted editors, lowering long-session background UI and lock contention.
- Improves Cubase FX Chain save/load, including mixed VST2/VST3 chains, with clear guidance for first-save MediaBay discovery.
- Adds native VST2 `.fxp/.fxb` presets and VST2 sidechain routing, including fixed 4-in/2-out effects on mono DAW tracks.
- Enables the fast restore path only for complete Bridges with a stable playback format; otherwise 0.9.22 automatically retains the conservative startup path.

## 0.9.3–0.9.22 完整版本记录 / Complete version history

从上一个公开版本 0.9.2 到本次 0.9.22 的真实版本全部列在下面。遗漏版本：无。

Every real version between the previous public release 0.9.2 and this 0.9.22 release is listed below. Omitted versions: none.

| Version | Status | 中文 | English |
|---|---|---|---|
| 0.9.3 | Candidate | 修复 DAW 原生 Bypass 时的 PDC 误报：旁路音频继续经过与 Bridge 报告延迟一致的 Dry 延迟线。 | Fixed DAW-native Bypass PDC mismatch by keeping bypassed audio on the latency-matched Dry path. |
| 0.9.4 | Candidate | 为 Duplicate、Move 与故障隔离加入持久 Slot UUID 和恢复快照事务，避免插件消失或错误关闭链首插件。 | Added persistent Slot UUIDs and transactional recovery snapshots for Duplicate, Move and fault isolation. |
| 0.9.5 | Invalid test | 一次未完成的 Idle CPU / 结构恢复自动修改试验；关键路径没有完整修改，从未成为可用基线。 | Incomplete automated Idle CPU/structural-recovery experiment; required paths were not fully changed, so it was never a valid baseline. |
| 0.9.6 | Candidate | 严格按 UUID 隔离故障，扩大新建 Rack 的首次调用保护，并加固结构变更后的恢复快照提交。 | Enforced UUID-only fault isolation, rack-wide first-use grace and hardened structural recovery snapshot commits. |
| 0.9.7 | Diagnostic Candidate | 增加运行时故障、watchdog、调用阶段和恢复原因遥测，不改变既有恢复决策。 | Added runtime-fault, watchdog, call-stage and recovery telemetry without changing recovery policy. |
| 0.9.8 | Stable | 将 QQ Host 自有对齐缓冲扩容与第三方插件 `prepareToPlay` 生命周期分离，消除高延迟插件加载后的重复 Prepare 与卡顿。 | Split QQ Host alignment-buffer growth from hosted plug-in preparation, eliminating duplicate prepares and post-load stalls. |
| 0.9.9 | Candidate | 移除隐藏插件编辑器持续进行的重复 Automation 扫描和高频尺寸轮询，降低长时间工程的后台 UI/锁竞争。 | Removed duplicate automation scans and aggressive hidden-editor polling that accumulated during long sessions. |
| 0.9.10 | Candidate | 首次保存 Cubase FX Chain 时先写无监视扩展名的完整临时文件，再原子发布到最终路径。 | Reworked first FX Chain publication to write a complete non-watched temporary file before atomic final-path publication. |
| 0.9.11 | Candidate | 将保存事务交给 Processor 生命周期管理，加入事务 ID、完整 busy 状态、原子发布校验和 Shell 通知。 | Moved save ownership to the processor and added transaction IDs, complete busy state, atomic verification and Shell notification. |
| 0.9.12 | Candidate | 修复含 VST2 的混合 VST2/VST3 Chain 在状态捕获阶段中断，允许保存与加载混合 FX Chain。 | Fixed VST2 state-capture aborts so mixed VST2/VST3 FX Chains can be saved and loaded. |
| 0.9.13 | Candidate | 写出 Cubase 可识别的严格 FXB v2 头，并为同类 VST2 实例生成唯一 ID；加载时只规范化私有副本。 | Added strict Cubase FXB v2 headers and unique repeated-instance IDs while normalizing only private load copies. |
| 0.9.14 | Candidate, withdrawn | 尝试用延迟的 MediaBay 发现刷新解决首次新文件不显示；实测无效，后续移除。 | Tried delayed MediaBay discovery refreshes for first-save visibility; real testing showed no benefit and the retries were removed. |
| 0.9.15 | Candidate | 对 MediaBay 外部索引问题改为明确提示；同时加入 VST2 Sidechain Bus 路由和原生 `.fxp/.fxb` 预设支持。 | Replaced ineffective MediaBay retries with guidance and added VST2 sidechain-bus routing plus native `.fxp/.fxb` support. |
| 0.9.16 | Candidate | 把缺失的 Host 路由缓冲作为独立 Prepare 条件，修复零延迟首 Slot 在音频开始前未建立 Main/Sidechain 缓冲的问题。 | Treated missing host routing buffers as an independent prepare condition for zero-latency first-slot startup. |
| 0.9.17 | Candidate | 针对 VST2 扁平输入 ABI，将 Main 固定送往物理 1/2，Sidechain 送往物理 3/4；VST3 Aux 不变。 | Routed VST2 flat physical inputs directly: Main to pins 1/2 and Sidechain to pins 3/4, leaving VST3 Aux unchanged. |
| 0.9.18 | Diagnostic Candidate | 增加实时 Sidechain 源峰值、VST2 物理 Pin 峰值、路由布局和 routed-block 计数，用于定位仅在真实 DAW 工程出现的问题。 | Added realtime source/pin peaks, route layout and routed-block telemetry to isolate the DAW-only VST2 sidechain failure. |
| 0.9.19 | Stable | 修复单声道 DAW 轨道上的固定 4-in/2-out VST2：复制 Main 到 1/2，并把 Sidechain 送入 3/4。 | Fixed fixed 4-in/2-out VST2 effects on mono DAW tracks by mirroring Main to 1/2 and routing Sidechain to 3/4. |
| 0.9.20 | Diagnostic Candidate | 只记录 Bridge 到达、拓扑稳定、恢复事务、首个音频块与 `HOST READY` 时序，不修改等待或恢复行为。 | Added startup milestone telemetry only, without changing any wait, ordering or recovery decision. |
| 0.9.21 | Rejected Candidate | 尝试完整 Cohort 的条件式快速启动；真实 Cubase 测试中更慢并重现卡顿，因此否决。 | Tried a conditional cohort fast path; rejected after real Cubase testing lengthened startup and reproduced the stall. |
| 0.9.22 | Stable | Bridge 发布 DAW 的真实播放格式；只有完整且格式稳定的 Cohort 才快速恢复，否则自动保留保守路径。真实三 Bridge Cubase 工程已确认一次进入 `HOST READY`。 | Publishes the real DAW playback format and enables fast restore only for a complete, format-stable cohort, otherwise retaining the conservative path. Confirmed in a real three-Bridge Cubase project. |

## 行为变化 / Behaviour changes

- Cubase FX Chain 可以包含已获授权的 64-bit VST2 与 VST3 效果器。
- VST2 使用原生 `.fxp/.fxb` 预设；标准 `.vstpreset` 仍属于 VST3。
- 第一次保存新的 Cubase FX Chain 后，如果 MediaBay 暂时没有显示，请执行 **Quick Rescan Disk**；必要时再保存一次。
- 0.9.21 的快速启动试验没有进入本次稳定版；0.9.22 使用带条件检查和保守回退的实现。

- Cubase FX Chains may contain licensed native 64-bit VST2 and VST3 effects.
- VST2 uses native `.fxp/.fxb` presets; standard `.vstpreset` remains a VST3 format.
- If a newly saved Cubase FX Chain does not immediately appear in MediaBay, run **Quick Rescan Disk** and save once more if needed.
- The rejected 0.9.21 startup experiment is not part of this Stable release; 0.9.22 uses guarded eligibility checks with a conservative fallback.

## 兼容性 / Compatibility

- Windows 10/11 x64：VST3 Bridge + 后台 QQ Host.exe。
- macOS 11 或更高版本：Apple Silicon VST3、Intel x86_64 VST3、Universal 2 AU。
- 可托管插件：已获授权的原生 64-bit VST2/VST3 音频效果器；不支持乐器和 32-bit VST2。
- macOS 文件未经 Apple Developer ID 公证。
- 侧链与 PDC 对齐依赖第三方插件正确报告延迟和输入布局。

- Windows 10/11 x64: VST3 Bridge + background QQ Host.exe.
- macOS 11 or later: Apple Silicon VST3, Intel x86_64 VST3, Universal 2 AU.
- Hosted plug-ins: licensed native 64-bit VST2/VST3 audio effects; instruments and 32-bit VST2 are unsupported.
- macOS files are not Apple Developer ID notarized.
- Sidechain and PDC alignment depend on third-party plug-ins reporting latency and input layouts correctly.

## 安装要求与升级 / Installation and upgrade

1. 完全退出 DAW 与插件扫描器。
2. 删除所有旧版 QQ Host Bridge 与后台 QQ Host，避免 Bridge/Agent 混用版本。
3. 只下载并安装与你的平台和插件格式匹配的 ZIP；详细路径见对应的中英文安装说明。
4. 在 DAW 中重新扫描 QQ Host Bridge。
5. FL Studio 用户必须在 Wrapper 的 Troubleshooting 页面启用 **Process maximum size buffers** 和 **Use maximum buffer size from host**。

1. Fully quit the DAW and plug-in scanners.
2. Remove every older QQ Host Bridge and background QQ Host copy so Bridge and Agent versions cannot be mixed.
3. Download only the ZIP matching your platform and plug-in format; see the Chinese or English installation guide for exact paths.
4. Rescan QQ Host Bridge in the DAW.
5. FL Studio users must enable **Process maximum size buffers** and **Use maximum buffer size from host** in the Wrapper Troubleshooting page.

## 已知问题 / Known issues

- QQ Host 仍是实验性外部宿主；性能收益取决于 DAW、插件、Buffer Size、Bridge 数量、IPC 开销和电脑配置。
- 第三方插件误报延迟或动态改变延迟但不通知宿主时，无法保证完全对齐。
- Cubase MediaBay 的首次文件发现由 Cubase 自己的外部索引控制，必要时需要 Quick Rescan Disk 或再次保存。
- macOS 未公证文件可能需要可信来源确认和 quarantine 处理；请阅读安装说明。

- QQ Host remains an experimental external host; performance gains depend on the DAW, plug-ins, buffer size, Bridge count, IPC overhead, and computer.
- Complete alignment cannot be guaranteed when third-party plug-ins misreport latency or change it without notifying the host.
- First-time Cubase MediaBay discovery is controlled by Cubase's external index and may require Quick Rescan Disk or another save.
- Unnotarized macOS files may require trusted-source confirmation and quarantine handling; read the installation guide.

## Release 资产 / Release assets

- `QQ Host 0.9.22 Windows x64 VST3.zip`
- `QQ Host 0.9.22 macOS Apple Silicon VST3.zip`
- `QQ Host 0.9.22 macOS Intel x86_64 VST3.zip`
- `QQ Host 0.9.22 macOS Universal 2 AU.zip`
- `QQ Host 0.9.22 安装说明（中文）.txt`
- `QQ Host 0.9.22 Installation Guide (English).txt`
- `QQ Host 0.9.15 用户手册 中文版.pdf`
- `QQ Host 0.9.15 User Manual English Edition.pdf`
- `SHA256SUMS.txt`

0.9.15 用户手册继续适用于 0.9.22，因为 0.9.16–0.9.22 没有新增用户操作步骤。每个平台 ZIP 和文档的 SHA-256 请见 `SHA256SUMS.txt`。

The 0.9.15 user manuals remain applicable to 0.9.22 because versions 0.9.16–0.9.22 add no new user-facing operation. See `SHA256SUMS.txt` for the SHA-256 of every platform ZIP and document.
