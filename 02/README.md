---
marp: true
theme: default
paginate: true
---

# { CODE_THE_WEB #2 }
コードでウェブをつくろう #2

---

## 前回のおさらい 1/4
- あらゆるウェブページは基本的に **HTML コード**でできている
    - 画像や動画などの素材は、**ページを構成する部品**にすぎない
    - 部品をただ並べるだけではサイトはできない
    - 部品を**正しく構成**し、サイトとして組み上げるのが **HTML コード**の役割
- HTML コード（ページのナカミ）は、
ブラウザの**開発者ツール `alt + cmd + I`** で覗ける

---

## 前回のおさらい 2/4
- どんな**言語**（日本語, 英語, 中国語など）にも必ず**文法というルール**が存在する
- **HTML コード**とは、**HTML という言語**の文法に従って書かれたテキスト（文字情報）
- HTML の文法は、様々な種類の **タグ (tag)** で成り立っている
- タグはこういうやつら:
    - `<html>`, `<head>`, `<body>`, `<h1>`, `<p>` (他にも沢山あるよ)

---

## 前回のおさらい 3/4
- タグの書き方:
    - `<タグ名>テキスト</タグ名>`
    - `</タグ名>` これは**閉じタグ**。（スラッシュに注目）
    - タグと閉じタグは**ワンセット**になっている。（例外あり）
    - タグと閉じタグで**囲まれたテキスト**に対して、
    何らかの**意味**や**機能**を付与することができる。

基本的なタグの用例については [`01_tags.html`](01_tags.html) のコードを参照してください。

---

## 前回のおさらい 4/4
- タグには **属性 (attribute)** を持たせることができる。
- 属性とは、タグに与える**付加的な情報**。パラメタ。
- 属性の書き方:
    - `<タグ名 属性名="属性値">`

例1: `<a>`タグと `href`属性を使った**リンク**の付け方:
```html
<a href="リンク先のURL">リンクテキスト</a>
```

例2: `<img>`タグと `src`属性を使った**画像**の置き方:
```html
<img src="画像へのパス">
```

その他用例については [`02_attributes.html`](02_attributes.html) のコードを参照してください。

---

## :sparkles:  style 属性ってすごい
- **どんなタグ**にも持たせることができる
- そのタグで囲まれた部分の**見た目**を自由にいじれる

---

## style 属性の書き方
```html
<タグ名 style="プロパティ: 値">テキスト</タグ名>
```

- `プロパティ` とは、**フォントサイズ**や**文字色**といった、
**見た目のどの部分**を変えたいかを指定するためのものです。
- `値` は、その部分を**どの程度変えたいか**を指定するものです。

[`03_style-attrib.html`](03_style-attrib.html) をブラウザで開いてみましょう。
開発者ツール `alt + cmd + I` でコードを確認することも忘れずに。

---

## 試しに自分で色々書いてみよう
[`03_style-attrib.html`](03_style-attrib.html) を参考にしながら、
[`index.html`](index.html) を編集して、**スタイルをカスタマイズした見出し**を作ってみよう。

---

## でも…
"スタイルを変えたいタグ**全部**に対して、
**いちいち `style="****"` って書く**の大変じゃない？"

"ぶっちゃけ**めんどくね**？"

って思ったひと

---

## :sparkles: エライッ :relaxed::sparkles:

---

"**面倒くさい**" を解決するためにテクノロジーは進歩するもの。
これにもちゃんと解決法があります。

---

## <style> タグ
- **スタイルを指定したいタグ** と **プロパティ**, そしてその **値** を
**セットで記述**するためのタグ
- `<style>` タグ内に記述したスタイルは、
**そのページ内の複数のタグ**に対してまとめて適用可能

---

## <style> タグ、及びスタイルシートの書き方
`<style>`タグと閉じタグ`</style>` の間にスタイルを記述する。
ただし、その記述に用いられる文法は **スタイルシート** という独自の言語に従うものとなる。

---

### スタイルシートの基本文法
```html
タグ名 {
    プロパティA: 値;
    プロパティB: 値;
    プロパティC: 値;
}
別のタグ名 {
    (同上)
}
```
ここからは体系的な説明を省き、
実際の記述例を示しながら解説を挟んでいこうと思います。

---

### スタイルシートの記述例1:
```html
<style>
    h1 {
        font-style: italic;
        font-size: 32px;
        color: red;
    }
</style>
```
このスタイルシートを解説すると、
- `<h1>` タグに対して:
    - フォントをイタリックに
    - フォントサイズを 32px に
    - 文字色を 赤 (red) に

というスタイルを当てています。
重要なのは、これが**ページ内の全ての `<h1>` タグ**に適用されるという点です。

---

### 表示を確認してみよう
先ほど示した `<style>`タグ、及びスタイルシートを、
`index.html` 内の **`<body>`タグのすぐ下** にコピペしてください。

```html
    <body>
        <style>
            h1 {
                font-style: italic;
                font-size: 32px;
                color: red;
            }
        </style>

        (省略)

    </body>
```

上のようなコードになったら、**試しに `<h1>`の見出しをいくつか書いてみて**、
表示がスタイル通りになっているかを確認してみましょう。

---

### ちなみに
エディタ (VS Code) 上で **字下げ（インデント）** をする場合は、
**`Tab`キー**を一回押せば、**一段階インデント**することができます。
**`Space`を4回叩く必要はありません。**

また、複数の行をまとめてインデントしたい場合は、
**その行をマウスで選択した状態で `Tab`キーを押せば OK です。**

逆に**インデントを戻したい時は、`Shift + Tab`キー**を押してください。

ちなみにインデント自体は**コードを見やすくするためだけ**のもので、
ブラウザでの表示結果には "ほとんどの場合" 影響しません。

---

### スタイルシートの記述例2:
```html
<style>
    body {
        background-color: black;
        color: white;
    }
    a {
        color: greenyellow; /* 黄緑色 */
        font-weight: bold;
    }
</style>
```
今度は **`<body>`タグ**と **`<a>`タグ**に対するスタイル指定です。

`<body>`タグは、**ページ全体**を表しているタグです。
`background-color`は、そのタグの**背景色**を示すプロパティです。

`/* 黄緑色 */` という記述は単なる **コメント** で、書き手がメモとして書き残すものです。
HTML における `<!-- コメント -->` と同じ役割のものです。

---

### 表示を確認してみよう
先ほどと同じように、記述例2のスタイルを `index.html` にコピペして
ブラウザでの表示を確認してください。

今度の記述には **`<a>`タグ**へのスタイル指定が含まれているので、
表示の確認のために `<a>`タグを `<body>`タグ内にいくつか書き込んでみてください。

---

## スタイルシートにおける色の表現
ここまでの記述例では、背景色や文字色に対して
`red` や `black`, `white` といった単純な色のみを指定してきたが、
次に示す指定方法を用いることで、より多彩で自由な色表現が可能である。

---

### RGB
```css
color: rgb(0, 0, 0);       /* 黒 */
color: rgb(255, 255, 255); /* 白 */
```

RGB に **A (アルファ)** を加えると **不透明度 (0.0 から 1.0)** を表現できる。
```css
color: rgba(255, 0, 0, 0.5); /* 半透明の赤 */
```

---

### HSL
H = 色彩 (0 から 360)
S = 彩度 (0% から 100%)
L = 明度 (0% から 100%)
```css
color: hsl(120, 100%, 40%); /* 緑 */
```
HSL に **A (アルファ)** を加えると **不透明度 (0.0 から 1.0)** を表現できる。
```css
color: hsla(120, 100%, 40%, 0.5); /* 半透明の緑 */
```

---

## 演習:
学習したフォントやカラーの指定など、画像の設置などを駆使して、
自分のサイトのコーディングを進めてください。

「こうしたいけどやり方がわからない」などの質問は受け付けます。
他のサイトのマネをしても構いません。
（ただし、コピペは無し）

---

[#3 へつづく](README_3.html)