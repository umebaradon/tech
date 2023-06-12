# microcms-blog

サイト: https://blog.microcms.io

## 機能

- 記事一覧
- カテゴリー別記事一覧
- タグ別記事一覧
- 人気の記事一覧
- 最新の記事一覧
- 著者別の記事一覧
- 検索
- パンくずリスト
- 記事詳細
  - 目次
  - 著者
  - SNS シェアボタン
  - 下書きプレビュー
  - 関連記事
- サイトマップ
- バナー
- Google Tag Manager
- Facebook Pixel
- RSS
- PWA

## 技術構成

- Nuxt（SSG）
- microCMS（コンテンツ）
- Netlify（Hosting, Functions）
- ESLint
- Prettier
- PostCSS
- PWA

## microCMS の API スキーマ設定

### ブログ

endpoint: blog  
type: リスト形式

| フィールド ID | 表示名      | 種類                                            |
| ------------- | ----------- | ----------------------------------------------- |
| title         | タイトル    | テキストフィールド                              |
| category      | カテゴリー  | コンテンツ参照 - カテゴリー                     |
| tag           | タグ        | 複数コンテンツ参照 - タグ                       |
| toc_visible   | 目次        | 真偽値                                          |
| body          | 本文        | リッチエディタ                                  |
| description   | 概要        | テキストフィールド                              |
| ogimage       | OGP 画像    | 画像                                            |
| writer        | 著者        | コンテンツ参照 - 著者                           |
| partner       | パートナー  | コンテンツ参照 - パートナー                     |
| previous_blog | 前の記事    | コンテンツ参照 - ブログ                         |
| next_blog     | 次の記事    | コンテンツ参照 - ブログ                         |
| related_blogs | 関連記事    | 複数コンテンツ参照 - ブログ                     |
| cv_point      | CV ポイント | 繰り返し（※上限 1 に設定） - カスタムフィールド |

#### カスタムフィールド

フィールド ID: thumbnail

| フィールド ID | 表示名         | 種類               |
| ------------- | -------------- | ------------------ |
| title         | タイトル       | テキストフィールド |
| text          | 本文           | テキストエリア     |
| buttonText    | ボタンテキスト | テキストフィールド |
| buttonLink    | ボタンリンク   | テキストフィールド |
| thumbnail     | サムネイル     | 画像               |

### 著者

endpoint: authors  
type: リスト形式

| フィールド ID | 表示名       | 種類               |
| ------------- | ------------ | ------------------ |
| name          | 名前         | テキストフィールド |
| text          | 自己紹介     | テキストエリア     |
| image         | 画像         | 画像               |
| twitter       | Twitter URL  | テキストフィールド |
| facebook      | Facebook URL | テキストフィールド |
| github        | GitHub URL   | テキストフィールド |

### カテゴリー

endpoint: categories  
type: リスト形式

| フィールド ID | 表示名 | 種類               |
| ------------- | ------ | ------------------ |
| name          | 名前   | テキストフィールド |

### タグ

endpoint: tags
type: リスト形式

| フィールド ID | 表示名 | 種類               |
| ------------- | ------ | ------------------ |
| name          | 名前   | テキストフィールド |

### パートナー

endpoint: partners  
type: リスト形式

| フィールド ID | 表示名   | 種類               |
| ------------- | -------- | ------------------ |
| company       | 会社名   | テキストフィールド |
| url           | 会社 URL | テキストフィールド |
| description   | 説明文   | テキストエリア     |
| logo          | ロゴ     | 画像               |

### 人気の記事

endpoint: popular-articles  
type: オブジェクト形式

| フィールド ID | 表示名     | 種類                        |
| ------------- | ---------- | --------------------------- |
| articles      | 人気の記事 | 複数コンテンツ参照 - ブログ |

### バナー

endpoint: banner  
type: オブジェクト形式

| フィールド ID | 表示名       | 種類               |
| ------------- | ------------ | ------------------ |
| image         | 画像         | 画像               |
| url           | リンク先 URL | テキストフィールド |
| alt           | 代替テキスト | テキストフィールド |

## 環境変数

プロジェクトルートに`.env`ファイルを作成し、以下の項目を設定してください。

- API_KEY（microCMS の API キー）
- SERVICE_ID（microCMS のサービス ID）
- GTM_ID（Google Tag Manager の ID）※任意
- FB_PIXEL_ID（Facebook ピクセル ID）※任意

例:

```
API_KEY=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
SERVICE_ID=your-service-id
GTM_ID=GTM-xxxxxxx
FB_PIXEL_ID=xxxxxxxxxxxxxxxxxx
```

## 開発方法

```bash
# パッケージをインストール
$ npm install

# 開発サーバーを起動（localhost:3000）
$ npm run dev

# Netlify Functionsをローカルで起動（localhost:9000）
$ npm run functions:serve

# アプリケーションを静的生成
$ npm run generate

# 静的生成したアプリケーションを起動
$ npm start
```

## ライセンス

Apache License 2.0
