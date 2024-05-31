---
title: Hexoのカスタマイズ:テーマインストール編
date: 2024-05-31 22:59:15
categories:
  - 技術
  - Hexo
  - nexT
coauthor:
  - Yuto Uehara
tags:
  - node
  - hexo
  - github
  - nexT
---
ROOXIM株式会社COO 上原です。
前投稿では、Hexoのセットアップが完了しました。
Hexoではデフォルトでlandscapeというテーマが設定されています。
landscapeのテーマでもいいのですが、もう少しいろいろカスタマイズしたい。
そこでテーマの変更とテーマのカスタマイズをしていこうと思います。
<!-- more -->

# テーマの変更
まずはテーマを選びましょう。
ここでは`NexT`というプラグインに変更していきます。

## nexTのテーマをインストール
以下のコマンドでnexTをインストールします。
```bash
npm i hexo-theme-next --save
```


## NexTの設定
NexTの設定ファイルを編集して、HexoプロジェクトでNexTテーマを有効にします。
プロジェクトのディレクトリ直下にある`_config.yml`ファイルを開いて、以下のように設定します。

```yaml
theme: next
```
※インストールしたばかりだと、`theme: landscape`となっていると思います。


## nexT用の設定ファイルのコピー
以下のコマンドでnexTの設定ファイルをプロジェクト直下にコピーします。
```bash
cp node_modules/hexo-theme-next/_config.yml _config.next.yml
```

## (任意)不要なlandscapeのテーマを削除
以後landscapeテーマを利用しない場合、以下のコマンドでlandscapeのテーマを削除します。

```bash
rm _config.landscape.yml
npm remove hexo-theme-landscape
```

## サーバーの起動
Hexoサイトをローカルでプレビューするには、以下のコマンドを実行してHexoサーバーを起動します。
```bash
hexo server
```

## ブラウザで確認
ブラウザで `http://localhost:4000` にアクセスしてテーマが変わっていることを確認します。


以上でnexTのインストールができました。
次回はnexTの設定をしていきたいと思います。
