# AGENTS.md 標準テンプレート（Geolonia版）

> このファイルは、OpenAI Codex および AGENTS.md 対応AIコーディングエージェント向けの設定ファイルです。
> プロジェクトのルートディレクトリに配置してください。

---

## プロジェクト概要

<!-- プロジェクトの簡潔な説明を記載 -->

**プロジェクト名**: [プロジェクト名]

**説明**: [プロジェクトの目的・概要を1-2文で記載]

**主要技術**:
- フロントエンド: [例: HTML/CSS, React, Vue.js]
- バックエンド: [例: Node.js, Python, Go]
- インフラ: [例: AWS, GCP, Vercel]
- 地図: [例: Geolonia Maps, MapLibre GL JS]

---

## コーディング規約

### 全般

- インデントはスペース2つを使用
- ファイル末尾には改行を入れる
- 日本語コメントを推奨（公開ライブラリは英語）
- コミットメッセージは日本語または英語（プロジェクトに応じて統一）

### HTML

- セマンティックな要素を適切に使用（header, main, footer, article, section等）
- アクセシビリティに配慮（alt属性、aria-label等）
- 画像にはloading="lazy"を付与

### CSS

- CSS変数を活用してカラースキーム・サイズを管理
- モバイルファーストのレスポンシブ設計
- BEM記法またはユーティリティファーストを採用（プロジェクトに応じて）

### JavaScript/TypeScript

- TypeScriptを推奨
- ESLint/Prettierの設定に従う
- 非同期処理はasync/awaitを使用

---

## ディレクトリ構成

```
project-root/
├── AGENTS.md           # 本ファイル（Codex設定）
├── README.md           # プロジェクト説明（人間向け）
├── docs/               # ドキュメント
│   └── specification.md  # 仕様書
├── src/                # ソースコード
│   ├── index.html
│   ├── css/
│   └── js/
├── tests/              # テストコード
└── .github/            # GitHub設定
    └── workflows/      # GitHub Actions
```

---

## 開発ワークフロー

### ブランチ戦略

- `main`: 本番環境、直接コミット禁止
- `develop`: 開発統合ブランチ
- `feature/*`: 機能開発ブランチ
- `fix/*`: バグ修正ブランチ

### コミット前の確認

```bash
# リント実行
npm run lint

# テスト実行
npm test

# ビルド確認
npm run build
```

### プルリクエスト

- PRタイトルは変更内容を簡潔に
- 関連するIssue番号を記載
- レビュアーを1名以上指定

---

## Geolonia固有のルール

### 地図関連

- Geolonia Maps APIを使用する場合は、APIキーを環境変数で管理
- Static Image APIのURL形式: `https://api.geolonia.com/dev/static-map?marker=off&lat={緯度}&lng={経度}&zoom={ズーム}&width={幅}&height={高さ}`
- 座標系はWGS84（EPSG:4326）を使用

### セキュリティ

- APIキー、シークレットはコードに直接記載しない
- 環境変数または.envファイルで管理（.envは.gitignoreに追加）
- 機密情報を含むファイルはコミット前に確認

### ドキュメント

- 仕様書は`docs/specification.md`に配置
- 実装変更時は仕様書も更新すること
- READMEには最低限のセットアップ手順を記載

---

## AIエージェントへの指示

### 実装時のルール

1. **仕様書を最初に確認**: `docs/specification.md`がある場合は必ず読んでから実装
2. **確認してから実装**: 不明点がある場合は実装前に確認を求める
3. **段階的に進める**: 大きな変更は小さなステップに分割
4. **テストを意識**: テスト可能なコードを書く
5. **コミットは適切な粒度**: 1つの論理的な変更を1コミットに

### 禁止事項

- 本番環境のAPIキーやシークレットの出力
- mainブランチへの直接コミット
- 未確認の破壊的変更
- ライセンス違反となるコードの使用

### 推奨事項

- 変更内容の要約を日本語で説明
- エラー発生時は原因と対処案を提示
- 外部APIを使用する前にドキュメントを確認
- コード品質を意識（可読性、保守性、パフォーマンス）

---

## 環境固有の設定

### ローカル開発

```bash
# 依存関係のインストール
npm install

# 開発サーバー起動
npm run dev

# ビルド
npm run build
```

### 環境変数

| 変数名 | 説明 | 例 |
|--------|------|-----|
| GEOLONIA_API_KEY | Geolonia Maps APIキー | YOUR_API_KEY |
| NODE_ENV | 実行環境 | development / production |

---

## トラブルシューティング

### よくある問題

1. **画像が表示されない**
   - APIキーの設定を確認
   - URLの形式を確認
   - ネットワーク接続を確認

2. **ビルドエラー**
   - `npm install`を再実行
   - Node.jsのバージョンを確認
   - キャッシュをクリア: `npm cache clean --force`

3. **地図が表示されない**
   - Geolonia APIキーの有効性を確認
   - ドメイン制限の設定を確認

---

## 連絡先・参考資料

- **チームSlack**: #dev-ai-tools
- **Geolonia Maps ドキュメント**: https://docs.geolonia.com/
- **社内Wiki**: [URL]

---

## 更新履歴

| 日付 | 版 | 内容 |
|------|-----|------|
| 2026/01/26 | 1.0 | 初版作成 |

---

<!-- 
このテンプレートはGeolonia組織でのAI開発ツール利用を標準化するために作成されました。
プロジェクトの特性に応じてカスタマイズしてください。

参考:
- AGENTS.md 公式ドキュメント: https://agents.md/
- OpenAI Codex AGENTS.md ガイド: https://developers.openai.com/codex/guides/agents-md
-->
