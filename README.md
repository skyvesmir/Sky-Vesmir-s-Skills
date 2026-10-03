# Sky Vesmir's Skills (`sky-vesmir-skills`)

Google Drive の大規模整理・Obsidian Vault 最適化スキルと、商業出版基準の厳格な小説編集・校正・表現トレーニングスキルを収録した Claude プラグインです。

---

## 収録スキル

### 1. `drive-organizer-obsidian-optimizer`
Google Drive 内の大量ファイル（数百〜数千件）を最小限のツール呼び出しで調査・重複排除・整理し、そこに保存・同期されている Obsidian 用 Markdown ノート（ファイル名・YAML Frontmatter・`title`・`aliases`・`tags`・`date`・`type`）を既存 Vault の規約に合わせて最適化するスキルです。

- **段階的ワークフロー**: メタデータによる全体把握 → 候補抽出 → 必要な本文のみ詳細確認 → レビュー可能な整理案の提示 → 承認後の安全な実行
- **安全設計**: 完全削除は行わず承認後にのみゴミ箱へ移動、重複グループから最低1件を保持、実行直前の更新チェック、Obsidian の `[[リンク]]` 破壊防止
- **定期実行対応**: スケジュール実行時は原則として整理案の提案とログ記録のみを実施

### 2. `novel-editor`
商業出版のベテラン編集者として、日本語の小説原稿・改稿・プロット・世界観設定資料を評価・採点・批評するほか、制約付きの文章表現トレーニングや小説専用の誤字脱字・表記ゆれ校正を行うスキルです。

- **採点モード (Scoring mode)**: 7軸（構成・キャラクター・世界観・感情設計・牽引力・独自性・文章）の明確な達成条件に基づく厳格な採点と商業適合性チェック
- **トレーニングモード (Training mode)**: 制約条件を用いた描写・表現力の反復演習と講評
- **誤字チェックモード (Proofreading mode)**: リライトや採点を行わず、誤字・脱字・誤変換・表記ゆれのみを抽出する校正パス
- **作品規模監査モード (Audit mode)**: 長編（複数巻・100万字規模）のシリーズ・アーク単位での構造監査とセッション間引き継ぎデータ管理

---

## インストール方法

### Claude Code（マーケットプレイス経由）

このリポジトリをマーケットプレイスとして追加し、プラグインをインストールできます。

```bash
# マーケットプレイスの追加
claude plugin marketplace add skyvesmir/Sky-Vesmir-s-Skills

# プラグインのインストール
claude plugin install sky-vesmir-skills@sky-vesmir-skills
```

スラッシュコマンドから追加する場合：

```text
/plugin marketplace add skyvesmir/Sky-Vesmir-s-Skills
/plugin install sky-vesmir-skills@sky-vesmir-skills
```

### Claude Code（ローカルディレクトリ指定）

リポジトリをクローンして直接読み込む場合：

```bash
git clone https://github.com/skyvesmir/Sky-Vesmir-s-Skills.git
claude --plugin-dir ./Sky-Vesmir-s-Skills
```

### Claude.ai / Claude Desktop（単体 `.skill` ファイル）

リポジトリ直下に同梱されている `.skill` ファイルを Claude のスキル設定画面から直接アップロードして利用することも可能です。

- `drive-organizer-obsidian-optimizer.skill`
- `novel-editor.skill`

---

## 使い方

プラグインをインストールすると、依頼内容に応じて自動的に各スキルが呼び出されるほか、スラッシュコマンドで明示的に呼び出すこともできます。

- `/sky-vesmir-skills:drive-organizer-obsidian-optimizer`
  - 例：「Google Drive を整理して」「重複ファイルを探して」「Obsidian のファイル名や Frontmatter を見直して」
- `/sky-vesmir-skills:novel-editor`
  - 例：「この原稿を採点・講評して」「表現力のトレーニングのお題を出して」「誤字脱字・表記ゆれだけチェックして」

---

## ディレクトリ構成

```text
Sky-Vesmir-s-Skills/
├── .claude-plugin/
│   ├── plugin.json                              # プラグインマニフェスト
│   └── marketplace.json                         # マーケットプレイスマニフェスト
├── skills/
│   ├── drive-organizer-obsidian-optimizer/
│   │   ├── SKILL.md
│   │   ├── references/
│   │   │   ├── drive-connector.md
│   │   │   ├── obsidian.md
│   │   │   ├── scheduled.md
│   │   │   └── templates.md
│   │   └── scripts/
│   │       └── find_candidates.py
│   └── novel-editor/
│       ├── SKILL.md
│       ├── references/
│       │   ├── audit-mode.md
│       │   ├── expression-training.md
│       │   ├── handoff-format.md
│       │   ├── hook-techniques.md
│       │   ├── proofreading-mode.md
│       │   ├── prose-diagnostics.md
│       │   ├── score-anchors.md
│       │   └── scoring-rubric.md
│       └── scripts/
│           └── check_quotes.py
├── drive-organizer-obsidian-optimizer.skill     # 単体配布用スキルパッケージ
├── novel-editor.skill                           # 単体配布用スキルパッケージ
└── README.md
```
