---
title: Hexoのセットアップ
date: 2024-05-30 17:08:33
categories:
  - 技術
  - Hexo
coauthor:
  - Yuto Uehara
tags:
  - node
  - hexo
  - github
---

ROOXIM株式会社COO 上原です。
前投稿では、Hexoを選んだ理由について紹介しました。
今回は、セットアップ手順についてご紹介します。
<!-- more -->
なお、技術的なお話になるので時間が経過するとこれから記載する手順ではうまく行かない場合もあると思います。
なので、まずは時期と環境からから紹介します。

# 環境
セットアップは2024/05/30に行いました。
各バージョンは以下となります。

| 項目                      | バージョン                                |
|-------------------------|--------------------------------------|
| node                    | v18.17.1                             |
| hexo-cli                | v4.3.2                               |
| hexo                    | v7.2.0                               |

ちなみに開発環境はMacBook Pro(Apple M1 Max) MacOS 14.4.1(Sonoma)です。

# Hexoのセットアップ手順

## 1. Node.jsのインストール
[Node.jsの公式サイト](https://nodejs.org/)から最新のNode.jsをダウンロードしてインストールします。
※ __パッケージマネージャーからのインストールをおすすめしますが、ここでは簡単な方法として公式のインストーラからインストールする方法としています。__


## 2. Hexo-cliのインストール
ターミナルまたはコマンドプロンプトを開き、次のコマンドを実行します。
```bash
npm install -g hexo-cli
```

## 3. Hexoプロジェクトの作成
先ほどインストールしたHexo-cliを使ってHexoのプロジェクトを作ります。
任意のディレクトリに移動し、新しいHexoプロジェクトを作成します。
```bash
hexo init myblog
```

このコマンドでcurrentディレクトリに`myblog`というフォルダが生成されているはずです。
以降生成された`myblog`内で作業するため、以下のコマンドでディレクトリを移動しておきます。

```bash
cd myblog
```

## 4. パッケージ（ライブラリ）をインストール
Hexoプロジェクトディレクトリ内で、以下のコマンドを使用して必要なパッケージ（ライブラリ）をインストールします。
```bash
npm install
```

## 5. サーバーの起動
Hexoサイトをローカルでプレビューするには、以下のコマンドを実行してHexoサーバーを起動します。
```bash
hexo server
```

## 6. ブラウザで確認
ブラウザで `http://localhost:4000` にアクセスしてHexoサイトを確認します。

## 7. 投稿の作成
新しい投稿を作成するには、以下のコマンドを実行します。
```bash
hexo new "My New Post"
```
これにより、`source/_posts` ディレクトリ内に `My-New-Post.md` という名前のMarkdownファイルが作成されます。

# 初期設定
セットアップは完了しました。
次に基本的な設定をしていきたいと思います。
hexoの基本的な設定は`_config.yml`で変更できます。
ここでは主な変更箇所を紹介します。

## title,subtitle,description,keywords,authorの設定
```yaml _config.yml
title: Hexo
subtitle: ''
description: ''
keywords:
author: John Doe
```
↓
```yaml _config.yml
title: ルークシム技術ブログ
subtitle: ''
description: '「あなたの会社のCTO」ROOXIM株式会社が運営する技術ブログです。業務や、最新の技術について紹介していきます。'
keywords:
  - ルークシム株式会社
  - ROOXIM.inc
  - あなたの会社のCTO
author: ROOXIM.inc
```

## 言語の設定
Hexoの言語設定は、`_config.yml`で変更できます。
下記では、日本語に対応していれば日本語、そうでなければ英語が表示されるようになります。
※記事を日本語で書いている場合、翻訳されるわけではありません。
```yaml _config.yml
language: en
```
↓
```yaml _config.yml
language:
  - ja
  - en
```

## タイムゾーンの設定
タイムゾーンを変更します。
wikiに記載されているタイムゾーンが利用できるらしいです。
https://en.wikipedia.org/wiki/List_of_tz_database_time_zones
日本向けなので `japan`としています。

```yaml _config.yml
timezone: ''
```
↓
```yaml _config.yml
timezone: 'japan'
```

## urlの設定
公開するURLに変更します。

```yaml _config.yml
url: http://example.com
```
↓
```yaml _config.yml
url: https://blog.rooxim.com
```

## 投稿毎に画像などのassetフォルダを分ける
デフォルト設定だと、投稿毎にフォルダが`source/images`以下にすべての画像を置くようになっています。
この設定でもいいですが、投稿が多くなると、すべての画像が1箇所に集まってしまって管理が大変になる可能性があります。
そこで、投稿毎にフォルダを作ってアセットを管理できるようにします。

```yaml _config.yml
post_asset_folder: false
```
↓
```yaml _config.yml
post_asset_folder: true
```

これで`hexo new new-post`とした際に、`new-post.md`といっしょに`new-post`というフォルダが生成される用になります。
しかし、`new-post`フォルダ以下に`img.png`という画像をおいて、マークダウン上で[img](img.png)としてもそのままでは参照できません。

そこで追加で以下の設定を`_config.yml`の最後に追加します。
```yaml _config.yml
marked:
  prependRoot: true
  postAsset: true
```



# 次回: Hexoのカスタマイズ
以上でHexoの基本的なセットアップは完了します。
しかしながら、これではシンプルなブログサイトです。
そこでもっとカスタマイズをしていきたいと思います。

[Hexoのセットアップ:テーマ編](/2024/05/30/20240530002-Hexoのカスタマイズ)

