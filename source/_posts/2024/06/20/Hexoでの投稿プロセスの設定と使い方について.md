---
coauthor: Yuto Uehara
title: Hexoでの投稿プロセスの設定と使い方について
sitemap: true
coauthor: Yuto Uehara
categories:
  - 技術
  - Hexo
tags:
  - node
  - hexo
date: 2024-06-20 19:43:44
---


こんにちは！ROOXIM株式会社COO 上原です。
今回は、Hexoで投稿するまでの流れと設定をご紹介しようと思います。

<!-- more -->

# 基本的な投稿方法
まずは、Hexoのコマンドを確認しておきましょう。

# 記事を作る
まずは以下のコマンドで記事を作ります。
```bash
hexo new <記事名>
```

上記コマンドで記事を作ると、デフォルトの設定だと`source/_posts` に`<記事名>.md`のファイルが作成されます。

または、下記のコマンドで下書きとして`source/_dradts`に`<記事名>.md`のファイルが作成されます。
```bash
hexo new draft <記事名>
```
draftで作成された`<記事名>.md`に記事を書いた後、投稿とする際は以下のコマンドを利用します。
```bash
hexo publish <記事名>
```
以上で記事の作成が完了します。
あとは、実際に公開するためにPushして公開される形となります。

なお、下書きの記事を確認しながら編集する場合、以下のコマンドを利用してローカル環境でサーバを動かすことで
下書き記事を見ながら編集出来ます。

```bash
hexo s --draft
```

`--draft`オプションを利用することで下書きの記事も表示されるようになります。

# 課題
上記の方法では、`source/_posts`以下に記事が並ぶ形となります。
しかし、記事が増えてくると、`source/_posts`以下にどんどんマークダウンファイルが増えていき管理し辛いです。
そこで、以下の画像のようなディレクトリ構造にして投稿日と、記事を関連付けた形にしていこうと思います。

![img](directory.png =x300)

# `source/_posts`のディレクトリ構造の設定
下記の様に`_config.yml`を設定することで、生成されるマークダウンファイルに階層構造をもたせることが可能です。
```diff _config.yml
# Writing
- new_post_name: /:title.md # File name of new posts
+ new_post_name: /:year/:month/:day/:title.md # File name of new posts
default_layout: post
```
あとは基本的な流れで記事を作成するだけです。

# 最後に
これで記事の管理がしやすくなりました。
また便利な機能があれば、ご紹介するかもしれませんが、以上でHexoの記事は終わりにしようと思います。


