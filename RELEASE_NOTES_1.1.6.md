# QQ Host 1.1.6 Stable / Scan Management and Format Filter

发布日期 / Release date: 2026-10-13
上一稳定版本 / Previous Stable: 1.1.5

## 中文

- 扫描目录现在可以逐项移除；移除正在使用的扫描目录会请求取消当前扫描，下次按新目录列表扫描。
- 阻止误加整盘、网络共享根目录和 macOS 卷根目录；旧的误加根目录仍可移除，扫描会跳过它们。
- “管理”菜单支持选择单个插件文件扫描，以及按 VST2 / VST3 增量扫描；macOS 另支持 AU。Refresh 保留全部格式增量扫描。
- 插件列表支持移除选中项、移除不存在文件的项目、按格式移除及清空；右键可定位文件或单独重新扫描。
- 加载浏览器新增“全部格式 / VST2 / VST3”筛选，macOS 另有 AU，记住上次选择，可配合搜索、收藏及分类。
- 修复不能移除误加扫描目录的管理缺口；扫描可在目录遍历期间响应取消请求。暂无额外音频或预置修复声明。

## English

- Remove individual custom scan folders. Removing a folder during a scan requests cancellation; the next scan uses the updated folder list.
- Reject whole-drive, network-share and macOS volume roots. Previously saved roots remain removable and are skipped during discovery.
- Manage supports scanning one plug-in file and incremental VST2-only or VST3-only scans; macOS also supports AU. Refresh keeps incremental scanning across all formats.
- Remove selected catalog rows, missing-file entries, all entries of a format, or the entire list. Right-click to reveal a file or rescan it individually.
- The loading browser adds a remembered All / VST2 / VST3 filter, plus AU on Mac, used together with search, favorites and categories.
- Resolves the inability to remove accidental scan folders and makes directory traversal responsive to cancellation requests. No additional audio or preset fix is claimed.

## 兼容、升级与限制 / Compatibility, upgrade and limits

Windows 10/11 x64 VST3; macOS 12+ Apple Silicon VST3, Intel x86_64 VST3 and Universal 2 AU.
升级前关闭 DAW 和 QQ Host；Bridge 与后台程序应一起升级。已有工程的 Power 和插件状态保持原行为。
Quit the DAW and QQ Host before upgrading both the Bridge and background app. Existing Power and project-state behavior is retained.

移除目录不删除列表项目；移除列表项目不卸载软件或移除工程内已加载的插件。以后再次主动扫描仍可重新发现被移除项目。
Removing a folder does not remove catalog entries. Removing entries does not uninstall software or unload project instances. A later deliberate scan may rediscover removed entries.
取消请求不能强制中断尚未返回的操作系统文件调用；若文件被其他程序阻塞，需要等待调用返回。
Cancellation cannot interrupt an operating-system file call that has not returned.
只支持原生 64-bit 效果器；不包含 32-bit 桥接，Instrument/Synth/Sampler 不列入效果器浏览器。
Native 64-bit effects only; no 32-bit bridge. Instruments, synths and samplers are excluded from the effects browser.

## 验证 / Validation

继承已通过的 Windows 构建、181 项隔离回归和安装核验。三套 Mac 成品已通过版本、架构、签名与中文编码检查；不将编译通过等同于所有 DAW 的听感验收。
Reuses the passing Windows build, 181 isolated regression checks and installation verification. Three Mac packages passed version, architecture, signature and Chinese encoding checks; successful builds do not establish listening acceptance in every DAW.

## 安装与附件 / Installation and assets

退出 DAW 和 QQ Host 后成对升级 Bridge 与后台程序。Mac 使用 ad-hoc 签名，未经过 Apple Developer ID 公证；详细步骤见双语安装指南。附件仅为四套安装包、两份安装说明和两本已更新的 1.1.6 手册，源码保持私有。
Quit the DAW and QQ Host before upgrading both the Bridge and background app. Mac bundles are ad-hoc signed, not Apple Developer ID notarized; follow the bilingual installation guides. The eight assets are four platform packages, two guides and two updated 1.1.6 manuals. Source stays private.

- [Windows x64 VST3](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.6/QQ.Host.1.1.6.Windows.x64.VST3.zip)
- [macOS Apple Silicon VST3](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.6/QQ.Host.1.1.6.macOS.Apple.Silicon.VST3.zip)
- [macOS Intel x86_64 VST3](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.6/QQ.Host.1.1.6.macOS.Intel.x86_64.VST3.zip)
- [macOS Universal 2 AU](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.6/QQ.Host.1.1.6.macOS.Universal.2.AU.zip)
- [中文安装说明 / Chinese installation guide](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.6/QQ.Host.1.1.6.Installation.Guide.Chinese.txt)
- [English installation guide](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.6/QQ.Host.1.1.6.Installation.Guide.English.txt)
- [中文用户手册 / Chinese user manual](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.6/QQ.Host.1.1.6.User.Manual.Chinese.pdf)
- [English user manual](https://github.com/Qing-Audio/QQHost-Release/releases/download/v1.1.6/QQ.Host.1.1.6.User.Manual.English.Edition.pdf)
