# Codex Statusline

[🇧🇷 Português](README.md) · [🇺🇸 English](README.en.md) · [🇪🇸 Español](README.es.md) · [🇯🇵 日本語](README.ja.md) · [🇨🇳 中文](README.zh.md)

A compact configuration for the **Codex CLI** native status line. It brings model, project, Git branch, context usage, usage limits, and approval mode together in one line.

![Preview of the native Codex status line](assets/statusline-preview.svg)

> This image is an illustrative preview. Codex renders its built-in indicators as text; this project does not draw graphical progress bars.

## Example

```text
GPT-6-Luna medium · 08 - statusline · main · Context 8% used · 258K window · weekly 98% left · Ask for approval
```

Values vary by session, account, and Codex version. Indicators may be omitted when data is unavailable.

## Installation

1. Open `%USERPROFILE%\.codex\config.toml` on Windows or `~/.codex/config.toml` on macOS/Linux.
2. Copy the block from [`codex-statusline.toml`](codex-statusline.toml).
3. If a `[tui]` section already exists, merge only the two options below and keep the rest of your settings.
4. Restart Codex. In Codex CLI, you can also open `/statusline` to select and reorder indicators.

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

## Indicators

| Indicator | Information |
| --- | --- |
| `model-with-reasoning` | Current model and reasoning effort. |
| `project-name` | Project name detected by Codex. |
| `git-branch` | Current branch when the folder is in a Git repository. |
| `context-used` | Percentage of the conversation context already used. |
| `context-window-size` | Total context window size, when available. |
| `weekly-limit` | Remaining weekly usage, when available for the account. |
| `approval-mode` | Current command approval mode. |

Codex also provides `five-hour-limit`; add it to `status_line` to show the 5-hour usage limit.

## What this configuration does not do

Codex's native status line accepts predefined indicators and renders them in the footer. It does not run a custom rendering script. This project therefore shows percentages as text, without graphical bars, threshold-based colors, or reset times. `status_line_use_colors` enables the theme's native colors; it does not set usage color thresholds.

The native line also does not provide prompt-cache warmth or tokens-to-rewrite indicators.

## Compatibility

Validated with Codex CLI `0.165.0-alpha.1.2` on Windows. Available indicators may vary by version; use `/statusline` to check your installation.

## License

MIT. See [`LICENSE`](LICENSE).
