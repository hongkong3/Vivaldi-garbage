---

title: Vivaldi markdown-sample
url: https://github.com/hongkong3/Vivaldi-garbage

---

# メモパネル用CSS [sample]
<a name="mdcsmp_0"></a>
これは [Vivaldi][vivaldi] のメモパネルを Markdownメモ として使い倒そうというカスタムCSS用のサンプルです。

[vivaldi]: https://vivaldi.com/ "Powerful. Personal. Private."

  * メモパネルの「マークダウン表示」に特化したCSSです  
    日本語用の調整やインラインHTMLによるクラス指定を使った自家拡張などしてます

  * あくまで**メモパネル用**です、タブで開く「メモ」は別物です  


<div class="box cross double">

- [文字装飾](#mdcsmp_1)
- [見出し](#mdcsmp_2)
- [リスト](#mdcsmp_3)
- [引用](#mdcsmp_4)
- [テーブル](#mdcsmp_5)
- [インラインHTML](#mdcsmp_6)
  - [装飾用クラス](#mdcsmp_6d)
  - [スライドメニュー](#mdcsmp_6s)
  - [アニメーションクラス](#mdcsmp_6a)
* [設定](#mdcsmp_7)
</div>

<div class="slide-menu"><div><!-- slide-menu -->

<!-- ### Table of Contents -->
<div>

- [TOP](#mdcsmp_0)
  - [文字装飾](#mdcsmp_1)
  - [見出し](#mdcsmp_2)
  - [リスト](#mdcsmp_3)
  - [引用](#mdcsmp_4)
  - [テーブル](#mdcsmp_5)
  - [インラインHTML](#mdcsmp_6)
    - [装飾用クラス](#mdcsmp_6d)
    - [スライドメニュー](#mdcsmp_6s)
    - [アニメーションクラス](#mdcsmp_6a)
* [設定](#mdcsmp_7)
* [ライセンス情報](#mdcsmp_l)
</div></div></div>

- - - - - - - -
## 文字装飾 <a name="mdcsmp_1"></a>
- `*em*` *斜体 + 文字色変更*  
- `**strong**` **太字 + 文字サイズ拡大**  
- `~~Strikethrough~~` ~~取消線 + 淡色化~~  
- `[text](# "tooltip")` 注釈付きテキストとして扱い、[マウスカーソルを乗せるとツールチップ](# "こんな感じで表示します")を表示します  
    リンク記法のURL指定が「`#_-+*!?`」のどれか1文字なら同様です  
- [普通のリンク][vivaldi] はこんな感じに表示されます  
&nbsp;

## 見出し <a name="mdcsmp_2"></a>
- 
  <details><summary>普通の見出し 使用例:</summary>

  # \# 見出し lv1
  ## \## 見出し lv2
  ### \### 見出し lv3
  #### \#### 見出し lv4
  ##### \##### 見出し lv5
  ###### \###### 見出し lv6
  * * * *
   水平線 `<hr>` <i class="ico arr u hl"></i>
  </details>

- ブロック内に `number-header` 等のクラスを持つ要素があると、同ブロック内では **番号付きの見出し** になります
  <details><summary>番号付き見出し 使用例：</summary>

  ## ここは番号なし
  > <i class="number-header"></i> <!-- これ自体は表示されません -->
  > # header 1.
  > ## header2 1-1.
  > ## header2 1-2.
  > ### header3 1-2-1.
  ## ここも番号なし

  ~~~~~~~~markdown
  ## ここは番号なし
  > <i class="number-header"></i> <!-- これ自体は表示されません -->
  > # header 1.
  > ## header2 1-1.
  > ## header2 1-2.
  > ### header3 1-2-1.
  ## ここも番号なし
  ~~~~~~~~

  > #### `number-header` `numhead` `num` など
  > `# ` ～ `### ` (Lv1～3) の見出しに番号付け
  > #### `number-header2` `numhead2` `num2` など
  > `## ` ～ `#### ` (Lv2～4)の見出しに番号付け
  </details>
&nbsp;

## リスト <a name="mdcsmp_3"></a>
- 本CSSとは関係なくメモパネルのマークダウン仕様として、番号リストでその階層で最初の番号が `2` 以上ならその番号から開始されます
  <details><summary>開始番号指定 使用例：</summary>

  1. one [1]  
     5. five [5]  
     1. one [6]  
        1. one [1]  
     1. one [7]  
  <br/>
  ~~~~~~~~md
  1. one [1]  
     5. five [5]  
     1. one [6]  
        1. one [1]  
     1. one [7]  
  ~~~~~~~~ 
  </details>

- 番号リスト内に `nest-order`, `nest` クラスを持つ要素があると、階層による番号リスト化します
  <details><summary>階層番号リスト 使用例：</summary>

  1. foo [1.] <i class="nest-order"></i>
     1. bar [1-1.]
        1. baz [1-1-1.]
     1. faz [1-2.]
  <br/>
  ~~~~~~~~md
  1. foo [1.] <i class="nest-order"></i>
     1. bar [1-1.]
        1. baz [1-1-1.]
     1. faz [1-2.]
  ~~~~~~~~
  </details>

- リスト内に `tree-list`, `tree` クラスを持つ要素があると、ツリーリスト化します
  <details><summary>ツリーリスト 使用例：</summary>

  **ツリーリスト**
  - その階層からすべてツリー化 <u class="tree"></u>
    1. 番号リスト・箇条書きリスト共に適用
  - 直前の要素にくっつくように余白も調整
  <br/>
  ~~~~~~~~md
  **ツリーリスト**
  - その階層からすべてツリー化 <u class="tree"></u>
    1. 番号リスト・箇条書きリスト共に適用
  - 直前の要素にくっつくように余白も調整
  ~~~~~~~~
  </details>

- 箇条書きリスト内に `nomarker`, `-mark` などのクラスを持つ要素があると、リストマーク無しのリストになります
  <details><summary>リストマークなしリスト 使用例：</summary>

  - 字下げだけしてる感じです <b class="nomarker"></b>
    - 引用ではない字下げを使いたい時に？
  <br/>
  ~~~~~~~~md
  - 字下げだけしてる感じです <b class="nomarker"></b>
    - 引用ではない字下げを使いたい時に？
  ~~~~~~~~
  </details>

- チェックリスト `- [x] checked` はマークダウン表示中は固定にしてます、切り替わりません
  <details><summary>チェックリスト 使用例：</summary>

  - [x] チェックON
  - [ ] チェックOff
  <br/>
  ~~~~md
  - [x] チェックON
  - [ ] チェックOff
  ~~~~
  </details>

- リストアイテム内に `data-mark` 属性を持つ要素があれば、その内容をリストマークのように表示します
  <details><summary>リストマークの変更 使用例：</summary>

  - 普通のリストアイテム
  - 内部に `data-mark="😉"` の要素<b data-mark="😉"></b>
    - <i class="c-red" data-marker="ゐ."></i> 絵文字以外の文字でもOKです
      `class="c-red" data-marker="ゐ."`
  - <s class="fade" data-mark="💡"></s> `fade` クラス付きで指定すると、通常のリストマーク同様に普段は薄く表示されます
    `class="fade" data-mark="💡"`
  - 表示上、絵文字一個か英数数文字くらいなら使えます <s class="fade c-grn" data-mark="hint"></s>  
  <br/>
  ~~~~md
  - 普通のリストアイテム
  - 内部に `data-mark="😉"` の要素<b data-mark="😉"></b>
    - <i class="c-red" data-marker="ゐ."></i> 絵文字以外の文字でもOKです
      `class="c-red" data-marker="ゐ."`
  - <s class="fade" data-mark="💡"></s> `fade` クラス付きで指定すると、通常のリストマーク同様に普段は薄く表示されます
    `class="fade" data-mark="💡"`
  - 表示上、絵文字一個か英数数文字くらいなら使えます <s class="fade c-grn" data-mark="hint"></s>  
  ~~~~
  文字色指定に`hl1` `hl2` を使うとリストマーク化してくれません…
  </details>
&nbsp;

## 引用 <a name="mdcsmp_4"></a>
- 引用内の最初にLv4見出し `#### lv4` があると引用ブロックの縦線と一体化し、定義リスト風の見た目になります  
  <details><summary>定義リスト風 使用例：</summary>
  > #### 定義語?
  > 定義内容?
  > #### 2つ目移行も
  > 同様に一体化します

  ~~~~~~~~md
  > #### 定義語?
  > 定義内容?
  > #### 2つ目移行も
  > 同様に一体化します
  ~~~~~~~~
  </details>

- 内部に `card` クラスを持つ要素があると、カード風に少し立体的に表示します  
  `hl0`, `hl1`, `hl2` などのクラスも併用すると着色します  
  <details><summary>カード風 使用例：</summary>
  > カード風？ <wbr class="card hl1"/>
  <br/>
  ~~~~~~~~md
  > カード風？ <wbr class="card hl1"/>
  ~~~~~~~~

  > #### Lv4見出しのと併用もできます
  > 他の色もあります <b class="card b-gray"></b>  
  > `<b class="card b-gray"></b>`

  ショートハンドとして以下のものも使えます
  > 情報: `<b class="card info"></b>` <b class="card info"></b>

  > 注意: `<b class="card warn"></b>` <b class="card warn"></b>

  > 警告: `<b class="card alert"></b>` <b class="card alert"></b>

  > ヒント: `<b class="card tips"></b>` <b class="card tips"></b>
  </details>
&nbsp;


## テーブル <a name="mdcsmp_5"></a>
- テーブル最上段のヘッダ行は *スクロールに追従* します  
  ヘッダ行がすべて空なら **ヘッダ行自体を表示しません**  

- 空のセルが1つだけの行は *表示しません*  
  2つ以上の空のセルのみの行は *テーブル内の区切り線* のようになります

- セル内に `<b></b>` か `th` `head` `bold` のクラスを持つ要素があると **ヘッダセル\<th\>化** します  
  セル内に `<tt></tt>` か `code` `kbd` `monospace` のクラスを持つ要素があると *等幅フォント化* します

- セル内に `left` `center` `right`, `top` `middle` `bottom` のクラスを持つ要素があると, そのセル内の位置揃えを指定できます

  <details><summary>テーブル 使用例:</summary>

  | th1 | th2 | th3 |
  | --- | :-: | --: |
  | 普通の | table | です |
  | 偶数行と | ホバー行は | 色分けします |

  |     |     |     |
  | --- | --- | --- |
  | <i class="icon arr c-red"></i>空っぽの | ヘッダ行は | 表示しません |
  | |
  | <i class="icon arr c-grn"></i>一個だけの | 空セル行も | 表示しません |
  | | | |
  | <i class="icon arr c-ble"></i>複数個の | 空セル行は | 区切りになります |
  | ヘッダセル化<b></b> | fixed<br class="kbd">cell | 右中央寄せ<wbr class="right middle"> |
  ~~~~md
  |     |     |     |
  | --- | --- | --- |
  | <i class="icon arr c-red"></i>空っぽの | ヘッダ行は | 表示しません |
  | |
  | <i class="icon arr c-grn"></i>一個だけの | 空セル行も | 表示しません |
  | | | |
  | <i class="icon arr c-ble"></i>複数個の | 空セル行は | 区切りになります |
  | ヘッダセル化<b></b> | fixed<br class="kbd">cell | 右中央寄せ<wbr class="right middle"> |
  ~~~~
  </details>

- 特定のクラスを持つ要素がテーブル内に存在すれば, テーブル全体のオプション指定となります
  <details><summary>テーブルオプション 使用例:</summary>

  |クラス名|内容<wbr class="t-m">|
  |-|-|
  |`noborder` `-border`|セルの枠線なし|
  |`frame` `edge`|テーブル全体を囲む枠線を描画|
  |`nostripe` `-stripe`|偶数行の色分けなし|
  |`nohover` `-hover`|マウスカーソル行の着色なし|
  |`t-top` `t-t`<br>`t-up` `t-u`<tt></tt><td rowspan="3">セル内部の上下位置揃え<br>(テーブル全体)|
  |`t-middle` `t-m`<br>`t-center` `t-c`<tt>|
  |`t-bottom` `t-b`<br>`t-down` `t-d`<tt>|
  |`t-right` `t-r`<tt>|テーブル自体を右側へ配置|
  |`full` `max`|テーブルを右端まで引き伸ばす|
  |`footer` `ft`|最後の行を[フッタ行として固定](* "スクロールに追従します")|
  |`row` `slide`<br>`horizontal` `hrz`|左端列の[セル固定化](* "横スクロールに追従します")<br>セル内の自動折り返し無効|

  **サンプル**
  | | |
  |:-:|---|
  |noborder<wbr class="noborder edge kbd nohover full footer t-bottom">|セルの枠線なし|
  |frame<tt></tt>|テーブル全体に枠線|
  |nohover<tt></tt>|マウスカーソル行の着色なし|
  |v-bottom<tt></tt>|全体的に下揃え|
  |full<tt></tt>|右端までテーブル|
  |footer<tt></tt>|フッタ行として固定<br>固定するだけで\<th\>化はしない|

  | th1 | th2 |
  |-|:-:|
  |nostripe<wbr class="kbd">|偶数行の色分けなし<i class="hl f-l">scroll >></i>|
  |上下位置<br>指定用クラス|上: `t-top` `t-up` `t-t` `t-u` / 中: `t-middle` `t-center` `t-m` `t-c` / 下: `t-bottom` `t-down` `t-b` `t-d`|
  |この列<u class="ico arr c-ppl slide nostripe t-m"></u>を固定化|`slide` で左端列が横スクロールに追従します セル内の自動改行も無し|
  </details>

- セルの連結
  GFMテーブル記法の`|`の代わりに`<td>` `<th>`を記述する事で`colspan="2"`などが効いたりします
  <details><summary>セル連結 使用例:</summary>

  | th1 | th2 | th3 |
  | --- | :-: | --: |
  | td1a <td colspan="2"> td2-3a |
  | td1b <td rowspan="2"> td2b-c | td3b |
  | td1c | td3c |
  ~~~~md
  | th1 | th2 | th3 |
  | --- | :-: | --: |
  | td1a <td colspan="2"> td2-3a |
  | td1b <td rowspan="2"> td2b-c | td3b |
  | td1c | td3c |
  ~~~~
  ただしこの方法では左端のセルは連結できないので, その場合は行(`<tr>`)ごとインラインHTMLで記述します  
  ~~~~md
  | |
  |<tr><td colspan="2"> td1a-b <td> td1c |
  ~~~~
  本来は空のセル一個だけの余分な行ができますが, 本CSSでは *空のセル一個だけの行は表示しない* 仕様なので消えます  
  さらに *偶数行塗り分け* の辻褄合わせとして空セル一個の行を追加してます
  | th1 | th2 | th3 |
  | --- | --- | --- |
  ||
  |<tr><td rowspan="2"> td1a-b <td colspan="2"> td2-3a |
  | <u class="b-ppl">td2b <td rowspan="2"> td3b-c |
  ||
  |<tr><td colspan="2"> td1-2c |
  ~~~~md
  | th1 | th2 | th3 |
  | --- | --- | --- |
  ||
  |<tr><td rowspan="2"> td1a-b <td colspan="2"> td2-3a |
  | <u class="b-ppl">td2b <td rowspan="2"> td3b-c |
  ||
  |<tr><td colspan="2"> td1-2c |
  ~~~~
  Vivaldiメモのマークダウンのクセを利用したハックなので, たぶん他では使えません…
  </details>&nbsp;


## インラインHTML <a name="mdcsmp_6"></a>
- 定義リスト・折りたたみブロック も使えるよう調整してます
  <details><summary>定義リスト・折りたたみブロック 使用例:</summary>

  <dl>
    <dt>定義リスト</dt>
    <dd>

    **一行空ければ** マークダウン記法も使える
    但し1行目がスペース4個以上字下げだと, *コードブロック化*するので注意
    </dd>
  </dl>

  ~~~~md
  <dl>
    <dt>定義リスト</dt>
    <dd>
  
    **一行空ければ** マークダウン記法も使える
    但し1行目がスペース4個以上字下げだと, *コードブロック化*するので注意
    </dd>
  </dl>
  ~~~~

  <details><summary>折りたたみブロック</summary>

    同上, `<details open>` なら初期で展開状態  
    終端の `</details>` などの後も1行空けないとマークダウン使えない
  </details>

  ~~~~md
  <details><summary>折りたたみブロック</summary>

    同上, `<details open>` なら初期で展開状態  
    終端の `</details>` などの後も1行空けないとマークダウン使えない
  </details>
  ~~~~
  </details>

- 2つ以上のスペースや空行には`&nbsp;`を使います  
  `<br>`を使えばテーブルセル内などの中で改行もできます  

- 行末に`<wbr>`があると直後の改行(`<br>`)を無効化してます  
  ただし`<wbr>`なので自動改行が必要なら改行されます  

- `<abbr>` `<kbd>` `<sup>` `<sub>` `<mark>` `<ruby><rt>` なんかも使えます  
  <abbr title="本来は略語を示すらしいです">abbr</abbr> <wbr>
  <kbd>kbd</kbd> <sup>sup</sup> <sub>sub</sub> <mark>mark</mark> <wbr>
  <ruby>ruby<rt>ルビ</rt></ruby>

- `<b>` `<i>` `<q>` `<s>` `<u>` `<tt>`はクラス指定用に*スタイルをリセット*してます
  他に`<wbr>`もクラス指定だけなら使いやすいです  

- `<p>` `<div>`は中身が空なら表示されません  
&nbsp;


### 装飾用クラス <a name="mdcsmp_6d"></a>
- 
  <details><summary>文字色 クラス</summary>

  `<b class="c-red">テキスト</b>`のように対象を<b class="c-red">囲んで使用</b>します
  |クラス名|表示サンプル|
  |-|-|
  | hl0 hl <tt>| <u class="hl">ハイライト0 😀 <i class="ico arr u"></i></u> |
  | hl1 <tt>| <u class="hl1">ハイライト1 😀 <i class="ico arr u"></i></u> |
  | hl2 <tt>| <u class="hl2">ハイライト2 😀 <i class="ico arr u"></i></u> |
  | c-red fg-red <tt>| <u class="c-red">red 赤 😀 <i class="ico arr u"></i></u> |
  | c-org fg-orange <tt>| <u class="c-org">orange 橙 😀 <i class="ico arr u"></i></u> |
  | c-ylw fg-yellow <tt>| <u class="c-ylw">yellow 黄色 😀 <i class="ico arr u"></i></u> |
  | c-grn fg-green <tt>| <u class="c-grn">green 緑 😀 <i class="ico arr u"></i></u> |
  | c-aqa fg-cyan <tt>| <u class="c-cyn">cyan 水色 😀 <i class="ico arr u"></i></u> |
  | c-ble fg-blue <tt>| <u class="c-ble">blue 青 😀 <i class="ico arr u"></i></u> |
  | c-ppl fg-violet <tt>| <u class="c-vlt">purple 紫 😀 <i class="ico arr u"></i></u> |
  | c-fch fg-magenta <tt>| <u class="c-mgt">magenta 赤紫 😀 <i class="ico arr u"></i></u> |
  | c-wht fg-white <tt>| <u class="c-wht b-red">white 白 😀 <i class="ico arr u"></i></u> |
  | c-gry fg-grey <tt>| <u class="c-gry b-red">gray 灰色 😀 <i class="ico arr u"></i></u> |
  | c-blk fg-black <tt>| <u class="c-blk b-red">black 黒 😀 <i class="ico arr u"></i></u> |
  ハイライト0～2 はテーマのハイライトカラーを元にした色ですが, それ以外は固定色です
  </details>

- 
  <details><summary>背景色 クラス</summary>

  `<b class="b-red">テキスト</b>`のように対象を<b class="b-red">囲んで使用</b>します
  |クラス名|表示サンプル|
  |-|-|
  | b-red bg-red <tt>| <u class="b-red">red 赤 😅 <i class="ico arr u r"></i></u> |
  | b-org bg-orange <tt>| <u class="b-org">orange 橙 😅 <i class="ico arr u r"></i></u> |
  | b-ylw bg-yellow <tt>| <u class="b-ylw">yellow 黄色 😅 <i class="ico arr u r"></i></u> |
  | b-grn bg-green <tt>| <u class="b-grn">green 緑 😅 <i class="ico arr u r"></i></u> |
  | b-cyn bg-aqua <tt>| <u class="b-aqa">cyan 水色 😅 <i class="ico arr u r"></i></u> |
  | b-ble bg-blue <tt>| <u class="b-ble">blue 青 😅 <i class="ico arr u r"></i></u> |
  | b-vlt bg-purple <tt>| <u class="b-ppl">violet 紫 😅 <i class="ico arr u r"></i></u> |
  | b-mgt bg-fuchsia <tt>| <u class="b-fch">fuchsia 赤紫 😅 <i class="ico arr u r"></i></u> |
  | b-wht bg-white <tt>| <u class="b-wht c-grn">white 白 😅 <i class="ico arr u r"></i></u> |
  | b-gry bg-gray <tt>| <u class="b-gry c-grn">gray 灰色 😅 <i class="ico arr u r"></i></u> |
  | b-blk bg-black <tt>| <u class="b-blk c-grn">black 黒 😅 <i class="ico arr u r"></i></u> |
  テーブルセルなどで要素が1つだけだと、セル全体を着色します
  それを避けるには `<wbr>` 等をてきとーに追加します
  </details>

- 
  <details><summary>文字サイズ クラス</summary>

  `<b class="big">テキスト</b>`のように対象を<b class="big">囲んで使用</b>します
  |クラス名|表示サンプル|
  |-|-|
  | big large <tt>| <u class="big vm">1.4倍化 😁 <i class="ico arr a1 r"></i></u> |
  | small mini <tt>| <u class="small">0.8倍化 😁 <i class="ico arr a1 r"></i></u> |
  それぞれ<s class="big">重ね<s class="big">がけ<s class="big">可能</s></s></s>です
  </details>

- 
  <details><summary>テキスト属性 クラス</summary>

  `<b class="ins">テキスト</b>`のように対象を<b class="ins">囲んで使用</b>します
  |クラス名|表示サンプル|
  |-|:-:|
  | em italic oblique<tt>| <u class="italic t-m">斜体テキスト</u> |
  | bold strong<tt>| <u class="strong">太字テキスト</u> |
  | del strike<tt>| <u class="del">取り消し線テキスト</u> |
  | ins underline u<tt>| <u class="ins">下線テキスト</u> |
  | heavy impact gonta<tt>| <u class="gonta">極太テキスト</u> |
  | metal chrome<tt>| <u class="metal">メタル調？</u> |
  ||
  |||
  | f-web f-regular f-reg<br/>f-normal f-norm<tt>| <u class="f-web">[標準 フォント](* "Vivaldi設定 > ウェブページ > フォント > &#x22;標準&#x22;のフォント")</u> |
  | code tt<br/>f-mono f-fixed<tt>| <u class="code">等幅フォント</u> |
  | f-sans-serif f-sans<br/>f-gothic f-go<tt>| <u class="f-sans">ゴシック系フォント</u> |
  | f-serif f-clasic<br/>f-book f-mincho f-min<tt>| <u class="f-serif">明朝系フォント</u> |
  | f-cursive f-hand<br/>f-script f-sosho<tt>| <u class="f-hand">手書き系フォント</u> |
  | f-fantasy f-fun<br/>f-logo f-display<tt>| <u class="f-fan">装飾系フォント</u> |

  <s class="serif">重ね<s class="italic">がけも<s class="heavy">可能</s></s></s>です
  手書き系・装飾系は[未設定だと日本語未対応](* "Vivaldi設定 > ウェブページ > フォント で設定可能です")だったりします
  </details>

- 
  <details><summary>ラインマーカー クラス</summary>

  `<b class="m-red">テキスト</b>`のように対象を<b class="m-red">囲んで使用</b>します
  |クラス名|表示サンプル|
  |-|-|
  | mk mark <tt>| <u class="mk">highlight 強調 🙄 <i class="ico arr a2 r f-lr"></i></u> |
  | mk-red mark-red <tt>| <u class="mk-red">red 赤 🙄 <i class="ico arr a2 r f-lr"></i></u> |
  | mk-org mark-orange <tt>| <u class="mk-org">orange 橙 🙄 <i class="ico arr a2 r f-lr"></i></u> |
  | mk-ylw mark-yellow <tt>| <u class="mk-ylw">yellow 黄色 🙄 <i class="ico arr a2 r f-lr"></i></u> |
  | mk-grn mark-green <tt>| <u class="mk-grn">green 緑 🙄 <i class="ico arr a2 r f-lr"></i></u> |
  | mk-cyn mark-aqua <tt>| <u class="mk-aqa">cyan 水色 🙄 <i class="ico arr a2 r f-lr"></i></u> |
  | mk-ble mark-blue <tt>| <u class="mk-ble">blue 青 🙄 <i class="ico arr a2 r f-lr"></i></u> |
  | mk-vlt mark-purple <tt>| <u class="mk-ppl">violet 紫 🙄 <i class="ico arr a2 r f-lr"></i></u> |
  | mk-mgt mark-fuchsia <tt>| <u class="mk-fch">fuchsia 赤紫 🙄 <i class="ico arr a2 r f-lr"></i></u> |
  | mk-wht mark-white <tt>| <u class="mk-wht b-ble">white 白 🙄 <i class="ico arr a2 r f-lr"></i></u> |
  | mk-gry mark-gray <tt>| <u class="mk-gry b-ble">gray 灰色 🙄 <i class="ico arr a2 r f-lr"></i></u> |
  | mk-blk mark-black <tt>| <u class="mk-blk b-ble">black 黒 🙄 <i class="ico arr a2 r f-lr"></i></u> |
  </details>

- 
  <details><summary>波線マーカー クラス</summary>

  `<b class="wv-red">テキスト</b>`のように対象を<b class="wv-red">囲んで使用</b>します
  |クラス名|表示サンプル|
  |-|-|
  | wv wave <tt>| <u class="wv">highlight 強調 😒 <i class="ico mark"></i> </u> |
  | wv-red wave-red <tt>| <u class="wv-red">red 赤 😒 <i class="ico mark"></i> </u> |
  | wv-org wave-orange <tt>| <u class="wv-org">orange 橙 😒 <i class="ico mark"></i> </u> |
  | wv-ylw wave-yellow <tt>| <u class="wv-ylw">yellow 黄色 😒 <i class="ico mark"></i> </u> |
  | wv-grn wave-green <tt>| <u class="wv-grn">green 緑 😒 <i class="ico mark"></i> </u> |
  | wv-cyn wave-aqua <tt>| <u class="wv-aqa">cyan 水色 😒 <i class="ico mark"></i> </u> |
  | wv-ble wave-blue <tt>| <u class="wv-ble">blue 青 😒 <i class="ico mark"></i> </u> |
  | wv-vlt wave-purple <tt>| <u class="wv-ppl">violet 紫 😒 <i class="ico mark"></i> </u> |
  | wv-mgt wave-fuchsia <tt>| <u class="wv-fch">fuchsia 赤紫 😒 <i class="ico mark"></i> </u> |
  | wv-wht wave-white <tt>| <u class="wv-wht b-org">white 白 😒 <i class="ico mark"></i> </u> |
  | wv-gry wave-gray <tt>| <u class="wv-gry b-org">gray 灰色 😒 <i class="ico mark"></i> </u> |
  | wv-blk wave-black <tt>| <u class="wv-blk b-org">black 黒 😒 <i class="ico mark"></i> </u> |

  `gy`などの文字・アイコン/回転クラス等でちょいちょい途切れます, 仕様らしいです
  </details>

-
  <details><summary>バーメーター クラス</summary>

  自動で進行したりはしません
  指定した進行度の割り合いを視覚的に眺めるだけです

  <b class="bar-meter frame" data-value="50">bar meter</b>
  `<b class="bar-meter frame" data-value="50">bar meter</b>`

  - `class="bar-meter"` *\[必須\]*
    `bar-meter`, `meter`, `progress` 等のクラスを指定します
  - `data-value="**"` *\[必須\]*
    進行度を 0 ～ 100 の数値で指定します
  
  #### 以下はオプション指定です：
  - (中身のテキスト)
    そのまま中央表示されます
  - 背景色クラス
    バーと背景の色が変わります
    `info`, `warn`, `alert`, `tips`クラスでは、バーの色だけ変わります
    <br/>

  - `border` `frame` クラス
    枠を表示します
  - `ruler` `measure` クラス
    目盛りを表示します
  - `tube` `pipe` クラス
    少し光沢感を出します
  - `stripe` `ribbon` `zebra` クラス
    薄い縞模様
  - `slim` `thin` クラス
    細めのバーになります
  - `line` `slit` クラス
    さらに細いバーになります
    <br/>

  - `data-thumb` 属性
    絵文字などを指定すればバー上に表示します
    <s class="meter b-org slim tube ruler" data-value="30" data-thumb="🐸"></s>
    `class="meter b-org slim tube ruler" data-value="30" data-thumb="🐸"`
    回転・反転クラスを併用すれば、向きも変更できます

  </details>

- 
  <details><summary>アイコン クラス</summary>

  `icon` `ico` クラスと以下のクラス同時に指定します
  追加で `a1` `a2` `a3` `a4` クラスも指定するとバリエーションのアイコンになります
  強制的にアイコン化するので, 内部に文字があっても見えません
  <s class="icon arr a3 r c-vlt">印</s> `<s class="icon arr a3 r c-vlt">印</s>`

  |icon + クラス名 <th colspan="5"> 表示 (a0, a1, a2, a3, a4)<u class="center">|
  |-|
  | arrow arr <tt>|<i class="arr ico"></i>|<i class="arr ico p1"></i>|<i class="arr ico p2"></i>|<i class="arr ico p3"></i>|<i class="arr ico p4"></i>|
  | star str <tt>|<i class="str ico"></i>|<i class="str ico p1"></i>|<i class="str ico p2"></i>|<i class="str ico p3"></i>|<i class="str ico p4"></i>|
  | link lnk <tt>|<i class="lnk ico"></i>|<i class="lnk ico p1"></i>|<i class="lnk ico p2"></i>|<i class="lnk ico p3"></i>||
  | check chk <tt>|<i class="chk ico"></i>|<i class="chk ico p1"></i>|<i class="chk ico p2"></i>|<i class="chk ico p3"></i>|<i class="chk ico p4"></i>|
  | mark mrk <tt>|<i class="mrk ico"></i>|<i class="mrk ico p1"></i>|<i class="mrk ico p2"></i>|<i class="mrk ico p3"></i>|<i class="mrk ico p4"></i>|
  </details>

- 
  <details><summary>回転・反転 クラス</summary>

  基本は矢印アイコン用ですが, 変形用クラスを使えばテキストや絵文字にも使えます
  `ico` `icon` または `transform` `trf` `tfx` などのクラスと以下のクラスを同時に指定します
  回転は上方向から45度ずつ時計回りです

  | (`ico`&#x7c;`tfm`) + クラス名| 表示サンプル | 方向 |
  | - | - | :-: |
  | `up` `u`<br>`d0` `d-360` | <i class="up ico arr t-m"></i> <i class="up ico mark c-grn"></i>&nbsp;<s class="up trf">🐔</s>&nbsp;<u class="up tfx">テキスト</u>| 0度|
  | `up right` `u r`<br>`d45`| <i class="up right ico arr"></i> <i class="up right ico mark c-grn"></i>&nbsp;<s class="up right trf">🐔</s>&nbsp;<u class="up right tfx">テキスト</u>| 45度|
  | `right` `r`<br>`d90`| <i class="right ico arr"></i> <i class="right ico mark c-grn"></i>&nbsp;<s class="right trf">🐔</s>&nbsp;<u class="right tfx">テキスト</u>| 90度|
  | `down right`<br>`d r` `d135`| <i class="down right ico arr"></i> <i class="down right ico mark c-grn"></i>&nbsp;<s class="down right trf">🐔</s>&nbsp;<u class="down right tfx">テキスト</u>| 135度|
  | `down` `d`<br>`d180`| <i class="down ico arr"></i> <i class="down ico mark c-grn"></i>&nbsp;<s class="down trf">🐔</s>&nbsp;<u class="down tfx">テキスト</u>| 180度|
  | `down left`<br>`d l` `d225`| <i class="down left ico arr"></i> <i class="down left ico mark c-grn"></i>&nbsp;<s class="down left trf">🐔</s>&nbsp;<u class="down left tfx">テキスト</u>| 225度|
  | `left` `l`<br>`d270`| <i class="left ico arr"></i> <i class="left ico mark c-grn"></i>&nbsp;<s class="left trf">🐔</s>&nbsp;<u class="left tfx">テキスト</u>| 270度|
  | `up left`<br>`u l` `d315`| <i class="up left ico arr"></i> <i class="up left ico mark c-grn"></i>&nbsp;<s class="up left trf">🐔</s>&nbsp;<u class="up left tfx">テキスト</u>| 315度|
  ||||
  | `flip-lr` `f-rl`<br>`flip-horizontal`<br>`f-horz` `left-right`| <i class="flip-lr ico arr"></i> <i class="flip-lr ico mark c-grn"></i>&nbsp;<s class="flip-lr trf">🐔</s>&nbsp;<u class="flip-lr tfx">テキスト</u>| 左右<br>反転 |
  | `flip-ud` `f-du`<br>`flip-vertical`<br>`f-vert` `uo-down`| <i class="flip-ud ico arr"></i> <i class="flip-ud ico mark c-grn"></i>&nbsp;<s class="flip-ud trf">🐔</s>&nbsp;<u class="flip-ud tfx">テキスト</u>| 上下<br>反転 |

  回転と反転を併用した場合, 回転後に反転したような表示になります
  `<b class="tfm d45 f-lr big">🐤</b>` <i class="ico arr r hl"></i> <b class="tfm d45 f-lr big">🐤</b>
  </details>

- 
  <details><summary>枠線 クラス</summary>

  `<div>` 要素で `box` `frame` `border` 等と以下のクラスを併用します
  内部でマークダウン記法を使うには*1行空ける*必要があります

  #### 枠線の種類
  <div class="box solid">

  `solid` `single` 一本線
  `<div class="box solid"> ～ </div>` 
  </div>
  <div class="frame double">

  `double` `dbl` `w` 二重線
  `<div class="frame double"> ～ </div>` 
  </div>
  <div class="border dotted">

  `dotted` `dot` 点線
  `<div class="border dotted"> ～ </div>` 
  </div>
  <div class="box dashed">

  `dashed` `dash` `dsh` 破線
  `<div class="box dashed"> ～ </div>` 
  </div>
  <div class="box cross">

  `cross` `crs` `x` 交差線
  `<div class="box cross"> ～ </div>` 
  </div>
  <div class="box interlace">

  `interlace` `inter` `il` 交差枠
  `<div class="box interlace"> ～ </div>` 
  </div>
  <div class="box pipe">

  `pipe` `tube` `wide` 隙間の広い二重線
  `<div class="box pipe"> ～ </div>` 
  </div>

  #### 枠線の太さ
  <div class="box dbl thick">

  `thick` 枠線を太くします
  `<div class="box dbl thick"> ～ </div>` 
  </div>
  <div class="box il thin">

  `thin` 枠線を細くします
  `<div class="box il thin"> ～ </div>` 
  </div>

  <div class="box cross dot b-blu">

  `cross` `interlace` `pipe` は<br/>`double` `dotted` `dashed` と併用可能です  
  `<div class="box cross dot b-blu"> ～ </div>`
  </div>
  </details>

-
  <details><summary>配置 クラス</summary>

  |クラス名|内容|
  |-|-|
  | a-left a-l <tt>| 全体的に左寄せ |
  | a-center a-c <tt>| 全体的に中央 |
  | a-right a-r <tt>| 全体的に右寄せ |
  ||
  |||
  | f-left f-l<tt>|<u class="f-left b-blu">左端配置</u> <wbr> |
  | f-right f-r<tt>|<u class="f-right b-red">右端配置</u> <wbr> |
  
  `a-left` `a-center` `a-right` クラスを持つ要素があれば、その段落/ブロック内のすべてが左/中/右配置化
  <u class="f-l b-blu">左</u> `f-left` `f-right` はその要素だけを左端/右端へ配置します <u class="f-r b-red">右</u>

  段落内に
  <s class="a-c">`<s class="a-c"></s>` があると</s>
  こんな感じです
  </details>
&nbsp;


### スライドメニュー <a name="mdcsmp_6s"></a>
スライドメニューっぽいものも不可能じゃなさそうです
ただし既存のカスタムCSSで `div.MarkdownRender` およびその子の `div` 要素の<i class="mk-red">スタイルが変更されてると上手く固定できません</i>

上手く出来てればメモ画面右上に「**&#x2630;**」が張り付いてると思います
マウスカーソルを乗せるとメニューが出てきます

<details><summary>スライドメニュー DIY</summary>

まず以下のような三重`div`要素の構造を用意します
~~~~md
<div class="slide-menu">  <!-- 1.メニュー土台 -->
<div>                     <!-- 2.メニュー本体 -->

  <!-- A.ここはスクロールしない -->
<div>  <!-- 3.メニュー内スクロール領域 -->

  <!-- B.ここにメニューの中身 -->
</div>
</div>
</div>
~~~~
1. ここに`slide-menu`クラスを設定します
2. これがメニュー本体になります
   `data-thumb`属性を設定すると、その内容がツマミ？部分に表示されます
   `data-thumb`未設定時は「&#x2630;」が表示されます
3. この中にメニューの内容を記述します
   最初に1行空ける事で、マークダウン記法を使えます
1. <u class="fade code" data-mark="A. "></u>省略可、スクロールさせない内容を記述できます
1. <u class="fade code" data-mark="B. "></u>メイン、高さが収まりきらなければスクロール可能になります
<br/>

「TOC」として作成するならこんな感じです
~~~~md
<div class="slide-menu">  <!-- 1.メニュー土台 -->
<div data-thumb="目次">   <!-- 2.メニュー本体 -->

  ### Table Of Contents
<div>  <!-- 3.メニュー内スクロール領域 -->

  - [section-1](#anc1)
  - [section-2](#anc2)
  - [section-3](#anc3)
</div>
</div>
</div>
~~~~
ただし、これだけではTOCとして機能しません
ジャンプ先に `<a name="anc1"></a>` 等を仕込んでおく必要があります

・・・**『メモ』**でやるような内容じゃないです
</details>
<br/>


### アニメーションクラス <a name="mdcsmp_6a"></a>
`anime/markdownNotesAnime.css` が存在すれば使えるアニメーションエフェクトのクラスです
目立ちはするので、アクセントなどに使えるのかも知れません

不用な場合は該当ファイルを削除等してください

<details><summary>アニメーション クラス</summary>

  以下のクラスのいずれかと、アニメ指定クラスのどれかを同時に指定して使用します
  `loud` `buzz` `dazz` `bling` `flash` `vivid` `attention`
  ~~~~md
  <s class="loud star">あにめ</s>
  ~~~~

  #### アニメ指定クラス
  サンプルはチェックONでアニメします
  |クラス名|サンプル<wbr class="t-m -stripe">|
  |--|--|
  | circle<tt class="">| <label><input type="checkbox" class="chk_anime"> <u class="big buzz circle">🐝 circle</u></label> |
  | vortex<tt class="">| <label><input type="checkbox" class="chk_anime"> <u class="big buzz vortex">🐝 vortex</u></label> |
  | tempo<tt class="">| <label><input type="checkbox" class="chk_anime"> <u class="big buzz tempo">🐝 tempo</u></label> |
  | mop<tt class="">| <label><input type="checkbox" class="chk_anime"> <u class="big buzz mop">🐝 mop</u></label> |
  | knead<tt class="">| <label><input type="checkbox" class="chk_anime"> <u class="big buzz knead">🐝 knead</u></label> |
  | cutoff stop no<tt class="">| <label><input type="checkbox" class="chk_anime"> <u class="big buzz stop">🐝 cutoff</u></label> |
  | bee<tt class="">| <label><input type="checkbox" class="chk_anime"> <u class="big buzz bee">🐝 bee</u></label> |
  |||
  | zoom<tt class="b-red">| <label><input type="checkbox" class="chk_anime"> <u class="big buzz zoom">🐶 zoom</u></label> |
  | gum goma gummy<tt class="b-red">| <label><input type="checkbox" class="chk_anime"> <u class="big buzz gum">🐶 gum</u></label> |
  | spring jump<tt class="b-red">| <label><input type="checkbox" class="chk_anime"> <u class="big buzz jump">🐶 spring</u></label> |
  | beat<tt class="b-red">| <label><input type="checkbox" class="chk_anime"> <u class="big buzz beat">🐶 beat</u></label> |
  | jerry<tt class="b-red">| <label><input type="checkbox" class="chk_anime"> <u class="big buzz jerry">🐶 jerry</u></label> |
  | back<tt class="b-red">| <label><input type="checkbox" class="chk_anime"> <u class="big buzz back">🐶 back</u></label> |
  |||
  | side slide<tt class="b-grn">| <label><input type="checkbox" class="chk_anime"> <u class="big buzz side">🐸 side</u></label> |
  | lift updown<tt class="b-grn">| <label><input type="checkbox" class="chk_anime"> <u class="big buzz lift">🐸 lift</u></label> |
  | near<tt class="b-grn">| <label><input type="checkbox" class="chk_anime"> <u class="big buzz near">🐸 near</u></label> |
  | square<tt class="b-grn">| <label><input type="checkbox" class="chk_anime"> <u class="big buzz square">🐸 square</u></label> |
  | star<tt class="b-grn">| <label><input type="checkbox" class="chk_anime"> <u class="big buzz star">🐸 star</u></label> |
  |||
  | flap<tt class="b-blu">| <label><input type="checkbox" class="chk_anime"> <u class="big buzz flap">🐔 flap</u></label> |
  | door<tt class="b-blu">| <label><input type="checkbox" class="chk_anime"> <u class="big buzz door">🐔 door</u></label> |
  | clock<tt class="b-blu">| <label><input type="checkbox" class="chk_anime"> <u class="big buzz clock">🐔 clock</u></label> |
  | swing seesaw<tt class="b-blu">| <label><input type="checkbox" class="chk_anime"> <u class="big buzz swing">🐔 swing</u></label> |
  |||
  | holo aura glow<tt class="b-ylw">| <label><input type="checkbox" class="chk_anime"> <u class="big buzz holo">🐵 holo</u></label> |
  | rainbow spectrum<tt class="b-ylw">| <label><input type="checkbox" class="chk_anime"> <u class="big buzz rainbow">🐵 rainbow</u></label> |
  |||
  |hole <tt class="b-aqa">| <label><input type="checkbox" class="chk_anime"> <u class="big buzz hole">🐷 hole</u></label> |
  |stripe <tt class="b-aqa">| <label><input type="checkbox" class="chk_anime"> <u class="big buzz stripe">🐷 stripe</u></label> |
  |curtains <tt class="b-aqa">| <label><input type="checkbox" class="chk_anime"> <u class="big buzz curtains">🐷 curtains</u></label> |
  |slit <tt class="b-aqa">| <label><input type="checkbox" class="chk_anime"> <u class="big buzz slit">🐷 slit</u></label> |
  |tunnel <tt class="b-aqa">| <label><input type="checkbox" class="chk_anime"> <u class="big buzz tunnel">🐷 tunnel</u></label> |
  |||
  | ghost<tt class="b-ppl">| <label><input type="checkbox" class="chk_anime"> <u class="big buzz ghost">👻 ghost</u></label> |
  | blink<tt class="b-ppl">| <label><input type="checkbox" class="chk_anime"> <u class="big buzz blink">👻 blink</u></label> |

  #### オプション指定クラス
  |クラス名|サンプル<wbr class="t-m -stripe">|
  |--|--|
  | fast<tt class="b-org">| <label><input type="checkbox" class="chk_anime"> <u class="big buzz side fast">🐇 fast</u></label> |
  | slow<tt class="b-org">| <label><input type="checkbox" class="chk_anime"> <u class="big buzz side slow">🐢 slow</u></label> |
  |||
  | reverse rev<tt class="b-gry">| <label><input type="checkbox" class="chk_anime"> <u class="big buzz clock reverse">👽 reverse</u></label> |
  |||
  | linear flat<tt class="b-mgt">| <label><input type="checkbox" class="chk_anime"> <u class="big buzz side linear">⛵ linear</u></label> |
  | ease flow inertia<tt class="b-mgt">| <label><input type="checkbox" class="chk_anime"> <u class="big buzz side ease">🐟 ease</u></label> |
  | steps strobe<tt class="b-mgt">| <label><input type="checkbox" class="chk_anime"> <u class="big buzz side strobe">🦐 steps</u></label> |

  #### アニメーション停止スイッチ
  同ブロックか段落内に以下のようなチェックボックスがあれば、チェックがONの時だけ動作します
  ~~~~md
  <input type="checbox" class="chk_anime" />
  ~~~~
  クラス `chk_anime` が重要です
  チェックボックスが無い場合、<label><i class="flash beat swing">***ずっと動き続けます***</i> <input type="checkbox" class="chk_anime"></label>

  ----
  アニメ指定は、背景色が異なるグループなら同時指定可能です
  <label><input type="checkbox" class="chk_anime"> <u class="dazz tempo jump">tempo🐹jump</u></label>

  また、以下のようにすれば重ねがけもできます
  ~~~~md
  <u class="dazz clock"><u class="buzz door b-ble">clock🐠door</u></u>
  ~~~~
  <label><input type="checkbox" class="chk_anime"> <u class="dazz clock"><u class="buzz door b-ble">clock🐠door</u></u></label>
</details>
<br/>


## 設定 <a name="mdcsmp_7"></a>
`markdownNotes.css` の250行目辺り・・・
~~~~md
--noteL0: 13px;
~~~~
これが基本フォントサイズの指定です
値を変更する事でメモ全般の文字サイズが変わります
(要：vivaldi再起動)

その他お好みでご自由に編集してください😉
<br/>


<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
## ライセンス情報 <a name="mdcsmp_l"></a>  
> このソフトウェアはCC0 1.0 (パブリックドメイン宣言) で公開されています。  
> 自由にご利用いただけますが無保証です。  
> 詳細は https://creativecommons.org/publicdomain/zero/1.0/ をご覧ください。
