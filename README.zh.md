# Codex Statusline

[🇧🇷 Português](README.md) · [🇺🇸 English](README.en.md) · [🇪🇸 Español](README.es.md) · [🇯🇵 日本語](README.ja.md) · [🇨🇳 中文](README.zh.md)

适用于 **Codex CLI** 原生状态栏的精简配置，可在一行中显示模型、项目、Git 分支、上下文使用量、使用限额和审批模式。

![Codex 原生状态栏预览](assets/statusline-preview.svg)

> 图片仅为示意。Codex 将内置指标显示为文本；本项目不会绘制图形进度条。

## 示例

```text
GPT-6-Luna medium · 08 - statusline · main · Context 8% used · 258K window · weekly 98% left · Ask for approval
```

具体数值会因会话、账户和 Codex 版本而异。数据不可用时，相应指标可能不会显示。

## 安装

1. Windows 用户打开 `%USERPROFILE%\.codex\config.toml`；macOS/Linux 用户打开 `~/.codex/config.toml`。
2. 复制 [`codex-statusline.toml`](codex-statusline.toml) 中的配置块。
3. 如果文件已有 `[tui]` 段，只合并下面两个选项，并保留其他设置。
4. 重启 Codex。在 Codex CLI 中也可以打开 `/statusline` 来选择和调整指标顺序。

```toml
[tui]
status_line = [
  "model-with-reasoning",
  "project-name",
  "git-branch",
  "context-used",
  "context-window-size",
  "weekly-limit",
  "approval-mode",
]
status_line_use_colors = true
```

## 指标

| 指标 | 信息 |
| --- | --- |
| `model-with-reasoning` | 当前模型和推理级别。 |
| `project-name` | Codex 检测到的项目名称。 |
| `git-branch` | 当前 Git 分支（仅在 Git 仓库中显示）。 |
| `context-used` | 当前对话已使用的上下文百分比。 |
| `context-window-size` | 可用时显示上下文窗口总大小。 |
| `weekly-limit` | 账户数据可用时显示每周剩余用量。 |
| `approval-mode` | 当前命令审批模式。 |

Codex 还提供 `five-hour-limit`；将它加入 `status_line` 即可显示 5 小时使用限额。

## 此配置不支持的功能

Codex 原生状态栏只能选择预定义指标并在页脚显示，不会运行自定义渲染脚本。因此，本项目以文本显示百分比，不提供图形进度条、按使用率阈值变色或重置时间。`status_line_use_colors` 使用主题原生颜色，但不能配置按使用率变化的颜色阈值。

原生状态栏也不提供提示缓存状态或需要重新写入缓存的 token 数量。

## 兼容性

已在 Windows 的 Codex CLI `0.165.0-alpha.1.2` 上验证。可用指标可能随版本变化；请使用 `/statusline` 查看当前安装支持的选项。

## 许可证

MIT。详见 [`LICENSE`](LICENSE)。
