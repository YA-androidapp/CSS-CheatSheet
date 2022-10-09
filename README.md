<!-- TOC -->

- [CSS概要](#css概要)
  - [指定方法](#指定方法)
- [CSSセレクター](#cssセレクター)

<!-- /TOC -->


# CSS概要
<a id="markdown-css%E6%A6%82%E8%A6%81" name="css%E6%A6%82%E8%A6%81"></a>


## 指定方法
<a id="markdown-%E6%8C%87%E5%AE%9A%E6%96%B9%E6%B3%95" name="%E6%8C%87%E5%AE%9A%E6%96%B9%E6%B3%95"></a>

| 名称                            | 場所                  | 例                                       |
| ------------------------------- | --------------------- | ---------------------------------------- |
| style属性（インラインスタイル） | 各タグのstyle属性     | `<div style="color: red;">Red</div>`     |
| styleタグ                       | head要素内のstyleタグ | `<style>div { color: red; }</style>`     |
| 外部CSS                         | head要素内のlinkタグ  | `<link href="app.css" rel="stylesheet">` |
|                                 | CSS内の `@import`     | `@import 'app.css';`                     |


# CSSセレクター
<a id="markdown-css%E3%82%BB%E3%83%AC%E3%82%AF%E3%82%BF%E3%83%BC" name="css%E3%82%BB%E3%83%AC%E3%82%AF%E3%82%BF%E3%83%BC"></a>

| セレクタ             |                  | 表記        | 例                                                                 | 備考                                                                                         |
| -------------------- | ---------------- | ----------- | ------------------------------------------------------------------ | -------------------------------------------------------------------------------------------- |
| 基本セレクター       |                  |             |                                                                    |                                                                                              |
|                      | 全称セレクター   | `*`         | `* { color: red; }`                                                |                                                                                              |
|                      |                  |             |                                                                    |                                                                                              |
|                      | 要素型セレクター | `要素名`    | `div { color: red; }`                                              |                                                                                              |
|                      |                  |             |                                                                    |                                                                                              |
|                      | クラスセレクター | `.クラス名` | `.consectetur { color: red; }`                                     |                                                                                              |
|                      |                  |             | `[class~=consectetur] { color: red; }`                             |                                                                                              |
|                      |                  |             |                                                                    |                                                                                              |
|                      | ID セレクター    | `#ID名`     | `#adipiscing { color: red; }`                                      |                                                                                              |
|                      |                  |             | `[id=adipiscing] { color: red; }`                                  |                                                                                              |
|                      |                  |             |                                                                    |                                                                                              |
|                      | 属性セレクター   | `[]`        | `a[href] { color: red; }`                                          | 属性が存在する要素                                                                           |
|                      |                  |             | `a:not([href]) { color: red; }`                                    | 属性が存在しない要素                                                                         |
|                      |                  |             |                                                                    |                                                                                              |
|                      |                  |             | `a[class="consectetur"] { color: red; }`                           | 完全一致                                                                                     |
|                      |                  |             | `a[class~="consectetur"] { color: red; }` ※1                       | 完全一致（属性値が空白区切りで指定されているときの挙動が `a[class="consectetur"]` と異なる） |
|                      |                  |             | `html[lang\|="en"] { color: red; }`                                | 完全一致または、 `value` で始まり直後にハイフン                                              |
|                      |                  |             |                                                                    |                                                                                              |
|                      |                  |             | `a[href^="#"] { color: red; }`                                     | 前方一致                                                                                     |
|                      |                  |             |                                                                    |                                                                                              |
|                      |                  |             | `a[href*="/articles/"] { color: red; }`                            | 部分一致                                                                                     |
|                      |                  |             | `a[href*="CaseInsensitive" i] { color: red; }`                     | 部分一致（大小文字を区別しない）                                                             |
|                      |                  |             | `a[href*="CaseSensitive" s] { color: red; }`                       | 部分一致（大小文字を区別する）                                                               |
|                      |                  |             |                                                                    |                                                                                              |
|                      |                  |             | `a[href$=".org"] { color: red; }`                                  | 後方一致                                                                                     |
|                      |                  |             |                                                                    |                                                                                              |
|                      |                  |             | `a[href^="https"][href$=".org"] { color: red; }`                   | 組み合わせ                                                                                   |
|                      |                  |             |                                                                    |                                                                                              |
| グループ化セレクター |                  |             |                                                                    |                                                                                              |
|                      | セレクターリスト |             | `h1, h2:pharetra, h3, h4, h5, h6 { color: red; }`                  | すべての一致するノードを選択（未対応のセレクターが1つでもあるとルール全体が無効化される）    |
|                      |                  |             | `:is(h1, h2:pharetra, h3, h4, h5, h6) { font-family: sans-serif }` |                                                                                              |
|                      |                  |             |                                                                    |                                                                                              |
| 結合子               |                  |             |                                                                    |                                                                                              |
|                      | 子孫結合子       | ` `         | `ul#ultrices li span { color: red; }`                              | 1つめの要素より下の階層にある2つめの要素                                                     |
|                      | 子結合子         | `>`         | `ul#ultrices > li > span { color: red; }` ※2                       | 1つめの要素の直下にある2つめの要素                                                           |
|                      | 一般兄弟結合子   | `~`         | `li:first-of-type ~ li { color: red; }`                            | 1つめの要素の後ろにある2つめの要素                                                           |
|                      | 隣接兄弟結合子   | `+`         | `li:first-of-type + li { color: red; }`                            | 1つめの要素の直後にある2つめの要素                                                           |
|                      | 列結合子         | `\|\|`      | `col.label \|\| td { color: red; }`                                | 列に所属するノード                                                                           |
|                      |                  |             |                                                                    |                                                                                              |

<details>
  <summary>※1</summary>

```html
<style>
    a[class="red"] {
        color: red;
    }

    a[class~="ivory"] {
        background-color: ivory;
    }
</style>

<a class="red">Lorem ipsum dolor sit amet.</a><!-- 文字色のみ適用 -->
<a class="red ivory">Lorem ipsum dolor sit amet.</a> <!-- 背景のみ適用 -->
```

</details><br><br>

<details>
  <summary>※2</summary>

```html
<style>
    ul#root li span {
        color: red;
    }

    ul#root>li>span {
        background-color: ivory;
    }

    li:first-of-type~li>span {
        text-decoration-line: underline;
    }

    li:first-of-type+li>span {
        text-decoration-line: underline line-through;
    }
</style>

<ul id="root">
    <li><span>1</span></li>
    <li><span>2</span></li>
    <li><span>3</span>
        <ul>
            <li><span>3-1</span></li>
            <li><span>3-2</span></li>
            <li><span>3-3</span>
                <ul>
                    <li><span>3-3-1</span></li>
                    <li><span>3-3-2</span></li>
                    <li><span>3-3-3</span></li>
                </ul>
            </li>
        </ul>
    </li>
</ul>
```

</details><br><br>

| セレクタ |            |                        | 表記                     | 例                                                                    | 備考                                                                                     |
| -------- | ---------- | ---------------------- | ------------------------ | --------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| 擬似表記 |            |                        |                          |                                                                       |                                                                                          |
|          | 擬似クラス |                        |                          |                                                                       |                                                                                          |
|          |            | 言語擬似クラス         |                          |                                                                       |                                                                                          |
|          |            |                        | `:dir`                   | `:dir(ltr) { color: red; }`                                           | 文書の言語によって決定される書字方向に基づいて要素を選択                                 |
|          |            |                        | `:lang` ※3               | `:lang(ja) { color: red; }`                                           | 内容物の言語に基づいて要素を選択                                                         |
|          |            |                        |                          |                                                                       |                                                                                          |
|          |            | 位置擬似クラス         |                          |                                                                       |                                                                                          |
|          |            |                        | `:any-link`              | `a:any-link { color: red; }`                                          | 要素が `:link` または `:visited` のいずれかに一致する要素を選択                          |
|          |            |                        | `:link`                  | `a:link { color: red; }` ※4                                           | まだ訪問していないリンク要素を選択                                                       |
|          |            |                        | `:visited`               | `a:visited { color: red; }` ※4                                        | 訪問したことのあるリンク要素を選択                                                       |
|          |            |                        | `:local-link`            | ※5                                                                    | 同じページへのリンク要素を選択（絶対 URL が対象 URL と同じリンク）                       |
|          |            |                        | `:target`                | ※6                                                                    | URL のフラグメント（#id）に一致する id を持つ要素                                        |
|          |            |                        | `:target-within`         | ※5                                                                    | URL のフラグメント（#id）に一致する id を持つ要素を子孫要素に持つ要素                    |
|          |            |                        | `:scope`                 | ※7                                                                    | DOM API（ `querySelector(), querySelectorAll()` など）で、メソッドを呼び出した要素を選択 |
|          |            |                        |                          |                                                                       |                                                                                          |
|          |            | ユーザー操作擬似クラス |                          |                                                                       |                                                                                          |
|          |            |                        | `:hover`                 | ※4                                                                    | カーソルを要素の上でかざしたとき                                                         |
|          |            |                        | `:active`                | ※4                                                                    | アイテムがクリックされたとき                                                             |
|          |            |                        | `:focus`                 | ※8                                                                    | フォーカスを持ったとき                                                                   |
|          |            |                        | `:focus-visible`         | ※8                                                                    | キーボード操作でフォーカスを持ったとき                                                   |
|          |            |                        | `:focus-within`          | ※8                                                                    | `:focus` の要素と `:focus` が適用される子孫要素を持つ要素                                |
|          |            |                        |                          |                                                                       |                                                                                          |
|          |            | 時間軸擬似クラス       |                          |                                                                       |                                                                                          |
|          |            |                        | `:current`               |                                                                       | 表示されている要素またはその祖先                                                         |
|          |            |                        | `:past`                  |                                                                       | `:current` 要素の前に発生する要素                                                        |
|          |            |                        | `:future`                |                                                                       | `:current` 要素の後に発生する要素                                                        |
|          |            |                        |                          |                                                                       |                                                                                          |
|          |            | リソース状態擬似クラス |                          |                                                                       |                                                                                          |
|          |            |                        | `:playing`               | `video:playing { border: 5px dashed green; }`                         | 動画などが再生中のとき                                                                   |
|          |            |                        | `:paused`                | `video:paused { border: 5px dashed red; }`                            | 動画などが一時停止中のとき                                                               |
|          |            |                        |                          |                                                                       |                                                                                          |
|          |            | 入力擬似クラス         |                          |                                                                       |                                                                                          |
|          |            |                        | `:autofill`              | `input:autofill { border: 5px dashed red; }`                          | input要素の値がブラウザーによって自動補完されたとき                                      |
|          |            |                        | `:enabled`               | `input:enabled { border: 5px dashed red; }`                           | 要素が有効なとき                                                                         |
|          |            |                        | `:disabled`              | `input:disabled { border: 5px dashed red; }`                          | 要素が無効なとき                                                                         |
|          |            |                        | `:read-only`             | `input:read-only { border: 5px dashed red; }`                         | ユーザーが変更できない要素                                                               |
|          |            |                        | `:read-write`            | `input:read-write { border: 5px dashed red; }`                        | ユーザーが編集できる要素                                                                 |
|          |            |                        | `:placeholder-shown`     | `input:placeholder-shown { border: 5px dashed red; }`                 | placeholder属性のものが表示されている入力要素                                            |
|          |            |                        | `:default`               | ※9                                                                    | 既定の要素                                                                               |
|          |            |                        | `:checked`               | `input:checked { box-shadow: 0 0 2px 1px red; }`                      | チェックボックスやラジオボタンなどのオンになっている要素                                 |
|          |            |                        | `:indeterminate`         | `input:indeterminate { background-color: red; }`                      | ※10                                                                                      |
|          |            |                        | `:blank`                 | `input[type=text]:blank { background-color: red; }`                   | 空文字列が入っている要素                                                                 |
|          |            |                        | `:valid`                 | `input[type=email]:valid { background-color: green; }`                | 内容が妥当である要素                                                                     |
|          |            |                        | `:invalid`               | `input[type=email]:invalid { background-color: red; }`                | 無効な内容を持つ要素                                                                     |
|          |            |                        | `:in-range`              | ※11                                                                   | 選択した値が許容範囲内にある場合                                                         |
|          |            |                        | `:out-of-range`          | ※11                                                                   | 選択した値が許容範囲内にない場合                                                         |
|          |            |                        | `:required`              | `input[type=text]:required { background-color: red; }`                | フォーム要素が必須項目                                                                   |
|          |            |                        | `:optional`              | `input[type=text]:optional { background-color: red; }`                | フォーム要素が省略可能                                                                   |
|          |            |                        | `:user-invalid`          | ※12                                                                   | 不正確な値が入力されている要素                                                           |
|          |            |                        |                          |                                                                       |                                                                                          |
|          |            | ツリー構造擬似クラス   |                          |                                                                       |                                                                                          |
|          |            |                        | `:root`                  | `:root { border: 5px dashed red; }`                                   | 文書のルートである要素                                                                   |
|          |            |                        | `:empty`                 | `div:empty { background-color: red; }`                                | 空白文字以外に子要素・文字列がない要素                                                   |
|          |            |                        | `:nth-child`             | ※13                                                                   | 兄弟要素のリストから要素を選択                                                           |
|          |            |                        | `:nth-last-child`        |                                                                       | 兄弟要素のリストの末尾から逆方向に要素を選択                                             |
|          |            |                        | `:first-child`           | ※13                                                                   | 兄弟のうちの最初の要素                                                                   |
|          |            |                        | `:last-child`            | ※13                                                                   | 兄弟のうちの最後の要素                                                                   |
|          |            |                        | `:only-child`            | ※13                                                                   | 兄弟要素がない要素                                                                       |
|          |            |                        | `:nth-of-type`           | ※14                                                                   | 兄弟要素のリストの特定の型に一致する要素                                                 |
|          |            |                        | `:nth-last-of-type`      |                                                                       | 兄弟要素のリストの末尾から逆方向に特定の型に一致する要素                                 |
|          |            |                        | `:first-of-type`         | ※14                                                                   | 兄弟のうちの最初の特定の型に一致する要素                                                 |
|          |            |                        | `:last-of-type`          | ※14                                                                   | 兄弟のうちの最後の特定の型に一致する要素                                                 |
|          |            |                        | `:only-of-type`          | ※14                                                                   | 指定された型セレクターで兄弟要素がない要素                                               |
|          |            |                        |                          |                                                                       |                                                                                          |
|          | 擬似要素   |                        |                          |                                                                       | 擬似要素は 1 つのセレクターに 1 つだけ使用可能                                           |
|          |            |                        | `::after`                | `p.new-item::after { content: "New!!"; color: red; }`                 | `<img>` や `<br>` のような置換要素には利用不可                                           |
|          |            |                        | `::backdrop`             | `dialog::backdrop { background-color: darkblue; }`                    | 全画面モードで表示される直下に直接表示される viewport の寸法のボックス                   |
|          |            |                        | `::before`               | `p.new-item::before { content: "New!!"; color: red; }`                | `<img>` や `<br>` のような置換要素には利用不可                                           |
|          |            |                        | `::cue`                  | ※15                                                                   | WebVTT キュー                                                                            |
|          |            |                        | `::cue-region`           | ※5 ※15                                                                | WebVTT キュー                                                                            |
|          |            |                        | `::file-selector-button` | `input::file-selector-button { color: red; }`                         | ファイル選択ボタン                                                                       |
|          |            |                        | `::first-letter`         | `p::first-letter { font-size: 2rem; font-weight: bold; color: red; }` | ブロックレベル要素の最初の文字                                                           |
|          |            |                        | `::first-line`           | `p::first-line { text-decoration: underline; }`                       | ブロックレベル要素の最初の行                                                             |
|          |            |                        | `::grammar-error`        | `p::grammar-error { text-decoration: underline; }`                    | ユーザーエージェントが文法的に正しくないとフラグを立てたテキストセグメント               |
|          |            |                        | `::marker`               | `li::marker { content: '☆'; }`                                        | リスト項目のマーカーボックス                                                             |
|          |            |                        | `::part()`               | ※16                                                                   | Shadow DOM内部の要素                                                                     |
|          |            |                        | `::placeholder`          | `input::placeholder { color: red; }`                                  | `<input>` や `<textarea>` のプレースホルダー                                             |
|          |            |                        | `::selection`            |                                                                       |                                                                                          |
|          |            |                        | `::slotted()`            |                                                                       |                                                                                          |
|          |            |                        | `::spelling-error`       |                                                                       |                                                                                          |
|          |            |                        | `::target-text`          |                                                                       |                                                                                          |
|          |            |                        |                          |                                                                       |                                                                                          |

<details>
  <summary>※3</summary>

```html
<style>
    :lang(en) > q {
        quotes: '\201C' '\201D' '\2018' '\2019';
    }

    :lang(ja) > q {
        quotes: '「' '」' '『' '』';
    }
</style>

<div lang="en">Duis porttitor consectetur elit, <q>et venenatis <q>odio gravida sed</q>. Aliquam pharetra vulputate mi nec semper.</q></div>
<div lang="ja">Duis porttitor consectetur elit, <q>et venenatis <q>odio gravida sed</q>. Aliquam pharetra vulputate mi nec semper.</q></div>
```

</details><br><br>

<details>
  <summary>※4</summary>

```html
<style>
    /* LVHA
            Just think 'LOVE' (LV) and 'HATE' (HA)....
            http://css-tricks.com/remember-selectors-with-love-and-hate/
     */
    a:link {
        color: #42ffe0;
        transition: color .5s;
    }

    a:visited {
        color: #42ffc1;
        transition: color .5s;
    }

    a:hover {
        color: #42ffa1;
        transition: color .5s;
    }

    a:active {
        color: #42ff82;
        transition: color .5s;
    }
</style>

<a href="#consectetur">Aliquam pharetra vulputate mi nec semper.</a>
```

</details><br><br>

<details>
    <summary>※5</summary>
    現状ではサポートしているブラウザが存在しない
</details><br><br>

<details>
  <summary>※6</summary>

```html
<style>
    a:local-link {
        text-decoration-line: none;
    }

    p:target {
        background-color: ivory;
        color: red;
    }

    p:target::before {
        color: red;
        content: "►";
        margin-right: 1em;
    }
</style>

<h3>TOC</h3>
<ol>
    <li><a href="#p1">Morbi</a></li>
    <li><a href="#p2">Interdum</a></li>
</ol>

<h3>Contents</h3>
<p id="p1">
    <!-- index.html#p1 にアクセスすると文字色・背景色が変わる -->
    Morbi commodo imperdiet felis, a euismod tellus dapibus et. Sed efficitur consectetur molestie.
</p>
<p id="p2">
    <!-- index.html#p2 にアクセスすると文字色・背景色が変わる -->
    Interdum et malesuada fames ac ante ipsum primis in faucibus. Phasellus condimentum diam vel lorem elementum.
</p>
```

</details><br><br>

<details>
  <summary>※7</summary>

```html
<ul id="context">
    <li id="1">1</li>
    <li id="2">2</li>
    <li id="3">3
        <ul>
            <li id="3-1">3-1</li>
            <li id="3-2">3-2</li>
            <li id="3-3">3-3
                <ul>
                    <li>3-3-1</li>
                    <li>3-3-2</li>
                    <li>3-3-3</li>
                </ul>
            </li>
        </ul>
    </li>
</ul>
<p>
    Selected elements ids :
    <span id="results"></span>
</p>

<script>
    document.addEventListener('DOMContentLoaded', function () {
        var context = document.getElementById('context');
        var selected = context.querySelectorAll(':scope > li');

        document.getElementById('results').innerHTML = Array.prototype.map.call(selected, function (element) {
            return element.getAttribute('id');
        }).join(', ');
    });
</script>
```

`document.getElementById('context')` の直下のli要素

> Selected elements ids : 1, 2, 3

</details><br><br>

<details>
  <summary>※8</summary>

```html
<style>
    button,
    div {
        margin: 10px;
    }

    button:focus {
        outline: 2px dashed red;
    }

    button:focus-visible {
        outline: 2px dashed orange;
    }

    div:focus-within {
        outline: 2px dashed green;
    }
</style>

<div>
    <button>aenean</button>
    <button>lacus</button>
    <button>felis</button>
</div>
```

</details><br><br>

<details>
  <summary>※9</summary>

```html
<style>
    input:default {
        box-shadow: 0 0 2px 1px red;
    }

    input:default + label {
        color: red;
    }
</style>

<fieldset>
  <input type="radio" name="level" id="high" checked><label for="high">High</label>
  <input type="radio" name="level" id="middle">      <label for="middle">Middle</label>
  <input type="radio" name="level" id="low">         <label for="low">Low</label>
</fieldset>
```

</details><br><br>

<details>
    <summary>※10</summary>
    indeterminate プロパティが true に設定されてチェックボックス、フォーム内の同じ name の値を持つすべてのラジオボタンが未選択、中間の状態のprogress要素
</details><br><br>

<details>
  <summary>※11</summary>

```html
<style>
    input[type=number]:in-range {
        background-color: green;
    }

    input[type=number]:out-of-range {
        background-color: red;
    }
</style>

<input type="number" name="num1" id="num1" min="1" max="10" value="8">
<input type="number" name="num2" id="num2" min="1" max="10" value="12">
```

</details><br><br>

<details>
  <summary>※12</summary>

```html
<style>
    input:user-invalid {
        border: 5px dashed red;
    }

    input:user-invalid+span::before {
        content: '✖';
        color: red;
    }
</style>

<input id="email" name="email" type="email">
<span></span>
```

</details><br><br>

<details>
  <summary>※13</summary>

```html
<style>
    li:nth-child(2n+1) {
        /*
        奇数番目
        li:nth-child(odd)
         */
        color: red;
    }

    li:nth-child(even) {
        /*
        偶数番目
        li:nth-child(2n)
         */
        color: blue;
    }

    li:nth-child(3) {
        /* li:nth-child(n) の n は 0 始まり */
        background-color: lightpink;
    }

    li:first-child {
        background-color: lightcoral;
    }

    li:last-child {
        background-color: lightcoral;
    }

    li:only-child {
        background-color: lightgray;
    }
</style>

<ul>
    <li>0</li>
    <li>1</li>
    <li>2</li>
    <li>3</li>
    <li>4</li>
    <li>5</li>
    <li>6</li>
    <li>7</li>
    <li>8</li>
    <li>9</li>
    <li>10</li>
</ul>
<ul>
    <li>00</li>
</ul>
```

</details><br><br>

<details>
  <summary>※14</summary>

```html
<style>
    li:nth-of-type(5n) {
        /* 4 つおき */
        color: red;
    }

    li:first-of-type {
        background-color: lightcoral;
    }

    li:last-of-type {
        background-color: lightcoral;
    }

    li:only-of-type {
        background-color: lightgray;
    }
</style>

<ul>
    <li>0</li>
    <li>1</li>
    <li>2</li>
    <li>3</li>
    <li>4*</li>
    <li>5</li>
    <li>6</li>
    <li>7</li>
    <li>8</li>
    <li>9*</li>
    <li>10</li>
    <li>11</li>
    <li>12</li>
    <li>13</li>
    <li>14*</li>
    <li>15</li>
</ul>
<ul>
    <li>00</li>
</ul>
```

</details><br><br>

<details>
  <summary>※15</summary>

```html
<style>
    ::cue {
        color: white;
        background-color: rgba(0, 0, 0, 0.6);
    }

    video::cue(b) {
        color: azure;
        background-color: rgba(0, 0, 0, 0.6);
    }
</style>

<video controls autoplay src="110879.mp4">
    <track default src="webvtt.vtt">
</video>
```

```
WEBVTT

00:01.000 --> 00:03.000
Lorem ipsum dolor sit amet, consectetur adipiscing elit.

00:04.000 --> 00:06.000
Cras congue, <b>lacus vel aliquet interdum</b>, augue tellus faucibus lorem, ac posuere purus lacus in erat.
Aliquam vitae nulla nec elit convallis ultrices. Aenean eget placerat risus.

NOTE
Sed dignissim, erat eget condimentum dapibus,
nisi nisl sollicitudin ex,
auctor tempor velit eros eget erat.

00:07.000 --> 00:09.000
Vestibulum dignissim vehicula est sed vehicula.

```

</details><br><br>

<details>
  <summary>※16</summary>

```html
<style>
    temp-elem::part(divpart):hover {
        background-color: #9c9cff;
        border-bottom: #0c0dcc solid 2px;
    }
</style>

<template id="temp-elem">
    <style>
        :host {
            display: flex;
        }

        div {
            margin: 5px;
        }
    </style>
    <div part="divpart active">Part 1</div>
    <div part="divpart">Part 2</div>
    <div part="divpart">Part 3</div>
</template>

<temp-elem></temp-elem>

<script>
    let template = document.querySelector("#temp-elem");
    globalThis.customElements.define(
        template.id,
        class extends HTMLElement {
            constructor() {
                super()
                    .attachShadow({ mode: "open" })
                    .append(template.content);
            }
        }
    );
</script>
```

</details><br><br>

<details>
  <summary>※17</summary>

```html

```

</details><br><br>

<details>
  <summary>※18</summary>

```html

```

</details><br><br>

<details>
  <summary>※19</summary>

```html

```

</details><br><br>


