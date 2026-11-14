# Emulsion Desktop 反馈

Emulsion 桌面端的问题反馈入口：报告 bug、安装升级问题，或者提功能建议，都在这里开 issue。

[提交 issue](https://github.com/ushaio/emulsion-feedback/issues/new/choose) · [下载最新版](https://mo.shaio.top/download) · [使用文档](https://mo.shaio.top/docs) · [更新日志](https://mo.shaio.top/docs/changelog)

## 提交前

1. 更新到最新版（设置 → 关于 → 检查更新）
2. 搜一下已有 issue，同一个问题跟帖比另开一条有用
3. 一条 issue 只讲一件事

## 请带上

- **版本与系统**：设置 → 关于 →「复制诊断摘要」，原样粘贴
- **复现步骤**：编号写，能稳定复现最好
- **截图 / 录屏**：界面问题基本必需
- **日志**：设置 → 日志 打开「启用日志」，复现一次后附上 `logs.json`

日志目录：

| 系统 | 路径 |
| --- | --- |
| Windows | `%APPDATA%\mo-gallery-desktop\logs\` |
| macOS | `~/Library/Application Support/mo-gallery-desktop/logs/` |
| Linux | `~/.config/mo-gallery-desktop/logs/` |

## 几种常见情况

- **macOS 提示「Emulsion 已损坏，无法打开」**：浏览器下载带了隔离标记。执行 `xattr -dr com.apple.quarantine /Applications/Emulsion.app`，或到「系统设置 → 隐私与安全性」点「仍要打开」
- **Windows 提示「已保护你的电脑」或杀软报毒**：点「更多信息 → 仍要运行」
- **应用内更新失败**：更新读取官方清单，不经过 GitHub；网络受限时去[下载页](https://mo.shaio.top/download)手动安装
- **插件装不上**：插件只在桌面端「设置 → 插件」里安装

## English

Emulsion Desktop feedback — report bugs, installation problems and feature requests here.

Before submitting: update to the latest version (Settings → About → Check for updates) and search existing issues. One issue per problem.

Please include your version and OS (Settings → About → copy diagnostics), reproduction steps, a screenshot when the UI is involved, and `logs.json` if logging is relevant — enable logging in Settings → Logs first, then reproduce. Log directories: `%APPDATA%\mo-gallery-desktop\logs\` on Windows, `~/Library/Application Support/mo-gallery-desktop/logs/` on macOS, `~/.config/mo-gallery-desktop/logs/` on Linux.

macOS "Emulsion is damaged" is the quarantine flag from browser downloads: run `xattr -dr com.apple.quarantine /Applications/Emulsion.app`, or allow it under System Settings → Privacy & Security. In-app updates read the official manifest rather than GitHub; if they fail, install from the [download page](https://mo.shaio.top/download). Plugins can only be installed from Settings → Plugins inside the desktop app.

Security issues: please use the private advisory flow described in [SECURITY.md](SECURITY.md).
