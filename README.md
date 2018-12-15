## IchigonQuest じゅもん・どうぐ一覧

IchigonQuest で使用できる命令を一覧しています。\
中間コードの仕様上、じゅもん 以外に\
どうぐ での代入・計算も含めてあります。

Download ZIP でファイル一覧をダウンロードできます。\
GitHub・Git を使っている場合は Clone を使っても良いでしょう。

RAW で参照した場合、またファイルをダウンロードした場合\
.txt ファイルは文字コード UTF-8、改行コード CR+LF になります。\
Windows ではメモ帳を使用する事が可能です。

* IchigonQuest (公式) http://ichigonquest.shizentai.jp/
* IchigoJam (公式) http://ichigojam.net/
* イチゴジャム レシピ (公開元) https://15jamrecipe.jimdo.com/

## バージョン表記

頭にあるじゅもん・どうぐ名の下に対応バージョンを入れています。
入れていない場合は初版 0.5.0 から対応しています。

## 中間コード

IchigonQuest では、プログラムを中間コードで保存しています。\
つうしん はこの中間コードを送受信します。\
この項目で特に記載がない数字は 10 進数表記です。

基本的に 1 行で 8 バイト使用し、64 行分 512 バイト固定で送出します。\
なし の部分は 0（16 進数 00）ですが、将来的に数値が入る可能性があり、\
解析する場合は無視するのが良いでしょう。\
プログラム終了後の空いた部分は 255（16 進数 FF）で埋められます。\
2 バイトは 下位 16 ビット 上位 16 ビット の順です。

* ID:   1 バイト
* 種類: 1 バイト
* 値1:  2 バイト
* 値2:  2 バイト
* 値3:  2 バイト

種類はビットで次の状態です。

* 下位 2・1 ビット: 値1 の種類（00=かず | 01=はこ | 10・11＝予備）
* 下位 4・3 ビット: 値2 の種類（00=かず | 01=はこ | 10・11＝予備）
* 下位 6・5 ビット: 値3 の種類（00=かず | 01=はこ | 10・11＝予備）
* 下位 8・7 ビット: 予備

かずを指定した場合、該当する値はそのまま数値が入ります。\
はこを指定した場合は次の値となります。

0=はこ# | 1=はこA | 2=はこB | 3=はこC | 4=はこD | 5=はこE | 6=はこF | 7=はこG
