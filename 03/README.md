---
marp: true
paginate: true
theme: custom
---

<!-- _class: cover -->

<h1 class="logo"><b>CODE</b>_THE_WEB #3</h1>
<p class="title">コードでウェブをつくろう #3</p>
<p class="author">&copy; 2025 Satoshi Soma</p>

---

## 前回のおさらい 1/3
*`style` 属性*
- タグに持たせられる**属性**のひとつ
- そのタグの **見た目（スタイル）** を自由に変更できる
- 書き方:
```html
<タグ名 style="プロパティ: 値">テキスト</タグ名>
```
- プロパティは “**どこ**を変えるか”
- 値は “**どう**変えるか”

---

## 前回のおさらい 2/3
*`<style>` タグ*
- **スタイルシート（CSS）** を記述するための*タグ*
- *CSS* は、**複数のスタイルをまとめて記述する**ための*言語*
- CSS の基本文法:

```html
<style>
  タグ名 {
    プロパティ: 値;
    プロパティ: 値;
    プロパティ: 値;
  }
  /* コメントはこのよう書く */
</style>
```

---

記述例:
```html
<style>
  p {
    /* p タグのスタイル */
    font-size: 16px;
  }
  h1 {
    /* h1 タグのスタイル */
    font-size: 36px;
    color: blue;
  }
</style>
```

---

## 前回のおさらい 3/3
*CSS における色の表現*
- RGB(A) 値:
```css
color: rgb(赤, 緑, 青);          /* 各色: 0 - 255 */
color: rgba(赤, 緑, 青, 不透明度); /* 不透明度: 0.0 - 1.0 */
```
- HSL(A) 値:
```css
color: hsl(色相, 彩度, 明度);          /* 色相: 0 - 360   彩度,明度: 0% - 100% */
color: hsla(色相, 彩度, 明度, 不透明度); /* 不透明度: 0.0 - 1.0 */
```

---

## `class` 属性
- タグに持たせられる**属性**のひとつ
- タグに「**クラス名（分類名）**」を付けることができる
- 「*クラス名*」そのものに*特別な機能はない*が、
  **CSS との組み合わせにおいて極めて重要な役割を持つ**

---

### `class` 属性の書き方:
```html
<タグ名 class="クラス名"> ... </タグ名>
```
```html
<タグ名 class="クラスA クラスB"> ... </タグ名> <!-- スペースを挟んで複数のクラス -->
```
- `クラス名` は基本的にどんな名前でも良いが、**半角英数**が推奨される
- 一つのタグに**複数のクラス名**を付けたい場合は、**スペースを挟んで併記**する

---

### クラス名に対してスタイルを指定する
スタイルシートにおいて、
これまでは以下のように*タグ名*に対してスタイルを指定していた。

```html
<style>
  h1 {
    font-size: 24px;
  }
  p {
    font-size: 16px;
  }
</style>

<h1>見出し (24px)</h1>
<p>段落 (16px)</p>
<p>段落 (16px)</p>
```

---

実はタグ名だけではなく、
**クラス名に対してスタイルを指定**することも可能である。

スタイルの指定先としてクラス名を使用するには、
*`.（ピリオド）` の後にクラス名*を続けて書けばいい。

```html
<style>
  .クラス名 {
    プロパティ: 値;
  }
</style>
```

次に簡単な例を示す。

---

```html
<style>
  .alfa {
    font-size: 48px;
  }
  .bravo {
    font-size: 36px;
  }
</style>
<h1 class="alfa">見出しA (48px)</h1>  <!-- クラス名: alfa -->
<h1 class="bravo">見出しB (36px)</h1> <!-- クラス名: bravo -->
```

<b class="red">`見出しA`</b> と <b class="blue">`見出しB`</b> は**どちらも `<h1>` タグ**だが、
- <b class="red">`見出しA`</b> は `class` 属性が `alfa` なので、<b class="red">`alfa` クラス</b>となる。
- <b class="blue">`見出しB`</b> は `class` 属性が `bravo` なので、<b class="blue">`bravo` クラス</b> だ。

そして CSS によって、クラス <b class="red">`alfa`</b> と <b class="blue">`bravo`</b> それぞれに**異なる文字サイズが割り当てられている**ことに注目してほしい。

---

つまり、タグ名にではなく、*クラス名に対してスタイルを指定*することで、
**タグ名に関係なく自由にスタイルの適用先をコントロールすることができる**。

---

### 演習
[04_class.html](../04_class.html) を `WORKSPACE` フォルダにコピーし、エディタで開こう。
その中のサンプルコードを参考にしながら問題を解いてみよう。

---

## `<div>` と `<span>` タグ
第一回にて、**HTML タグはテキストに特定の役割や機能を与えるもの**だと説明した。
実はこの定義に厳密には当てはまらないタグが二つ存在する。
それが *`<div>`* と *`<span>`* タグである。

---

### `<div>` と `<span>` の特徴
- どちらもタグとしては**特別な機能を持たない**
- `<div>` は **ブロック要素**
- `<span>` は **インライン要素**
- 閉じタグ（ `</div>`, `</span>` ）と 1 セット

---

### 主な用途:
一つ、または複数の HTML 要素（テキストやタグ）を囲むことで、
**一つの要素としてグループ化**する。

感覚的には Adobe Illustrator や Photoshop における**グループ**や**レイヤー**の概念に近い。

<div class="cols gap">
<div>

```html
<!-- バラバラ -->
<h1>見出し</h1>
<p>段落</p>
<p>段落</p>
<p>段落</p>
```

</div>
<div>

```html
<!-- DIV で一まとめに -->
<div>
  <h1>見出し</h1>
  <p>段落</p>
  <p>段落</p>
  <p>段落</p>
</div>
```

</div>
</div>

[05_div-and-span.html](../05_div-and-span.html) をエディターで開き、サンプルコードを見てみよう。

---

## ブロック要素とは
- `<body>`
- `<div>`
- `<h1>`, `<h2>`, `<h3>`, ... `<h6>`
- `<p>`
- `<hr>` など

### 特徴:
- 強制的に改行される（**常に新しい行に挿入される**）
- **内容に関わらず幅が最大**で表示される（スタイルで変更可能）
- レイアウトに大きく影響しやすい

---

## インライン要素とは
- `<span>`
- `<a>`
- `<img>`
- `<strong>` など

### 特徴:
- 勝手に改行されない
- 幅が**内容次第**
- 途中で折り返されることはある
- レイアウトへの影響は少ない

---

## ヘッダーとフッターのあるページを作ってみよう
ウェブサイトによってページのデザインは様々だが、
多くのサイトは大きく分けて

「**ヘッダー**」, 「**メイン**」, 「**フッター**」

と呼ばれる*3つのパーツ*で構成されている。

---

*ヘッダー*は**ページの一番上に位置するパート**で、

- サイトのタイトル
- メニュー
- 検索バー

などの要素を内包していることが多い。
**訪問者が目的のページに迅速にたどり着けるよう案内する**のが主な役割と言えるだろう。

---

*メイン*は**そのページの主要なコンテンツ**を包含するパートだ。
すなわち、**そのページが存在する目的**といえる部分である。

ブログの一記事であれば、記事の見出しから本文までがそれにあたる。

---

*フッター*は**ページの下端に位置するパート**で、

- 著作権表示
- 作者のプロフィール
- サイトの利用規約
- SNS へのリンク

といった、**メインに対する補足的な情報や、その情報へのリンク**を内包していることが多い。

---

`WORKSPACE/index.html` ファイルをエディタで開き、
これらを実際に HTML コードに落とし込んでみよう。
それぞれのパーツは `<div>` として表現し、*クラス名*をつけて区別する。

```html
<!-- ヘッダー -->
<div class="header">
</div>

<!-- メイン -->
<div class="main">
</div>

<!-- フッター -->
<div class="footer">
</div>
```

---

ヘッダーには**サイトのタイトル**を入れよう。
タグは `<span>` で、クラス名には `title` とでも入れておけばわかりやすいだろう。

`<p>` タグで短い紹介文を付け足しておくのもいいだろう。

```html
<!-- ヘッダー -->
<div class="header">
  <span class="title">CODE_THE_WEB Blog</span>
  <p>コードでウェブ制作を学ぶブログ</p>
</div>
```

ちなみに、現段階では**見た目は気にしなくていい**。
*スタイルは後から調整*すれば良いので、
今は **HTML の構造**のみに気を配ろう。

---

メインには*ページの主要コンテンツ*を入れる。
ブログの記事ページなら記事の**見出し**と**本文**がそれにあたる。

```html
<!-- メイン -->
<div class="main">
  <h1>HTML の文法</h1>
  <p>HTML の文法はタグを最小単位として成り立っている。</p>
  <p> ... </p>
</div>
```

また、すでに書き途中のコンテンツがあるのなら、
**メインの中にまるごと移動**させてしまうといいだろう。

---

フッターには作者である自分の**プロフィール**を載せてみよう。

ただし、プロフィールとは往々にして**様々な種類の情報**から
成り立っているものである。<small>（例: 写真, 名前, 職業, 経歴 など）</small>

それらの情報は、*専用の `<div>` タグの中にまとめられるべき*だろう。
クラス名はわかりやすく `profile` としておく。

```html
<!-- フッター -->
<div class="footer">

  <!-- プロフィール -->
  <div class="profile">
  </div>

</div>
```

---

あとは `<div class="profile">` の中に、
載せたいプロフィール情報を入れていけばいい。

個々のタグが**どういう種類の情報**なのかを明確にするために、
**適切なクラス名**を与えることも忘れずに。

```html
<!-- フッター -->
<div class="footer">

  <!-- プロフィール -->
  <div class="profile">
    <p class="name">Satoshi Soma</p>   <!-- 名前 -->
    <img class="pic" src="my-pic.png"> <!-- 写真 -->
    <p class="job">ウェブデザイナー</p>   <!-- 職業 -->
  </div>

</div>
```

---

最後にコピーライト（著作権表記）を書き加えて締めくくろう。

```html
<!-- フッター -->
<div class="footer">

  <!-- プロフィール -->
  <div class="profile">
    （省略）
  </div>

  <!-- コピーライト -->
  <p class="copyright">
    CODE_THE_WEB Blog © 2022 Satoshi Soma
  </p>

</div>
```

---

**スタイルシートを別ファイルにする**
- スタイルシートは、 `<style>`タグだけではなく **`.css`ファイル** にも書くことができる
- **`<link>`タグ** で、HTMLファイルから `.css`ファイルを**読み込ませる**ことができる
- `<link>` の書き方:
```html
<head>
    <link rel="stylesheet" href="CSSファイルへのパス">
</head>
```
- 一つの `.css`ファイルを複数のページ (HTML) から読み込ませれば、
**サイト全体でスタイルを共通化**できる

