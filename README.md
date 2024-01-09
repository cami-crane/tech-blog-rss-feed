# <img src="src/site/images/icon-transparent.png" height=26> 必要の部屋 〜企業テックブログRSS
必要の部屋は企業のテックブログの更新をまとめたRSSフィードを配信しています。  
記事を読んでその企業の技術・カルチャーを知れることや、質の高い技術情報を得られることを目的とし、slackと連携することを前提としています。  
あなたにとって必要な情報が得られますように。

https://cami-crane.github.io/tech-blog-rss-feed/  

[@yamadashy](https://github.com/yamadashy)さんの作成された[yamadashy/tech-blog-rss-feed](https://github.com/yamadashy/tech-blog-rss-feed)をベースにカスタムしております。

## サイト追加の方針
企業のテックブログ（技術ブログ、エンジニアブログ）であれば、基本的には追加します。  
所属企業で運営してるため、記事の内容は勝手に変更されることがあります。  
需要があればフロントエンドやバックエンド、デザインなどの領域に特化したまとめフィードを作成する予定です。

### プルリクでの送り方
もしプルリクを送っていただける場合は以下のように作成できます。

1. このリポジトリをフォーク
2. ブランチ作成  
   `git checkout -b new-blog-feed-xxx`
3. フィードを追加  
   `src/resources/feed-info-list.ts` の `FEED_INFO_LIST` を更新
4. コミット  
   `git commit -am 'add: 新規フィード追加`
5. プッシュ  
   `git push origin new-blog-feed-xxx`
6. プルリクを作成

## 開発

### 仕組み
GitHub Actions で定期的に更新されており、サイトの生成は [Eleventy](https://www.11ty.dev/) を使用しています。

更新は多少遅延ありますが以下のタイミングで行います。
- 平日 8時-24時の1時間おき
- 休日 8時-24時の2時間おき

### フォークして使う場合
以下を書き換えると独自のサイトが動きます。

- `src/common/constants.js` の URL など
- `src/resources/feed-info-list.ts` のブログ情報

### 開発環境とコマンド
環境
- Node.js >= 20  

voltaでnodeとyarnのバージョンをピン留め
```
"volta": {
   "node": "20.10.0",
   "yarn": "1.18.0"
}
```

パッケージのインストール
```bash
$ yarn
```


フィード生成とサイト立ち上げ
```bash
$ # フィードを取得して作成
$ yarn feed-generate

$ # localhost:8080 で確認
$ yarn site-serve
```

コードのチェック
```bash
$ # lint
$ yarn lint

$ # TypeScript のチェック
$ yarn type-check

$ # テスト
$ yarn test
```

## ライセンス
MIT
