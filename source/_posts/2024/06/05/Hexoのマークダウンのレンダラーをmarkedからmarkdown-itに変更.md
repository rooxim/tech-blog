---
coauthor: Yuto Uehara
title: Hexoのマークダウンのレンダラーをmarkedからmarkdown itに変更
sitemap: true
categories:
  - 技術
  - Hexo
  - markdown it
tags:
  - node
  - hexo
  - markdown it
  - '@mdit/plugin-img-size'
date: 2024-06-05 03:48:02
---

こんにちは！ROOXIM株式会社COO 上原です。
今回は、マークダウンのレンダラーをmarkedからmarkdown itに変更していこうと思います。
なぜ変更するのかというと、画像をマークダウンで記事を記載した際に画像のサイズを指定できるようにしたいからです。
通常マークダウンでは、画像のサイズを指定することができません。
しかし、markdown itのプラグインを利用することで、画像のサイズを指定できるようにできます。
<!-- more -->
# どうなるの？
通常画像は以下のマークダウンで表示できます。
```markdown
![img](sample_image.png)
```
実際に表示した例は以下です。
![img](sample_image.png)

特にサイズが指定されていません。

しかし以下の様にマークダウンを記載することでサイズを指定できるようになります。
```markdown
![img](sample_image.png =200x)
```
実際に表示した例は以下です。
![img](sample_image.png =200x)
上の例では幅を200pxとしています。
下の例は高さを200pxとしています。
```markdown
![img](sample_image.png =x200)
```
実際に表示した例は以下です。
![img](sample_image.png =x200)

ちなみに高さ幅ともに指定する場合は以下となります。
```markdown
![img](sample_image.png =200x200)
```
実際に表示した例は以下です。
![img](sample_image.png =200x200)

とこんな感じにサイズが指定できるようになります。

# セットアップ
Hexoはデフォルトでhexo-renderer-markedが使われていますので、
hexo-renderer-markedからhexo-renderer-markdown-itに切り替える必要があります。
ではセットアップしていきましょう。

## `hexo-renderer-markdown-it`をインストール
以下のコマンドで`hexo-renderer-markdown-it`をインストールします。
```bash
npm i hexo-renderer-markdown-it --save
```

## `@mdit/plugin-img-size`をインストール
`@mdit/plugin-img-size`は画像のサイズを指定するmarkdown-itのプラグインです。
以下のコマンドで`@mdit/plugin-img-size`をインストールします。
```bash
npm i @mdit/plugin-img-size --save
```

## `hexo-renderer-markdown-it`を設定
以下の設定を`_config.yml`に追加します。

```yaml _config.yml
markdown:
  preset: default
  render:
    html: true
  plugins:
    - name: '@mdit/plugin-img-size'
```

## `hexo-renderer-marked`をアンインストール
`hexo-renderer-marked`がhexoをセットアップした際にインストールされていますが、
`hexo-renderer-markdown-it`と競合するため削除します。
以下のコマンドで`hexo-renderer-marked`をアンインストールします。
```bash
npm remove hexo-renderer-marked
```

# 最後に
以上で画像のサイズが指定できるようになります。
Hexoは何でも出来て便利ですね！
