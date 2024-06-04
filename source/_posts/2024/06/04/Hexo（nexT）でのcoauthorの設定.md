---
coauthor: Yuto Uehara
title: Hexo（nexT）でのcoauthorの設定
sitemap: true
categories:
  - 技術
  - Hexo
tags:
  - node
  - hexo
  - github
date: 2024-06-04 15:28:23
---

こんにちは！ ROOXIM株式会社COO 上原です。
今回は記事を書く際に著者が誰だれなのか記事単位で追加したいと思います。
Hexoでは一般的に記事に著者を追加することができませんが、
nexTテーマ向けでは著者を追加することができるようになります。
<!-- more -->

# どうなるか？
こうなります。
![img](image.png =x200)

記事を書く際には、以下のようにFront Matterに`coauthor`を追加します。
```diff
---
+ coauthor: Yuto Uehara
title: test
---
```

# セットアップ方法
ではセットアップをしていきましょう。
この方法は前提としてnexTのテーマを利用さている必要があります。
nexTは前回の記事で記載されているのでそちらを参照ください。
[Hexoのカスタマイズ-テーマインストール編](/2024-05-31-Hexoのカスタマイズ-テーマインストール編)

## `hexo-next-coauthor`をインストール
まずは、`hexo-next-coauthor`を以下のコマンドでインストールしましょう。
```bash
npm install theme-next/hexo-next-coauthor --save
```

## (任意)設定の追加
インストールしただけで著者が表示されるようになります。
これに加えて設定をすることで著者のリンクを追加することが可能です。
設定は、`_config.next.yml`に以下を追加します。
ここでは、例として弊社で利用している設定を示します。
```yaml _config.next.yml
coauthors:
  [Yuto Uehara]:
    nick: Yuto Uehara
    link: https://github.com/rooxim-uehara
```

# おまけ
いちいちFront Matterにcoauthorを追加するのは面倒です。
そこでGitのユーザ名を自動で使えるようにます。

## `hexo-git-username-coauthor`をインストール
以下のコマンドで`hexo-git-username-coauthor`をインストールします。

```bash
npm i hexo-git-username-coauthor --save
```

## 使い方
Hexoでは記事を作るとき以下のコマンドを実行すると思います。
```bash
hexo new 記事名
```
このコマンドを実行した際に自動で以下の様にユーザ名が代入されます。
```diff
---
title: 記事名
date: 2016-05-20 16:20
coauthor: Yuto Uehara
---
```

## gitのユーザ名の確認と変更方法
gitのユーザ名は以下のコマンドで確認できます。
```bash
git config --global user.name
```

また変更したい場合は以下のコマンドで変更可能です。
```bash
git config --global user.name "Yuto Uehara"
```

# 最後に
以上で記事に著者が設定できました。
あとは著者一覧の画面があると便利なのですが、これはまだプラグインが無いようです。
（ほしいなら作れという話ですが。。。）
作れそうでしたら作ってみたいと思います！
