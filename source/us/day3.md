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
こんにちは。Maaya([@maaya8585](https://twitter.com/maaya8585))です。最後のコラムでは、Outstanding PyLady Awardにまつわるお話です。
今年はPyLadiesの新しい取り組みとして、Outstanding PyLady Awardが設立され、その授賞式がPyCon US内で行われました。授賞式の様子についてはすでに本記事内で紹介されているので、私からは受賞式までのアレコレを書きたいと思います。

私の元にPyLadies Global Concil からメールが届いたのは3月の半ばのこと。PyLadiesの設立者であるLynn Rootさんから直接メールが届きました。「Outstanding PyLady Award 2024 に受賞しましたよ！おめでとう！PyCon US 2024の中で授賞式をやるのでぜひ来てください」とのこと。もうびっくりです。2024年の1月から2月にかけてノミネーションを行っていたことは知っていましたが、まさか自分自身が受賞するなんて夢にも思っていなかったのです。

実はこの受賞のお知らせをもらうまではPyCon US 2024には参加する予定がなかったのですが、せっかくいただいた賞の授賞式があるとのことで、スケジュールを調整して慌ててPyCon USに参加することにしました。

PyCon US 参加初日にLynn Rootさんとお会いし、受賞者用のピンバッチをいただきました。このピンバッチをネームタグにつけてPyCon USに参加していたのですが、以外とみなさん気づいてくださり、「そのアワードは何？」「すごいね！おめでとう！」など会話のきっかけになったり、お褒めの言葉をいただいたりして、初参加の身としては大変ありがたいツールとなりました。

```{figure} images/award_pin.jpg
:alt: Award ピンバッチはネームタグの上の方に装着しました。かわいい。
```

Outstanding PyLady Awardの授賞式自体はPyCon US クロージング付近ではありましたが、PyLadies オークションやPyLadies LunchonなどのPyCon US内で企画されていたPyLadiesイベントの中でも、本アワードの内容と受賞者のアナウンスをしていただきました。ほめられ慣れてない系の人間なので、お祝いの言葉や拍手をいただくたびに恥ずかしさ80％嬉しさ20％くらいの気持ちだったのですが、直接祝っていただけたことやたくさんの方に話しかけていただいてお友達が増えたことなどを思い返すと、受賞できてよかったな、PyCon US来てよかったな、と嬉しい気持ち100%で今を迎えています。

```{figure} images/award_gem.jpg
:alt: 宝石型のトロフィーいただきました。Lynnさん曰く「PyLadiesのメインカラーの赤にしたかったんだけど、そうするとRubyになってしまうから・・・」とのことで青になったそうです。
```

今回の受賞およびPyCon US 2024への参加を通じて、様々な国のPyLadies事情を聴いたり、意見交換したりできたことはも大変有意義でしたし、いままでオンライン上でしか会ったことのなかったPyLadiesのみなさんとも直接お話ができたことそのものが貴重な体験でした。

今回は個人として受賞させていただいていますが、当然一人で成せたものではなく、毎月一緒にイベント運営したりイベントに参加してくれるPyLadies Tokyoのみなさん、一緒にPyLadies Caravanを盛り上げてくれてるみなさん、やりたいとおもったことをできるようサポートしてくださるPyCon JPのみなさんなどなどたくさんの方のおかげでいただけた賞だと思っています。本当にありがとうございました。引き続きPythonコミュニティを盛り上げられたらいいなと思います。これからもよろしくお願いします。
```
