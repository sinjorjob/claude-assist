<p align="center">
  <strong>Claude Assist</strong><br>
  <em>Claude Code Input Assistant GUI</em>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/platform-Windows%2010%2F11-0078D6?logo=windows" alt="platform">
  <img src="https://img.shields.io/badge/python-3.10+-3776AB?logo=python&logoColor=white" alt="python">
  <img src="https://img.shields.io/badge/license-MIT-green" alt="license">
  <img src="https://img.shields.io/badge/Claude%20Code-Skill-7C3AED" alt="skill">
</p>

---

Claude Code のチャット欄への入力を支援する GUI ツールです。
長文の指示作成、テンプレート管理、ファイル参照付き指示の送信を快適に行えます。

## ✨ 機能一覧

| | 機能 | 説明 |
|:-:|------|------|
| 📝 | **複数行入力** | 改行を含む長文プロンプトをGUIで作成・送信 |
| 📋 | **テンプレート** | よく使う指示文を保存・編集・再利用（最大100件） |
| 🕐 | **入力履歴** | 過去の入力を一覧表示・再利用・テンプレ保存（最大50件） |
| 📎 | **ファイル添付** | ファイルの `@パス` をClaudeに送信し中身を読ませる |
| 📚 | **参照情報** | フォルダ/ファイルを設定し毎回自動でClaudeに読ませる |
| 🖼️ | **画像貼付** | `Ctrl+V` でスクリーンショット等を添付 |
| ⚡ | **スラッシュコマンド** | `/skill-name` を正しくClaudeに送信 |
| 🌐 | **日英切替** | UIの表示言語を日本語/英語に切り替え |

## 📋 動作要件

| 項目 | 要件 |
|------|------|
| 🖥️ OS | Windows 10 / 11 |
| 🐍 Python | 3.10 以上 |
| 📦 uv | Python パッケージランナー（下記参照） |
| 🤖 Claude Code | インストール済みであること |

> 💡 Python 依存パッケージ（customtkinter, Pillow）は `uv run` 実行時に**自動インストール**されます。
> ユーザーが手動でインストールする必要はありません。

---

## 🚀 インストール

### Step 1 — uv のインストール

uv は Python のパッケージ管理・スクリプト実行ツールです。
未インストールの場合、以下のいずれかの方法でインストールしてください。

**▶ PowerShell（推奨）:**
```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

**▶ pip:**
```powershell
pip install uv
```

**▶ winget:**
```powershell
winget install --id=astral-sh.uv -e
```

インストール後、ターミナルを**再起動**して以下で確認:
```powershell
uv --version
```

### Step 2 — ファイル配置（Claude Code スキルとして登録）

`claude-assist` フォルダを Claude Code の skills ディレクトリにコピーします:

```
📁 %USERPROFILE%\.claude\skills\claude-assist\
 ├── 📄 SKILL.md
 └── 📁 scripts\
     └── 🐍 claude_assist.py
```

**コマンド例:**
```powershell
xcopy /E /I claude-assist "%USERPROFILE%\.claude\skills\claude-assist"
```

### Step 3 — 動作確認

Claude Code のチャットで以下を入力:
```
/claude-assist
```
✅ GUI ウィンドウが起動すれば成功です！

---

## 📖 使い方

### 基本フロー

```
 1️⃣  Claude Code で /claude-assist を実行
      ↓
 2️⃣  GUI ウィンドウが起動
      ↓
 3️⃣  入力欄に指示文を書く
      ↓
 4️⃣  送信 ボタン（または Ctrl+Enter）
      ↓
 5️⃣  Claude Code のチャット欄にテキストが自動入力！
```

### スタンドアロン起動（スキルを使わない場合）

ターミナルで以下を実行してから Claude を起動:
```bash
uv run path/to/claude_assist.py
claude
```

### ⌨️ キーボードショートカット

| ショートカット | 機能 |
|:-:|------|
| `Ctrl+Enter` | 📤 送信 |
| `Ctrl+H` | 🕐 履歴を表示 |
| `Ctrl+T` | 📋 テンプレート一覧を表示 |
| `Ctrl+L` | 🧹 入力欄をクリア |
| `Ctrl+V` | 📎 テキスト or 画像を貼り付け |
| `Ctrl+A` | ✅ 入力欄を全選択 |

### 📋 テンプレート

| 操作 | 方法 |
|------|------|
| ➕ 新規作成 | テンプレート画面の「+ 新規作成」ボタンから名前と内容を入力 |
| 🕐 履歴から保存 | 履歴画面の「テンプレ保存」ボタンから保存 |
| ✏️ 編集 | テンプレート一覧の「編集」ボタンで名前・内容を修正 |
| ▶️ 使用 | 「使用」ボタンで入力欄に貼り付け |
| ❌ 削除 | 各テンプレートの「×」ボタンで個別削除 |

### 📚 参照情報

フォルダやファイルを「参照情報」に登録すると、毎回の送信時に自動で `@パス` が付与され、
Claude が中身を読んで回答します。

### 🔧 デバッグモード

問題発生時はスキルのコマンドに `--debug` を追加:
```bash
uv run path/to/claude_assist.py --skill --debug
```
ログは `data/_debug.log` に出力されます。

---

## 📁 ファイル構成

```
claude-assist/
├── 📄 SKILL.md              ← Claude Code スキル定義
├── 📄 README.md             ← このファイル（ユーザーガイド）
├── 📄 DESIGN.md             ← 設計書
├── 📁 scripts/
│   └── 🐍 claude_assist.py  ← アプリケーション本体
└── 📁 data/                 ← 実行時に自動生成
    ├── 📊 history.json      ← 入力履歴
    ├── 📊 templates.json    ← テンプレートデータ
    └── 📊 config.json       ← 設定（言語、参照情報等）
```

---

## 📜 ライセンス

MIT License
