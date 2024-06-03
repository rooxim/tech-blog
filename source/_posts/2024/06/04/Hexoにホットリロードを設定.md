---
title: Hexoにホットリロードを設定
sitemap: true
categories:
  - 技術
  - Hexo
tags:
  - node
  - hexo
  - github
coauthor: Yuto Uehara
date: 2024-06-04 01:24:00
---


こんにちは！ ROOXIM株式会社COO 上原です。
今回は記事を書く際に便利な機能を紹介させていただきます。
具体的にはHexoでのホットリロードの方法をご紹介します。

<!-- more -->
# ホットリロードとは
まずはホットリロードの概念です。
ホットリロードについて検索すると以下の様に書かれています。

ホットリロード（Hot Reload）とは、開発中にコードを変更してもアプリを再起動することなく、リアルタイムなプレビューが可能な機能です。
「ホット」は「実行中の／アクティブな」という意味で、「リロード」には「再読み込み」という意味があります。

とのことで簡単に言ってしまうと、マークダウンを編集すると自動でブラウザを更新してくれるものとなります。


# どうなるの？
1. サーバを起動
サーバを起動します。
```bash
hexo s --draft
```

起動すると画像の様に裏で`Browsersync`が起動します。
![img](boot.png =350x)

記事を更新すると以下のようになります。
![img](image.gif =x350)

編集して保存するだけなので、ブラウザにフォーカスする必要が無いので楽に編集ができます。

# セットアップ方法
では実際にホットリロードができるように`hexo-browsersync`をインストールしてみましょう。

## `hexo-browsersync`をインストール
以下のコマンドで`hexo-browsersync`をインストールします。

```bash
npm i hexo-browsersync --save
```

## `hexo-browsersync`を設定
以下の設定を`_config.yml`に追加します。
```yaml _config.yml
browsersync:
  logLevel: "warn"
  ghostMode:
    scroll: true
```
その他のオプションは https://browsersync.io/docs/options/ を参照してください。

以上で設定完了です。
ホットリロードで楽しく記事を書いてください！
