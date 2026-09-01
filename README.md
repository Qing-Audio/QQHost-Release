# QQ Host

**中文 | English**

> QQ Host 是闭源软件。本公开仓库只提供经过确认的二进制 Release、安装信息与公开版本记录；源码仓库保持私有。
>
> QQ Host is closed-source software. This public repository provides only approved binary releases, installation information, and public version history; the source repository remains private.

## 项目简介 / Overview

**QQ Host 是专门针对 DAW 混音插件链设计的外部宿主。**

与传统外部 Host 把音频送往独立 Mixer 再返回不同，QQ Host 保留 DAW 原本的 Insert 工作流：在轨道上插入 `QQ Host Bridge`，在 Bridge 中加载第三方效果器，然后继续像普通 DAW 插件链一样工作。

QQ Host 通过 Bridge + 后台 Host 的组合，把原本可能集中在 DAW 实时音频线程或单个 CPU 核心上的多个独立插件链，卸载到 DAW 外部进程并调度到更多 CPU 核心，以降低实时线程压力、改善 CPU/ASIO 峰值并提高多核 CPU 利用效率。

**QQ Host is an external host purpose-built for DAW mixing plug-in chains.**

Unlike traditional external hosts that route audio through a separate mixer, QQ Host preserves the DAW's native Insert workflow: insert `QQ Host Bridge` on a track, load third-party effects inside the Bridge, and continue mixing as with a normal DAW plug-in chain.

The Bridge + background Host architecture offloads independent plug-in-chain workloads from the DAW process and allows them to be scheduled across more CPU cores. This can reduce real-time-thread pressure, improve CPU/ASIO peak behavior, and use multi-core CPUs more effectively.

“将单核处理转化为多核处理”指进程级、实例级和插件链级的卸载与调度，不表示把第三方插件内部的单线程 DSP 自动改写为并行算法。实际收益取决于 DAW 路由、Bridge 数量、缓冲区、插件行为、IPC 开销和计算机配置。

“Turning single-core processing into multi-core processing” refers to process-, instance-, and plug-in-chain-level offloading and scheduling. It does not rewrite a third-party plug-in's internally single-threaded DSP algorithm. Results depend on DAW routing, Bridge count, buffer size, plug-in behavior, IPC overhead, and the host computer.

## 当前公开版本 / Current public release

- 产品 / Product: **QQ Host**
- 厂商 / Vendor: **Qing Audio**
- 版本 / Version: **0.8.4**
- 发布日期 / Release date: **2026-09-01**
- 授权 / Licensing: **闭源专有软件 / Closed-source proprietary software**

### 下载 / Download

- [QQ Host 0.8.4 Release 页面 / Release page](https://github.com/Ziqing-Gu/QQHost-Release/releases/tag/v0.8.4)
- [直接下载 / Direct download: `QQ.Host.0.8.4.zip`](https://github.com/Ziqing-Gu/QQHost-Release/releases/download/v0.8.4/QQ.Host.0.8.4.zip)
- 公开资产 / Public asset: `QQ.Host.0.8.4.zip`
- 大小 / Size: `44,866,824 bytes`
- SHA-256: `B214AFF29543E79BE89BA7B8E91ED3891CA6E80AEC130CACE45D25F78BAE83EF`

总包包含 / The package contains:

- Windows 10/11 x64 VST3
- macOS 11+ Apple Silicon VST3 (`arm64`)
- macOS 11+ Intel VST3 (`x86_64`)
- macOS 11+ Universal 2 AU (`arm64 + x86_64`)
- 0.8.4 中英文安装说明 / 0.8.4 Chinese and English installation guides
- 0.8.4 中英文用户手册 / 0.8.4 Chinese and English user manuals

> 0.8.4 手册与安装说明包含 VST2/VST3 区分、LIVE/OFFLOAD 模式、独立 Hosted Editor、FL Studio 固定缓冲区要求，以及 macOS 安装与安全提示。
>
> The 0.8.4 manuals and installation guides cover VST2/VST3 identification, LIVE/OFFLOAD modes, independent Hosted Editors, FL Studio fixed-buffer requirements, and macOS installation/security notes.

## 支持范围 / Compatibility

- Windows 10/11 x64: VST3 Bridge + background `QQ Host.exe`
- macOS 11 or later: Apple Silicon VST3, Intel x86_64 VST3, Universal 2 AU
- Hosted plug-ins: licensed native 64-bit VST2 and VST3 audio effects; the browser labels each format and excludes instruments.
- 32-bit VST2 plug-ins are not supported. Cubase `.fxchainpreset` and standard `.vstpreset` operations remain VST3-only.
- macOS packages are not Apple Developer ID notarized.

## 安装与基本使用 / Installation and basic use

1. 完全退出 DAW 与插件扫描器。 / Fully quit the DAW and plug-in scanners.
2. 解压 `QQ.Host.0.8.4.zip`，进入 `Win` 或 `Mac` 选择对应平台包。 / Extract the archive and select the appropriate package under `Win` or `Mac`.
3. 按随包 0.8.4 安装说明删除旧版并复制新版；不要混用不同版本的 Bridge 与后台 Host。 / Follow the bundled 0.8.4 guide; never mix Bridge and Host versions.
4. 在 DAW 中重新扫描插件。 / Rescan plug-ins in the DAW.
5. 在轨道 Insert 中加载 `QQ Host Bridge`，再在 Bridge Rack 中加载第三方 VST2/VST3 效果器。 / Insert `QQ Host Bridge`, then load VST2/VST3 effects in its Rack.
6. FL Studio 用户必须在插件 Wrapper 的 Troubleshooting 中启用 `Process maximum size buffers` 和 `Use maximum buffer size from host`。 / FL Studio users must enable `Process maximum size buffers` and `Use maximum buffer size from host` in the plug-in Wrapper's Troubleshooting page.

## 主要功能 / Main features

- 保留 DAW Insert 工作流的 Bridge + 后台 Host 架构 / Bridge + background Host architecture preserving the DAW Insert workflow
- 多 Bridge、多 Slot VST2/VST3 效果器 Rack / Multi-Bridge, multi-Slot VST2/VST3 effect Rack
- OFFLOAD 与 LIVE / OFFLOAD and LIVE modes
- Internal PDC、Per-Slot PlayHead 与 Latency Rescue
- Sidechain、BYPASS ALL、Power、Fader、Pan、Polarity 与 Meter
- 隔离扫描并只收录效果器 / Isolated scanning restricted to audio effects
- Cubase FX Chain 载入/保存、自动参数镜像、Undo/Redo
- 工程恢复、Hosted Editor 与运行时故障隔离 / Project restore, Hosted Editor, and runtime fault isolation

## 0.8.4 更新摘要 / 0.8.4 summary

- 支持已获授权的原生 64-bit VST2 效果器；扫描结果明确标记 VST2/VST3，并继续排除乐器与 32-bit VST2。
- 将原 `LOW LATENCY` 工作流明确为 `LIVE`：适合实时监听和录音，不宣称提供 OFFLOAD 的确定性多核卸载收益。
- Bridge 与 Hosted Editor 可独立关闭；操作插件时 Bridge 保持可见，除非用户主动关闭。
- 修复无效 Slot 重新加载、首次窗口闪跳，以及空格等 DAW 快捷键转发回归。
- 保留 0.8.3 自动化恢复，以及既有 PDC、Rescue、Sidechain、FX Chain、Divider、Undo/Redo 与故障隔离行为。

- Hosts licensed native 64-bit VST2 effects, labels VST2/VST3 scan results, and continues to exclude instruments and 32-bit VST2 plug-ins.
- Clarifies the former `LOW LATENCY` workflow as `LIVE`, intended for real-time monitoring and recording without claiming OFFLOAD's deterministic multi-core offload benefit.
- Allows Bridge and Hosted Editor windows to close independently; the Bridge remains visible while a hosted plug-in is operated unless the user closes it.
- Fixes invalid-Slot reload, first-show window jumping, and the regression affecting Space and other DAW shortcut forwarding.
- Preserves the 0.8.3 automation recovery and the established PDC, Rescue, Sidechain, FX Chain, Divider, Undo/Redo, and fault-isolation behavior.

## 已知问题与升级注意 / Known issues and upgrade notes

- QQ Host 是实验性外部宿主；性能收益与延迟依赖 DAW、插件、缓冲区、IPC 开销与系统配置。
- 仅支持已获授权的原生 64-bit VST2 与 VST3 效果器；不支持乐器或 32-bit VST2。
- macOS 包未经 Apple Developer ID 公证，系统可能要求可信来源确认与 quarantine 处理。
- 旧工程若出现 Missing 自动化，只在确认后手动执行 `Reset Missing Automation...`，并检查 `Control NNN` 自动化轨道。
- Cubase `.fxchainpreset` 与标准 `.vstpreset` 操作仍为 VST3-only。
- FL Studio 必须启用两个最大固定缓冲区选项，否则 Bridge 可能不工作。
- 升级顺序：关闭 DAW -> 删除旧文件 -> 复制 0.8.4 -> 重新扫描。
- 以随包 0.8.4 手册和安装说明为准。

- QQ Host is experimental; performance and latency depend on the DAW, plug-ins, buffers, IPC overhead, and system configuration.
- Only licensed native 64-bit VST2 and VST3 effects are supported; instruments and 32-bit VST2 plug-ins are unsupported.
- macOS packages are not Apple Developer ID notarized and may require trusted-source confirmation and quarantine handling.
- Run `Reset Missing Automation...` only after confirmation and review `Control NNN` automation lanes.
- Cubase `.fxchainpreset` and standard `.vstpreset` operations remain VST3-only.
- FL Studio requires both maximum fixed-buffer options; otherwise the Bridge may not process correctly.
- Upgrade order: quit DAW -> remove old files -> copy 0.8.4 -> rescan.
- Follow the bundled 0.8.4 manuals and installation guides.

## 灵感与独立性声明 / Inspiration and independence

项目概念灵感来自 Vienna Ensemble Pro 8 的外部宿主与处理卸载工作流。QQ Host 为独立开发项目，与 Vienna Symphonic Library 无关联、授权或背书关系；灵感仅限于工作流方向，不涉及其代码或实现。

The concept was inspired by the external-host and processing-offload workflow of Vienna Ensemble Pro 8. QQ Host is independently developed and is not affiliated with, authorized by, or endorsed by Vienna Symphonic Library. The inspiration is limited to workflow direction, not code or implementation.

## 完整版本记录 / Complete version history

本 README 保留从 0.0.1 到 0.8.3 的既有完整历史，并追加 0.8.4；共覆盖 63 个真实版本。遗漏版本：无。

This README preserves the complete existing history from 0.0.1 through 0.8.3 and adds 0.8.4, covering 63 real versions in total. Omitted versions: none.

| 版本 / Version | 中文摘要 | English summary | 状态 / Status |
|---|---|---|---|
| 0.0.1 | 建立 QQ Compute 原型与 AI 开发文档；产品后来定名为 QQ Host。 | Established the QQ Compute prototype and AI development documentation; the product was later named QQ Host. | 历史原型 / Historical prototype |
| 0.0.2 | 引入实时 IPC 原型，验证 DAW Bridge 与外部进程通信方向。 | Introduced the real-time IPC prototype and validated communication between the DAW Bridge and an external process. | 历史原型 / Historical prototype |
| 0.0.3 | 探索确定性延迟与跨进程音频时序。 | Explored deterministic latency and cross-process audio timing. | 历史原型 / Historical prototype |
| 0.0.4 | 将处理截止时间固定为一个缓冲区。 | Fixed the processing deadline to one buffer. | 历史原型 / Historical prototype |
| 0.0.5 | 探索同一音频块的低延迟处理路径。 | Explored a same-block low-latency processing path. | 历史原型 / Historical prototype |
| 0.1.0 | 建立单个 VST3 效果器宿主能力。 | Established single-VST3-effect hosting. | 历史里程碑 / Historical milestone |
| 0.1.1 | 稳定跨进程处理截止时间。 | Stabilized the cross-process processing deadline. | 历史版本 / Historical version |
| 0.1.2 | 使用最新音频块并强化安全卸载。 | Adopted latest-block handling and safer unloading. | 历史版本 / Historical version |
| 0.1.3 | 改进基础工作流与用户体验。 | Improved the core workflow and user experience. | 历史版本 / Historical version |
| 0.1.4 | 加入 DAW 工程状态持久化。 | Added DAW project-state persistence. | 历史版本 / Historical version |
| 0.1.5 | 完善工作流与通道条控制。 | Refined the workflow and channel-strip controls. | 历史版本 / Historical version |
| 0.1.6 | 加入离线快速路径与安全实时加载。 | Added an offline fast path and safer live loading. | 历史版本 / Historical version |
| 0.1.7 | 完善 VST3 宿主与 Shift 精细调节。 | Refined VST3 hosting and Shift-based fine adjustment. | 历史版本 / Historical version |
| 0.2.0 | 建立 Bridge Rack 与后台 Agent 架构。 | Established the Bridge Rack and background Agent architecture. | 架构里程碑 / Architecture milestone |
| 0.2.1 | 修复音频引擎关键问题。 | Rescued critical audio-engine behavior. | 历史版本 / Historical version |
| 0.2.2 | 修复 UI 与工作流问题。 | Rescued UI and workflow behavior. | 历史版本 / Historical version |
| 0.2.3 | 完成向统一后台工作流的过渡。 | Completed the transition toward the unified background workflow. | 历史过渡版 / Historical transition |
| 0.3.0 | 集成工作流并改善兼容性。 | Integrated the workflow and improved compatibility. | 历史版本 / Historical version |
| 0.3.1 | 加入增量扫描与实时扫描进度。 | Added incremental scanning and live scan progress. | 历史版本 / Historical version |
| 0.3.2 | 修复扫描生命周期、真实刷新与透明 Rack。 | Repaired scanner lifetime, true refresh, and transparent Rack behavior. | 历史版本 / Historical version |
| 0.3.3 | 修复扫描数据库持久化。 | Rescued scanner-database persistence. | 历史版本 / Historical version |
| 0.3.4 | 提高插件扫描完整性。 | Improved plug-in scan completeness. | 历史版本 / Historical version |
| 0.3.5 | 加强 `moduleinfo.json` 与插件身份识别。 | Strengthened `moduleinfo.json` and plug-in identity recognition. | 历史版本 / Historical version |
| 0.3.6 | 修复版本身份与 UTF-8 文本处理。 | Rescued version identity and UTF-8 text handling. | 历史版本 / Historical version |
| 0.3.7 | 加固安全扫描器与 UTF-8 UI。 | Hardened the safe scanner and UTF-8 UI. | 历史版本 / Historical version |
| 0.3.8 | 隔离插件探测进程，并只收录效果器、排除乐器。 | Isolated plug-in probing and restricted the database to effects while excluding instruments. | 历史扫描基线 / Historical scanner baseline |
| 0.3.9 | 修复工作流输入、菜单交互与基于清单的加载。 | Rescued workflow input, menu interaction, and manifest-based loading. | 历史稳定基线 / Historical stable baseline |
| 0.4.0 | 建立多 Bridge 基础架构。 | Established the multi-Bridge foundation. | 历史架构里程碑 / Historical architecture milestone |
| 0.4.1 | 修复焦点处理与 Host 生命周期。 | Rescued focus handling and Host lifetime. | 历史版本 / Historical version |
| 0.4.2 | 支持独立编辑器窗口与动态尺寸。 | Added independent editor windows and dynamic resizing. | 历史版本 / Historical version |
| 0.4.3 | 修复多 Bridge 工程恢复与恢复流程。 | Rescued multi-Bridge project restoration and recovery. | 历史版本 / Historical version |
| 0.4.4 | 加入全局恢复静默区并优化工作流。 | Added Global Restore quiescence and polished the workflow. | 历史版本 / Historical version |
| 0.4.5 | 优化 Bridge 工作流与电平表。 | Polished the Bridge workflow and metering. | 历史版本 / Historical version |
| 0.4.6 | 修复 Bridge UI 与编辑器开关。 | Rescued Bridge UI and editor-toggle behavior. | 历史版本 / Historical version |
| 0.4.7 | 加固 Host 硬生命周期与编辑器状态。 | Hardened Host lifetime and editor-state handling. | 历史版本 / Historical version |
| 0.4.8 | 加入单次启动选举、重启 Host 与可调整 Bridge。 | Added single-launch election, Restart Host, and a resizable Bridge. | 历史版本 / Historical version |
| 0.4.9 | 完成响应式 UI 与 Hosted 工具栏。 | Completed the responsive UI and Hosted toolbar. | 历史版本 / Historical version |
| 0.5.0 | 加入原生 Sidechain 与标准 VST3 Preset。 | Added native Sidechain and standard VST3 preset support. | 历史版本 / Historical version |
| 0.5.1 | 加入多 Bridge 启动队列与 Bypass 图标。 | Added multi-Bridge startup cohort handling and the Bypass icon. | 历史版本 / Historical version |
| 0.5.2 | 对迟到的恢复会话执行自动回收。 | Added automatic recycling for late restore sessions. | 历史版本 / Historical version |
| 0.5.3 | 加入迟到会话恢复屏障与编辑器激活修复。 | Added the late-session restore barrier and editor-activation rescue. | 历史版本 / Historical version |
| 0.5.4 | 加入恢复事务看门狗。 | Added the Restore Transaction Watchdog. | 历史版本 / Historical version |
| 0.5.5 | 加入 Agent 启动事务监督器。 | Added the Agent Startup Transaction Supervisor. | 历史版本 / Historical version |
| 0.5.6 | 优化 Preset、Rack 与 Browser 工作流。 | Polished the Preset, Rack, and Browser workflow. | 历史版本 / Historical version |
| 0.5.7 | 修复文本输入、编辑器尺寸与启动卡顿。 | Rescued text input, editor sizing, and startup stalls. | 历史稳定基线 / Historical stable baseline |
| 0.5.8 | 同步 Hosted Editor 窗口尺寸并采用响应式工具栏。 | Synchronized Hosted Editor window sizing and introduced a responsive toolbar. | 历史稳定基线 / Historical stable baseline |
| 0.5.9 | 加入运行时故障隔离与单 Slot 重启，降低第三方插件故障对整个后台 Host 的影响。 | Added runtime fault isolation and per-Slot restart to reduce the impact of third-party plug-in faults on the background Host. | 2026-08-30 · 历史稳定基线 / Historical stable baseline |
| 0.6.0 | 加入按上下文转发 DAW 快捷键，同时保护文本输入与插件自身快捷键。 | Added context-aware DAW shortcut forwarding while protecting text entry and plug-in-owned shortcuts. | 2026-08-30 · 历史候选 / Historical candidate |
| 0.6.1 | 修复外部插件 Undo/Redo 保留策略，避免 Bridge 快捷键破坏被宿主插件的历史。 | Corrected hosted plug-in Undo/Redo preservation so Bridge shortcuts do not disrupt plug-in history. | 2026-08-30 · 历史稳定基线 / Historical stable baseline |
| 0.7.0 | 试验手动自动化映射基础；该方案后来被自动参数镜像替代。 | Prototyped manual automation mapping; this approach was later replaced by automatic parameter mirroring. | 2026-08-31 · 已替代候选 / Superseded candidate |
| 0.7.1 | 加入自动参数镜像和 Host Touch 反馈，取代手动映射流程。 | Added automatic parameter mirroring and Host Touch feedback, replacing the manual mapping workflow. | 2026-08-31 · 历史版本 / Historical version |
| 0.7.2 | 加入 Bridge 尺寸持久化与时序诊断，便于定位界面尺寸问题。 | Added Bridge resize persistence and timing diagnostics for editor-size investigation. | 2026-08-31 · 历史候选 / Historical candidate |
| 0.7.3 | 修复自动化恢复状态，并加入 Bridge Undo/Redo 与插件状态恢复。 | Protected automation restore state and added Bridge Undo/Redo with hosted plug-in state restoration. | 2026-08-31 · 历史稳定基线 / Historical stable baseline |
| 0.7.4 | 增加上下文 S/M/L 快捷键转发，并以只读方式探测 Cubase Insert 拖拽载荷。 | Added context-aware S/M/L shortcut forwarding and a read-only Cubase Insert drag-payload probe. | 2026-08-31 · 历史候选 / Historical candidate |
| 0.7.5 | 引入内部 PDC 与每 Slot PlayHead，修复链内时间线错位。 | Introduced internal PDC and per-Slot PlayHead handling to correct in-chain timeline misalignment. | 2026-08-31 · 已验证的延续功能 / Validated carry-forward feature |
| 0.7.6 | 扩展 Cubase 拖拽 OLE 探测与诊断，但未实现未经验证的直接导入。 | Expanded Cubase drag OLE probing and diagnostics without implementing unverified direct import. | 2026-08-31 · 历史探针版本 / Historical probe |
| 0.7.7 | 加入 Cubase FX Chain 载入/保存与自宿主防护；互操作性保持受限验证状态。 | Added Cubase FX Chain load/save and self-host protection; interoperability remained a limited-validation feature. | 2026-08-31 · 历史候选 / Historical candidate |
| 0.7.8 | 改进 Divider、扫描隔离/效果器过滤、FX Chain 快速载入和 Fixed-Zero Rescue；保留兼容性边界。 | Improved Divider behavior, scan isolation/effect filtering, fast FX Chain loading, and Fixed-Zero Rescue while retaining compatibility boundaries. | 2026-08-31 · 历史候选 / Historical candidate |
| 0.8.0 | 加入 50 ms Crossfade 的 BYPASS ALL、明确的 Power UI 与 VST2 链加载保护；用户提升为稳定基线。 | Added 50 ms-crossfaded BYPASS ALL, explicit Power UI, and VST2 chain-load protection; user-promoted to Stable. | 2026-08-31 · 历史稳定基线 / Historical stable baseline |
| 0.8.1 | 将 Bypass 统一为醒目的 `B` 控件，并恢复“初始匿名、可选命名”的 Divider 工作流；不改变受保护的音频与状态行为。 | Unified Bypass as a prominent `B` control and restored the “anonymous by default, optionally nameable” Divider workflow without changing protected audio or state behavior. | 2026-08-31 · 正式回滚基线 / Formal rollback baseline |
| 0.8.2 | 修复 Hosted 自动化回声与抖动、16-Slot FX Chain 写入、旧 FX Chain 自动化关联，以及 Fader/Pan/相位 Undo/Redo。 | Corrected Hosted automation echo/jitter, 16-Slot FX Chain export, automation association for older FX Chains, and Fader/Pan/polarity Undo/Redo. | 2026-09-01 · 已验证候选 / Validated candidate |
| 0.8.3 | 安全归一化旧通用 VST3 标识与精确 CID，并加入只清理 Missing、保留 Active 的显式自动化恢复。 | Safely canonicalised legacy generic VST3 identities to exact CIDs and added explicit recovery that removes only Missing mappings while preserving Active mappings. | 2026-09-01 · 历史稳定基线 / Historical stable baseline |
| 0.8.4 | 支持已授权的 64-bit VST2 效果器并标记 VST2/VST3；将低延迟模式明确为 LIVE；修复独立编辑器、无效 Slot 重载、首次窗口闪跳和 DAW 快捷键转发。 | Added licensed 64-bit VST2 effect hosting with VST2/VST3 labels; clarified low-latency operation as LIVE; fixed independent editors, invalid-Slot reload, first-show jumping, and DAW shortcut forwarding. | 2026-09-01 · **当前稳定基线 / Current stable baseline** |
## 源码与公开边界 / Source and publication boundary

QQ Host 为闭源软件，源码仓库保持私有。本仓库不包含源码、构建缓存、内部日志、私有路径或开发凭据，只提供公开说明与用户批准的二进制 Release。

QQ Host is closed-source software and its source repository remains private. This repository contains no source code, build cache, internal logs, private paths, or development credentials; it provides only public documentation and user-approved binary releases.