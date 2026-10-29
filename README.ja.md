# Codex Statusline

[🇧🇷 Português](README.md) · [🇺🇸 English](README.en.md) · [🇪🇸 Español](README.es.md) · [🇯🇵 日本語](README.ja.md) · [🇨🇳 中文](README.zh.md)

**Codex CLI** の標準ステータスライン向けのシンプルな設定です。モデル、プロジェクト、Git ブランチ、コンテキスト使用量、使用制限、承認モードを1行に表示します。

![Codex 標準ステータスラインのプレビュー](assets/statusline-preview.svg)

> 画像は表示例です。Codex の標準インジケーターはテキストで表示され、このプロジェクトはグラフィカルな進捗バーを描画しません。

## 表示例

```text
GPT-6-Luna medium · 08 - statusline · main · Context 8% used · 258K window · weekly 98% left · Ask for approval
```

値はセッション、アカウント、Codex のバージョンによって異なります。データがない項目は表示されない場合があります。

## インストール

1. Windows では `%USERPROFILE%\.codex\config.toml`、macOS/Linux では `~/.codex/config.toml` を開きます。
2. [`codex-statusline.toml`](codex-statusline.toml) の設定ブロックをコピーします。
3. `[tui]` セクションが既にある場合は、以下の2項目だけを追加または置き換え、他の設定は残します。
4. Codex を再起動します。Codex CLI では `/statusline` を開いて項目の選択や並べ替えもできます。

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

## インジケーター

| 項目 | 表示内容 |
| --- | --- |
| `model-with-reasoning` | 現在のモデルと推論レベル。 |
| `project-name` | Codex が検出したプロジェクト名。 |
| `git-branch` | Git リポジトリ内にある場合の現在のブランチ。 |
| `context-used` | 会話コンテキストの使用率。 |
| `context-window-size` | 利用可能な場合のコンテキストウィンドウ全体のサイズ。 |
| `weekly-limit` | アカウントで利用可能な場合の週次使用量の残り。 |
| `approval-mode` | 現在のコマンド承認モード。 |

Codex には `five-hour-limit` もあります。5時間の使用制限を表示するには `status_line` に追加してください。

## この設定でできないこと

Codex の標準ステータスラインは、定義済みの項目を選んでフッターに表示します。独自の描画スクリプトは実行できません。そのため、このプロジェクトでは使用率をテキストで表示し、グラフィカルなバー、しきい値に応じた色分け、リセット時刻は表示しません。`status_line_use_colors` はテーマ標準の色を有効にしますが、使用率に応じた色のしきい値は設定しません。

プロンプトキャッシュの状態や、キャッシュに再書き込みされるトークン数も標準ラインには表示されません。

## 互換性

Windows の Codex CLI `0.165.0-alpha.1.2` で確認しています。利用可能な項目はバージョンによって異なる場合があります。`/statusline` でインストール環境の項目を確認してください。

## ライセンス

MIT。詳細は [`LICENSE`](LICENSE) を参照してください。
