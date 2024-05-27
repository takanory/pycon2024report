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
* discordでセキュリティ問題があった?
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
  
```{admonition} (いい感じのコラムタイトルにしてね)
(maaya担当)

PyLady Awardのはなしとか
```
