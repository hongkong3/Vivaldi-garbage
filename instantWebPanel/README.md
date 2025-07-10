# インスタントWebパネル
[vivaldi]: https://vivaldi.com/ "Powerful. Personal. Private."
[![REQUIRE: Vivaldi](https://img.shields.io/static/v1?label=vivaldi&message=utils&color=ef3939&logo=vivaldi)][vivaldi]&nbsp;
[![CC0 1.0Universal](https://img.shields.io/static/v1?label=license&message=CC0&color=28c)](https://creativecommons.org/publicdomain/zero/1.0/ "CC0 1.0Universal")&nbsp;
![version 2.21](https://img.shields.io/static/v1?label=version&message=2.21&color=2a2 "version: 2.21")&nbsp;
<br/>
ウェブページを一時的にWebパネルに表示するためのHTMLファイルです  
ローカルのHTMLファイルをWebパネルとして登録し、一時表示用の容れ物として使うような感じです  

Zipファイルは [instantWenPanel_v2.21.zip](https://github.com/hongkong3/MyStorage-vivaldi/releases/download/iwp-v2.21/instantWebPanel_v221.zip) です  
<br/>

## 使い方
  1. ウェブパネルにこのHTMLファイルを登録し表示します  
  2. 画面上部の入力欄に目的のページのURLを入力します  
  3. Enterキーやフォーカス移動でそのページが表示されます  

### 元のページに戻す
  ウェブパネルナビゲーションの **ホームへ移動 ボタン** で戻せます  
  ※ 以前はできたサイドバー出し入れによる初期化はできなくなってます…  
<br/>

## リンクを追加
  "LINK" 部分にマウスカーソルを乗せると出る **\[+\] ボタン** で追加します  
  使用頻度の低い *Webパネルページ* をまとめる事ができます  
  |入力項目|内容|
  |-|-|
  |URL address|  リンク先のURL (必須)|
  |link name|    リンクの表示名<br/>先頭に `--- `が在ればリンクの上に区切り線を追加<br/>末尾に `---` が在ればリンクの下に区切り線を追加|
  |icon image|   ファビコン用画像, 自動取得とかは無理です<br/>Base64やencodeURIをデータURIとして指定も可能です<br/>  例: `data:image/png;base64,***`|

### リンクのインポート・エクスポート
  入力欄に`@import`でインポート, `@export`でエクスポートできます  
  `instantWebPanel_link.csv` として出力します
<br/>

## メモ
  ページ下部はメモとして使えます  
<br/>

- - - - - - - -
> このソフトウェアはCC0 1.0 (パブリックドメイン宣言) で公開されています。  
> 自由にご利用いただけますが無保証です。  
> 詳細は https://creativecommons.org/publicdomain/zero/1.0/ をご覧ください。  
