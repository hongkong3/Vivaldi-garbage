# メモパネル-マークダウン用 - カスタムCSS
[![REQUIRE: Vivaldi](https://img.shields.io/static/v1?label=vivaldi&message=6.4?&color=ef3939&logo=vivaldi)][vivaldi]&nbsp;
[![CC0 1.0Universal](https://img.shields.io/static/v1?label=license&message=CC0&color=28c)](https://creativecommons.org/publicdomain/zero/1.0/ "CC0 1.0Universal")&nbsp;
![version 3.04](https://img.shields.io/static/v1?label=version&message=3.04&color=2a2 "version: 3.04")&nbsp;
<br/>

[vivaldi]: https://vivaldi.com/ "Powerful. Personal. Private."

> 🍙 This README is written in Japanese only.  Please use a translation tool if needed.  

  [Vivaldiブラウザ][vivaldi]のメモパネル機能を、**Markdownメモ** として使い倒そうというカスタムCSSです  
  * メモパネルの「マークダウン表示」に特化したCSSです  
    マークダウン表示を使用されない場合はほぼ無意味です  
    一部 *インラインHTML* も併用します  
  * あくまでメモパネル用です、***タブで開く「メモ」は別物*** です  

ダウンロード用のZipファイルは [css_markdownNotes_v304.zip](/../../raw/master/.releases/css_markdownNotes_v304.zip) です  
<br/>

- [インストール方法](#インストール方法)  
- [本CSSによる調整内容](#本cssによる調整内容)  
- [ライセンス情報](#ライセンス情報)
- - - - - - - -

## インストール方法
  1. まずVivaldiの「オリジナルカスタム UI」機能（所謂 カスタムCSS）を有効化する必要があります  
     この辺を参考に有効化してください  
     > [Tip \#9 | Vivaldi のユーザーインターフェースの見た目をカスタム CSS で変更する方法](https://vivaldi.com/ja/blog/tips/desktop-tips/tip-9/ "Tip \#9 | Vivaldi Browser")  
     > [【Vivaldi】カスタムCSSの導入方法。自由にカスタマイズしてみよう！ | ナポリタン寿司のPC日記](https://www.naporitansushi.com/vivaldi-css/ "【Vivaldi】カスタムCSSの導入方法。自由にカスタマイズしてみよう！ | ナポリタン寿司のPC日記")  
  
  2. 設定したCSSフォルダ内へ `markdownNotes.css` を移動します  
     - アニメーションクラスも使用する場合は `anime/markdownNotesAnime.css` もフォルダごと同じ場所へ移動させてください
  3. Vivaldiブラウザを再起動します  

  - 同梱の `sample/css_sample.md` をメモパネルにインポート（または内容をメモにコピペ）して「マークダウン表示」でご覧ください  
    動作サンプル兼仕様書となっております  
<br/>


## 本CSSによる調整内容
  見た目の調整やインラインHTMLによるクラス指定を使った自家拡張などをしてます  
  着色用クラス以外に固定色は使っておらず、テーマに沿った色あいになるようにしてます  

- **エディター画面** (メモパネルのテキスト表示)  
  等幅フォント・自動折り返しなし  
  <br/>

- **マークダウン表示画面**  
  UI用ではなくウェブページ用フォントで表示  

- 文字装飾  
  *\*斜体\** + 文字色変更、**\*\*太字\*\*** + サイズアップ、~~\~\~取消線\~\~~~ + 淡色化  
  `[リンク](# "ツールチップ")` のリンク先が `#_-+*!?` のどれか一文字だけなら、注釈としてツールチップ表示のみ行います  

- 見出し  
  Lv1～3 や Lv2～4 の見出しを、階層型の番号付き見出し にできます  

- リスト  
  階層型番号リスト・ツリーリスト・リストマークなしのリスト・リストマークを絵文字等に変更  

- 引用ブロック  
  定義リスト風・カード風 にできます  

- テーブル  
  デフォルトで、ヘッダ行スクロール・偶数行の色分け・カーソル行を着色 します  
  オプションとして、任意のセルをヘッダセル化・枠線の有無・フッタ行スクロール化・左端列のスクロール化 なども指定できます  

- インラインHTML  
  定義リスト`<dl><dt><dd>`・折りたたみブロック`<details><summary>` の表示調整  
  `<b>` `<i>` `<q>` `<s>` `<u>` `<tt>` はクラス指定用に *スタイルリセット* してます  
  行末が `<wbr>` なら改行を打ち消します  

  - 装飾用クラス  
    文字色・背景色・マーカー・バーメーター・アイコン・枠線 などのクラスがあります  

  - アニメーション用クラス  
    `anime/markdownNotesAnime.css` を追加インストールする事で使えるクラスです  
    動きます、**メモ**としては不要です

<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>

## ライセンス情報  
> このソフトウェアはCC0 1.0 (パブリックドメイン宣言) で公開されています。  
> 自由にご利用いただけますが無保証です。  
> 詳細は https://creativecommons.org/publicdomain/zero/1.0/ をご覧ください。  
