---
coauthor: Yuto Uehara
title: Hexoのカスタマイズ:nexTのカスタマイズ
categories:
  - 技術
  - Hexo
  - nexT
tags:
  - node
  - hexo
  - github
  - nexT
sitemap: true
date: 2024-06-01 00:01:19
---


こんにちは！ ROOXIM株式会社COO 上原です。
前回はHexoのテーマであるnexTをインストールしました。
しかしnexTをインストールしただけでは個性があまりありません。
そこでnexTのテーマをカスタマイズしてより見た目にこだわっていきましょう。
ここでは、設定した一部をご紹介させていただいています。
<!-- more -->
# schemeの変更
nexTには4つのschemeが用意されています。

**Muse**
![img](scheme-muse.png =x200)

**Mist**
![img](scheme-mist.png =x200)

**Pisces**
![img](scheme-pisces.png =x200)

**Gemini**
![img](scheme-gemini.png =x200)

_config.next.ymlの`Scheme`のコメントを外して、好きなschemeを選びましょう。

```yaml _config.next.yml
# ---------------------------------------------------------------
# Scheme Settings
# ---------------------------------------------------------------

# Schemes
# scheme: Muse
# scheme: Mist
# scheme: Pisces
scheme: Gemini
```

# ダークモードの有効化
trueにすると、ダークテーマになります。

```yaml _config.next.yml
# Dark Mode
darkmode: true
```

![img](dark.png =x200)

# テーマカラーの変更
theme_colorを変えることでページの色を変更できます。 
HTMLで指定できる色の値で指定が可能です。
（`#222222` , `red`, `rgb(255 0 153)`など）

```yaml _config.next.yml
# Browser header panel color.
theme_color:
  light: "#222"
  dark: "#222"
```

**light: "orange"**
![img](color-orange.png =200x)

**light: "green"**
![img](color-green.png =200x)

**light: "red"**
![img](color-red.png =200x)
