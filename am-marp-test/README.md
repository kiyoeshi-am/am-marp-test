# AM Marp Test

AlgomaticのMarpを使用したプレゼンテーション作成システムです。Markdownファイルから美しいプレゼンテーションPDFを生成できます。

## 📋 概要

このプロジェクトは、Algomaticのプレゼンテーション資料作成を効率化するためのシステムです。`/input`にMarkdownファイルを配置し、Claude Codeで自動的にスライド化します。

### 特徴
- **Markdown記法**: シンプルなMarkdownでプレゼンテーション作成
- **自動スライド化**: Claude Codeによる自動変換
- **カスタムテーマ**: ブランドカラーに合わせた専用テーマ
- **構造テンプレート**: 再利用可能なスライド構造
- **SCSS管理**: 効率的なスタイル管理

## 🚀 セットアップ

### 前提条件
- Node.js (v16以上)
- npm または yarn

### インストール
```bash
# リポジトリをクローン
git clone [repository-url]
cd am-marp-test

# 依存関係をインストール
npm install
```

## 📁 プロジェクト構造

```
am-marp-test/
├── themes/                    # テーマファイル
│   ├── theme_Algomatic.scss  # グローバルスタイル
│   └── partials/             # スタイルパーシャル
│       ├── _utility.scss     # ユーティリティ関数
│       ├── _company.scss     # ブランドカラー
│       └── _structure.scss   # 構造テンプレート
├── input/                    # 入力Markdownファイル（集約対象）
│   ├── presentation-1.md     # プレゼンテーション1
│   ├── presentation-2.md     # プレゼンテーション2
│   └── company-profile.md    # 会社プロフィール
├── output/                   # 出力PDFファイル（日付・テーマ付き）
│   ├── 2024-01-15_Algomatic_presentation-1.pdf
│   ├── 2024-01-15_Algomatic_presentation-2.pdf
│   └── 2024-01-15_Algomatic_company-profile.pdf
├── template_structure.md     # 構造テンプレート
├── CLAUDE.md                 # 開発ルール
└── README.md                 # このファイル
```

## 🎨 テーマ構成

### グローバルスタイル (theme_Algomatic.scss)
- ヘッダー・フッター
- 基本タイポグラフィ
- テーブルスタイル
- ユーティリティクラス

### パーシャルファイル
- **_utility.scss**: 関数・変数・ミックスイン
- **_company.scss**: ブランドカラー・ロゴ設定
- **_structure.scss**: 構造テンプレート専用スタイル

## 📝 使用方法

### 1. プレゼンテーション作成ワークフロー

```bash
# 1. inputディレクトリにMarkdownファイルを作成
cp template_structure.md input/my-presentation.md

# 2. Markdownファイルを編集（純粋なMarkdown記法）
code input/my-presentation.md

# 3. Claude Codeで自動スライド化と集約
# - ファイル構造の最適化
# - スタイルの適用
# - PDF生成（日付付きファイル名）
# - 全inputファイルの一括処理
```

### 2. Markdownファイルの構造

```markdown
---
marp: true
theme: theme_Algomatic
---

# タイトルスライド
{:.title-slide}

![ロゴ](logo.png)

![登壇者](speaker.jpg)
**役職名**
**名前**

---

# 目次
{:.toc-slide}

1. 項目1
2. 項目2
3. 項目3

---

# 章タイトル
{:.chapter-slide}

## セクション1

内容をここに記載

## セクション2

- リスト項目1
- リスト項目2
- リスト項目3
```

### 3. Claude Codeでの自動処理

Claude Codeは以下の処理を自動で実行します：

1. **ファイル構造の最適化**
   - 純粋なMarkdown構造への変換
   - 不要なHTMLタグの削除
   - セクション名の統一

2. **スタイルの適用**
   - ブランドカラー関数の使用
   - レスポンシブレイアウトの調整
   - グローバル・ローカルスタイルの分離

3. **PDF生成と集約**
   - Marpによる自動変換
   - 日付付きファイル名での出力
   - 出力ファイルの整理

### 4. 出力ファイル

```bash
# 生成されるファイル
output/
├── 2024-01-15_Algomatic_my-presentation.pdf      # 日付・テーマ付きPDF
├── 2024-01-15_Algomatic_my-presentation.html     # 日付・テーマ付きHTML
└── 2024-01-15_Algomatic_company-profile.pdf      # 日付・テーマ付きPDF
```

## 🎯 開発ルール

詳細な開発ルールは [CLAUDE.md](./CLAUDE.md) を参照してください。

### 重要な原則
- **スタイル分離**: スタイルはSCSS、構造はMarkdown
- **ファイル分離**: グローバルとローカルを明確に分離
- **ブランドカラー**: 関数を使用したカラー管理
- **純粋なMarkdown**: HTMLタグの使用を最小限に
- **自動化**: Claude Codeによる自動スライド化

### Claude Codeの役割
- **入力ファイルの最適化**: `/input`のMarkdownファイルを自動処理
- **スタイルの統一**: ブランドカラーとレイアウトの一貫性確保
- **品質管理**: 開発ルールに従った自動チェック
- **ファイル集約**: 全inputファイルの一括処理
- **日付管理**: 出力ファイル名への日付自動付与

## 🎨 カスタマイズ

### ブランドカラーの変更
`themes/partials/_company.scss` を編集：

```scss
// ブランドカラー定義
$navyblue: (
  50: #f0f4f8,
  100: #d9e2ec,
  // ... 他の色階
  950: #1a365d
);
```

### 新しい構造テンプレートの追加
1. `template_structure.md` を参考に新しいテンプレートを作成
2. `themes/partials/_structure.scss` にスタイルを追加
3. セクション名でスタイルを指定

## 📚 利用可能なセクション

### 基本セクション
- `title-slide`: タイトルスライド
- `toc-slide`: 目次スライド
- `chapter-slide`: 章タイトルスライド

### 構造テンプレート専用
- `cover.presentation`: 登壇資料系表紙
- `cover.company-deck`: 会社資料系表紙
- `three-column`: 3カラムレイアウト

## 🔧 トラブルシューティング

### よくある問題

#### スタイルが適用されない
1. ファイル読み込み順序を確認
2. セクション名が正しいか確認
3. SCSSファイルが正しくコンパイルされているか確認
4. Claude Codeの自動処理が正常に実行されているか確認

#### カラーが反映されない
1. ブランドカラー関数の名前・引数を確認
2. `_company.scss` が正しく読み込まれているか確認
3. Claude Codeによる自動変換で関数が正しく適用されているか確認

#### レイアウトが崩れる
1. レスポンシブ対応を確認
2. 画像サイズ・配置を確認
3. ブラウザ開発者ツールでスタイル確認
4. Claude Codeによる自動レイアウト調整を確認

#### Claude Codeの自動処理が動作しない
1. `/input`ディレクトリのファイル構造を確認
2. Markdownファイルの形式が正しいか確認
3. 開発ルール（CLAUDE.md）に従っているか確認
4. 日付フォーマットが正しいか確認

#### ファイル集約が正常に動作しない
1. `/input`ディレクトリ内の全Markdownファイルを確認
2. ファイル名の重複がないか確認
3. 出力ファイル名の日付フォーマットを確認

### 解決手順
1. ブラウザ開発者ツールでスタイル確認
2. ファイル読み込み順序を確認
3. 関数・変数の定義を確認
4. Claude Codeの自動処理ログを確認
5. 必要に応じてルールを更新

## 🤝 貢献

1. このリポジトリをフォーク
2. 機能ブランチを作成 (`git checkout -b feature/amazing-feature`)
3. 変更をコミット (`git commit -m 'Add amazing feature'`)
4. ブランチにプッシュ (`git push origin feature/amazing-feature`)
5. プルリクエストを作成

## 📄 ライセンス

このプロジェクトは [ライセンス名] の下で公開されています。

## 📞 サポート

問題や質問がある場合は、[Issue](../../issues) を作成してください。

---

**注意**: このプロジェクトは開発中のため、仕様が変更される可能性があります。
