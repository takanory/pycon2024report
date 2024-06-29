# Day 3

## Lightlint Talk

## Keynote: Kate Chapman

* OpenStreetMap
* つなみ
* インドネシアの政府で仕事

## PSF - Meet our Security Engineers

* hoge
  * Security Developer-in-Residence
  * Alpha-Omegaのスポンサー
* Mike
  * PyPI Safety & Security Engineer
  * スポンサー: AWS
* 昨年PSFに参加した
* PyPIのセキュリティ対応したブログを書いた
* discordでセキュリティ問題があった?     Meet our Security Engineers


* next
  * CPythonの方でも見ていく?
  
## Poster session, Job Fair

## JIT

* Brandt Bucker
* 2021からCPython Fasterチーム
* 2023年にJIT実装
* 3.13で "micro-op" インタープリターが "hot" なコードを最適化して実行する
* フィボナッチの関数を例に説明
* Copy-And-Patch Compilation
* できあがったbytecodeを配列に入れて再利用する
* PRP 659:
* PEP 744: JIT Compilation
* `--enable-experimental-ji` オプションを付けてbuild

## How two undergrads from the other side of the planet are speeding up your future code

* https://us.pycon.org/2024/schedule/presentation/1/
* Ken Jin, Jules Poon
* 基本的なBytecodeとかスタックのはなしからはじまる
* 3.11 Specialising Interpreter
* コンパイラとかのクラスが大学にある

## Unlocking the Parallel Universe: Subinterpreters and Free-Threading in Python 3.13

* https://us.pycon.org/2024/schedule/presentation/128/
* Anthony Shaw
* 丸めた紙(pickle)を会場に投げてタスクを実行するイメージを伝える。面白い
* Python 3.13 でGILをdisableにできる
* Python 3.13を `./configure --disable-gil --experimental-gil` でbuild
* hypercornの後ろにFlaskでログイン画面作って、リクエストを素早く処理できるようになった

## Keynote: Sumana Harihareswara

* PyPI(?)のプロジェクトマネージャーとして、サイトを更新していったはなし?

## Steering Council Panel

* Steering Councilの説明
* SCはPSFとは独立している
* Steering Council SecretaryをFundして雇っている
  * Velda Kiara
* coredevの移動費とかも持っている
* CouncilとWorking Groupについて
  * Documatation Editorial Board
	* docs.python.org, devguide, translations
  * C API Work Groupができた
  * PEP 729 Typing Governance Process
	* Useful, Useable, Stable
* What's Expected in Python 3.13
  * PEP 594 で古いモジュールを削除
  * Type Annotation
  * Platform support: iOS, Android, Apple Silicon
  * new REPL: ペーストが便利になってる?F2でヒストリー
  * JIT
* Free threading
  * PEP 703
  
## Python Software Foundation Update

* Deb Nicolson
* PyLadies Commuynity Awards
  * 63,000 USD
  * 84名のノミネーション
  * PyLadies GhanaのAbigainlさん
  * PyLadies BerlinのJessica Greeneさん
  * PyLadies TokyoのMaaya Ishidaさん
* Fiscal Sponsores

## Closing

* トーク数
* 予算
* 参加者数
* Grants
  * 金額はだいふ増えた
* PyLadies item 29 -> 44
  * PyLadies Travel Grant
  
```{admonition} Outstanding PyLady Award
Outstanding PyLady Award は2024年1月にPyLadies Global Councilで新設され、世界中のPyLadiesの中からPythonコミュニティに広く貢献をした人を称えるアワードです。
2024年1月から2月の間にノミネーションが行われていたことは知っていましたが、まさか自分自身が受賞するとは思ってもいませんでした。
PyCon USではPyLadies Auction/PyLadies Luncheon/Closing の3回受賞アナウンスをしていただき、Closingでは青い宝石型の名前入りトロフィーもいただきました。みなさま、本当にありがとうございました。

今回の受賞およびPyCon US 2024への参加を通じて、様々な国のPyLadies事情を聴いたり、意見交換したりできたことは大変有意義でしたし、いままでオンライン上でしか会ったことのなかったPyLadiesのみなさんとも直接お話ができたことはとってもうれしかったです。

PyCon US(海外カンファレンス)ってちょっと怖いな、何喋ったらいいかわからないな、一人ぼっちにならないかな、女性いるのかな・・・不安は尽きないと思いますが、もし不安があるのであれば、一度PyLadiesに相談してみてください。日本にも海外にもPyLadiesがあります。私も今年PyLadiesのSlackでいろいろサポートいただいたのでフォローアップ体制はお墨付き。参加してみたい気持ちがあるなら行かないなんて選択肢はもったいない。会場ではPythonの知識共有だけではなく、驚くほどたくさんの人のつながりを体験できます。ぜひ、海外のPyConに訪れてみてください。
```
