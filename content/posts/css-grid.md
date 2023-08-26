---
title: "CSSグリッドレイアウトを完全に理解したい"
date: 2023-08-26
draft: true
---

今回は以下のドキュメントを参考に、勉強していく。

[グリッドレイアウトの基本概念](https://developer.mozilla.org/ja/docs/Web/CSS/CSS_grid_layout/Basic_concepts_of_grid_layout)

## グリッドレイアウトとは？

- CSSグリッドレイアウトは、Webページの要素を2次元のグリッド（行と列）上に配置するための新しいレイアウトシステム。
- Flexboxが1次元のレイアウトシステム（行または列のどちらか1つ）であるのに対し、グリッドは2次元のレイアウトシステム。
- フレックスボックスよりも柔軟にレイアウトを作ることが可能。

## グリッドとは？

### グリッドコンテナ

- グリッドは、列と行を定義する水平線と垂直線の集合が交差したものです。要素をグリッド上の行と列の中に配置することができます。 CSS グリッドレイアウトには次のような特徴があります。
- グリッドコンテナーを作成するには、要素に対して `display: grid` か `display: inline-grid` を指定すればいい。

### グリッドアイテム

- グリッドコンテナの直接の子要素。

## 基本的なプロパティ

### grid-template-rows / grid-template-columns

- グリッドの行と列のサイズを定義します。例: `grid-template-columns: 200px 1fr 2fr;`

### grid-gap / row-gap / column-gap

- グリッドアイテム間のギャップを定義します。

### grid-row / grid-column

- グリッドアイテムの開始と終了の位置を定義します。

```html
<div class="wrapper">
  <div>One</div>
  <div>Two</div>
  <div>Three</div>
  <div>Four</div>
  <div>Five</div>
</div>
```

上記で定義したwrapperをグリッドコンテナー化する。

```css
.wrapper {
  display: grid;
}
```

現状これだけでは、特に見た目上の変化は起こらない。
