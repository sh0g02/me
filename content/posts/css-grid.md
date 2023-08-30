---
title: "CSSグリッドレイアウトを完全に理解したかった"
date: 2023-08-31
draft: false
---

## グリッドレイアウトとは？

- 「行列」を使ったレイアウトシステム。
- CSSグリッドレイアウトは、Webページの要素を2次元のグリッド（行と列）上に配置する。
- Flexboxが1次元のレイアウトシステム（行または列のどちらか1つ）であるのに対し、グリッドは2次元のレイアウトシステム。
- フレックスボックスよりも柔軟にレイアウトを作ることが可能。

## グリッドとは？

### グリッドコンテナ

- グリッドアイテム（子要素）のラッパー。
- グリッドコンテナーを作成するには、要素に対して `display: grid` か `display: inline-grid` を指定すればいい。

### グリッドアイテム

- グリッドコンテナの直接の子要素。グリッドコンテナ内に並んでいる要素は自動的にグリッドアイテムとして扱われる。 そのため、明示的にCSSを設定する必要はない。

## 簡単なサンプル

```html
<div class="wrapper">
  <div class="one">One</div>
  <div class="two">Two</div>
  <div class="three">Three</div>
  <div class="four">Four</div>
  <div class="five">Five</div>
  <div class="six">Six</div>
</div>
```

上記で定義したwrapperをグリッドコンテナー化する。

```css
.wrapper {
  display: grid;
}
```

現状これだけでは、特に見た目上の変化は起こらない。

ここからグリッドをどのように見せたいか、定義していく。

### グリッドの列と行

レイアウトを二次元化するためには、グリッドの列（カラム）と行（ロウ）を定義する必要がある。

以下は3つの列と2つの行を作っている。

```css
.wrapper {
  display: grid;
  grid-template-columns: 100px 100px 100px; /* 列を3カラムに指定して、それぞれの列幅を指定 */
  grid-template-rows: 50px 50px; /* 行を2に指定して、それぞれの行幅を指定 */
}
```

そうすると、グリッドのサイズは列が100px, 行が50pxになる。

```css
.wrapper {
  display: grid;
  grid-template-columns: 200px 50px 100px;
  grid-template-rows: 100px 30px;
}
```

この場合もどうなるか想像して見よう。

### グリッドアイテムの配置

次にグリッドにアイテムを配置する方法を見ていく。

```css
.one {
    background-color: burlywood;
    grid-column-start: 1;
    grid-column-end: 4;
    grid-column: 1 / 4; /* start ~ end のショートハンド */
}
```

グリッドアイテムoneを最初のグリッドラインから開始して、4番目のグリッドのラインで終了すると指定。

これにより、oneは親要素の横方向いっぱいに広がる。

さらに以下のように指定してみよう。

```css
.one {
    background-color: burlywood;
    grid-column: 1 / 3;
}
.three {
    background-color: cadetblue;
    grid-row: 2 / 4;
}
.four {
    background-color: cornflowerblue;
    grid-column: 2 / 4;
}
```

### 全体のサンプル

```html
<div class="wrapper">
    <div class="one">One</div>
    <div class="two">Two</div>
    <div class="three">Three</div>
    <div class="four">Four</div>
    <div class="five">Five</div>
    <div class="six">Six</div>
</div>

<style>
.wrapper {
    display: grid;
    grid-template-columns: 100px 100px 100px;
    grid-template-rows: 100px 100px 100px;
    & div {
        /* h1やpといった要素名のセレクターの場合は、&を使う */
        /*https://zenn.dev/moneyforward/articles/css-nesting-without-sass*/
        color: white;
    }
    .one {
        background-color: burlywood;
        grid-column: 1 / 3;
    }
    .two {
        background-color: teal;
    }
    .three {
        background-color: cadetblue;
        grid-row: 2 / 4;
    }
    .four {
        background-color: cornflowerblue;
        grid-column: 2 / 4;
    }
    .five {
        background-color: darkgrey;
    }
    .six {
        background-color: slateblue;
    }
}

</style>
```
