# Emulsion 桌面端 · 问题反馈

Emulsion（MO Gallery 桌面工作台）是**闭源**桌面应用：本地资源库、跨存储管理、图文创作与 Zine 出版，覆盖 Windows / macOS / Linux。桌面端仍在快速迭代，这个仓库只做一件事——收集你在使用中遇到的问题和想法。

**[提交反馈](https://github.com/ushaio/emulsion-feedback/issues/new/choose)** · [下载最新版](https://mo.shaio.top/download) · [使用文档](https://mo.shaio.top/docs) · [更新日志](https://mo.shaio.top/docs/changelog) · [官网](https://mo.shaio.top)

## 这里能做什么

| 可以在这里说 | 这里办不了 |
| --- | --- |
| 崩溃、报错、功能异常 | 提代码 PR（客户端闭源，不接受代码贡献） |
| 安装、升级、启动失败 | 下载安装包（请走[官网下载页](https://mo.shaio.top/download)） |
| 功能建议、交互与文案改进 | 账号登录、付费、发票等账号事务（走官网） |
| 使用方式疑问（建议先翻[文档](https://mo.shaio.top/docs)） | 贴他人隐私照片、密钥、站点密码 |
| 安全漏洞（请走私密渠道，见 [SECURITY.md](SECURITY.md)） | 当作发版页 / 更新公告页使用 |

## 提交前 30 秒

1. **先更新到最新版**：设置 → 关于 → 检查更新。旧版本上的问题，很可能已经修好了。
2. **搜一下已有 issue**：同一个问题往往已经有人报过，跟帖补充信息比另开一条更有用。
3. **看一眼下一节的「常见情况」**：相当一部分"bug"在那里就有答案。
4. **一条 issue 只讲一件事**：两件事混在一起，最后只能修掉一件。

## 这些情况通常不是 bug

- **macOS 提示「Emulsion 已损坏，无法打开」**
  从浏览器下载的包带「隔离」标记，未公证的包在这一档右键「打开」是无效的。终端执行
  `xattr -dr com.apple.quarantine /Applications/Emulsion.app`，或到「系统设置 → 隐私与安全性」点「仍要打开」。官网下载页的「命令安装」方式用 curl 直取文件，不带隔离标记，首次打开不会被拦。

- **Windows 提示「Windows 已保护你的电脑」/ 杀软报毒**
  新版本安装包还没积累起足够的下载信誉，属于常见误报。点「更多信息 → 仍要运行」；仍被拦截，可临时关闭实时防护完成安装，装完立刻打开。

- **首次启动很慢、停在初始化**
  首次运行要建本地库、生成索引、准备运行时，慢是正常的。后续启动才会回到秒开。

- **应用内更新失败**
  更新读取的是官方清单（`mo.shaio.top`，备用 `mo-dl.shaio.top`），**不经过 GitHub**。网络受限时，直接去下载页拿新安装包覆盖安装即可，数据不会丢。

- **插件装不上**
  插件只在桌面端「设置 → 插件」里安装，网页端不能装。安装前会列出插件需要的权限，需要你逐项确认。

- **云空间 / 站点相关功能用不了**
  需要登录 Emulsion 账号。内测阶段部分能力按账号开通，不是所有人默认可见。

- **Linux 上版本落后于 Windows / macOS**
  各平台发版节奏不完全同步。下载页上某平台没有新包，就是该平台暂时没跟进，不是页面坏了——这种不必提 issue。

## 一份能让我们直接开工的反馈

- **版本号与系统**：设置 → 关于 →「复制诊断摘要」，原样粘贴。它长这样：

  ```
  Emulsion Desktop v0.9.3 (Production)
  OS: Windows (x64)
  Timestamp: 2026-11-14T09:57:45.000Z
  ```

- **复现步骤**：1、2、3……写得像交给别人的操作说明，能稳定复现最好。
- **期望结果 / 实际结果**：你以为会发生什么，实际发生了什么。
- **截图或录屏**：界面错位、渲染异常、报错弹窗这类问题，截图几乎是必需的。
- **日志**：默认**关闭**。需要先在 设置 → 日志 打开「启用日志」，再复现一次，然后把日志目录里的文件附上。路径见下一节。

## 日志在哪

设置 → 日志 →「打开日志目录」可以直接跳转。手动找的话：

| 系统 | 路径 |
| --- | --- |
| Windows | `%APPDATA%\mo-gallery-desktop\logs\logs.json` |
| macOS | `~/Library/Application Support/mo-gallery-desktop/logs/logs.json` |
| Linux | `~/.config/mo-gallery-desktop/logs/logs.json` |

日志是 JSON 数组，按 `auth` / `upload` / `photo` / `album` / `story` / `blog` / `storage` / `ai` / `system` 分类，可在日志页按分类和等级筛选。**打开开关之前发生的事不会被记录**，所以顺序是：开日志 → 复现 → 取文件。

## 处理节奏与标签

维护者按收到顺序看，**崩溃、数据丢失、上传失败优先**。功能建议会进评估，不承诺一定实现。

| 标签 | 含义 |
| --- | --- |
| `待确认` | 已收到，还没复现 |
| `已复现` | 我们复现了，在排期修 |
| `需要更多信息` | 缺版本、步骤或日志，等你补充 |
| `已修复` | 修复已进入某个版本，见 issue 里的版本号 |
| `暂不修复` | 当前不打算改，issue 里会写原因 |
| `安装与升级` | 安装包、更新、启动相关 |
| `平台: Windows` / `平台: macOS` / `平台: Linux` | 问题所属平台 |

## 隐私

反馈区是公开的。日志里可能带本地文件路径、站点域名和操作记录，贴之前扫一眼；**不要上传他人照片、密钥、密码、数据库连接串**。万一传错了，可以编辑 issue 删掉附件，或留言让我们清理。

## English

Emulsion is a closed-source desktop app for local photo libraries, multi-storage management, writing and Zine publishing (Windows / macOS / Linux). Use this repository to report bugs, installation problems and feature requests — in Chinese or English. Please include your app version and OS (Settings → About → copy diagnostics), reproduction steps, and a screenshot when the UI is involved. Security issues should go through the private advisory flow described in [SECURITY.md](SECURITY.md), not a public issue.

---

© 2026 MO Gallery（ushaio）。本仓库仅用于收集反馈；Emulsion 桌面端为闭源商业软件，客户端源代码不在此仓库。
