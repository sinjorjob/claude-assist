---
name: claude-assist
description: "複数行入力GUIを起動してClaudeのチャット欄に送信する入力支援ツール。長文の指示、テンプレート活用、ファイル参照付き指示の作成に便利。Use when the user wants to compose a multi-line prompt via GUI."
allowed-tools: "Bash(uv *)"
---

# Claude Assist - 複数行入力支援GUI

Claude Codeのチャット欄への入力を支援するGUIツールを起動します。

## 実行手順

1. 以下のコマンドを実行してGUIをバックグラウンドで起動する:

```bash
uv run ${CLAUDE_SKILL_DIR}/scripts/claude_assist.py --skill
```

2. コマンドは即座に完了する（GUIは別プロセスで起動済み）。
3. ユーザーがGUIで指示文を作成し送信すると、Claudeのチャット欄に直接テキストが入力される。

## 注意事項

- コマンド実行後、GUIは別ウィンドウで起動する。コマンド自体はすぐに終了する。
- ユーザーがGUIから送信したテキストは自動的にClaudeのチャット欄に入力される。
- このコマンド実行後、「GUIを起動しました」と短く伝えるだけでよい。追加の説明は不要。
