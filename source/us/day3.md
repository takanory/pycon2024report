# カンファレンス3日目

3回目はカンファレンス3日目とスプリントの様子をお伝えします。
カンファレンス3日目はCPythonのコア実装についてトークを中心に聴きました。
またクロージングでは驚きの表彰がありました。
スプリントでは1日開発を行って、PyCon USが終了しました。

## ライトニングトーク

* 動画: [Lightning Talks - May 19, 8pm - YouTube](https://www.youtube.com/watch?v=qXr--LBHWtY)

カンファレンス3日目のライトニングトークは朝にのみ行われます。
ここで、毎年恒例のPyCon、Pythonイベント紹介のライトニングトークがあります。
これは世界各国のPyConやPython関連イベントが、1イベント1枚のスライドを用意して、リレー形式で順番にイベント紹介をするライトニングトークです。
PyCon JPの紹介は共同座長である吉田さんが行いました。
写真を見ると吉田さんの右の方に、各イベントの主催者が列になって順番に並んでいるのがわかります。

```{figure} images/pyconus-yoshidalt.jpg
:width: 400

吉田さんのLTの様子
```

スライドだけ用意して主催者が来ていないイベントもあります。
その場合は司会のCheukさんがスライドの内容をもとにして代わりに発表していました。
アドリブ力が問われます。

## ポスターセッションとジョブフェア

PyCon USのカンファレンス3日目は10時から13時までの3時間はポスターセッションとジョブフェアのみとなります。

ポスターセッションはA0などの大きいサイズのポスターを掲示し、その内容について発表者と参加者がディスカッションをするといったイベントです。
今年は30件弱のポスター発表があったようです。
写真は[funix.io](https://github.com/TexteaInc/funix)という、Pythonの関数やクラスをWebアプリケーションにするライブラリです。

```{figure} images/poster.jpg
:width: 400

ポスター
```

ジョブフェアは求職のためのイベントです。
いくつかの企業がブースを出しており、修飾を希望している人がそこで話をするというものです。
以下の写真では[Sentry](https://sentry.io/)と[Plotly Technologies Inc](https://plotly.com/)が企業ブースを出しており、たくさんの人が話を聞いていました。

```{figure} images/jobfair.jpg
:width: 400

ジョブフェア
```

アメリカで仕事を探している人は、ジョブフェアに来ると企業の担当者と直接話ができるのでおすすめです。

## Building a JIT compiler for CPython

* [Building a JIT compiler for CPython](https://us.pycon.org/2024/schedule/presentation/124/)
* スピーカー：Brandt Bucher
* スライド：<https://github.com/brandtbucher/brandtbucher/blob/master/2024/05/19/building_a_jit_compiler_for_cpython.pdf>

スピーカーのBrandt Bucher氏は2021年からMicrosoftのFaster CPythonチーム（Pythonを高速化するチーム）に所属しています。
このチームの成果などにより、Python 3.11では25%高速化しました。
Brandt氏は2023年から実験的なJITコンパイラの実装をはじめたそうです（Brandt氏はPyCon JP 2021のキーノートスピーカーでもあります）。

* 動画: [\[PyCon JP 2021\] Day2 Keynote: A Perfect match (Brandt Bucher) - YouTube](https://www.youtube.com/watch?v=ggPJLwIbbyY)

```{figure} images/brandt.jpg
:width: 400

Brandt Bucker氏
```

まずJIT導入の背景として以下が述べられました（筆者はCPythonの内部には詳しくないので間違っていたらすいません）。

* CPython 3.11：適応型インタープリターがプログラムを分析し最適化する
* CPython 3.12：インターブリターの生成機能はDSLの仕様から解析と変更が可能になる
* CPython 3.13：micro-opインタープリターが「ホット」なコードを検出して最適化して実行する

以下の様なフィボナッチ関数のコードを例に、バイトコードとスタックの状態を使って説明が進められました。

```python
def fibonacci(n):
    a, b = 0, 1
    for _ in range(n):
        a, b = b, a + b
    return a	
```

`for` 文の箇所は通常は `FOR_ITER` というバイトコードになりますが、この場合は特殊なバイトコードの `FOR_ITER_RANGE` に置き換えられるそうです。
同様に `a + b` の箇所は `BINARY_OP` が `BINARY_OP_ADD_INT` となるそうです。
そしてバイトコードから生成された "micro-op" を最適化するという動作をするそうです。
しかし、この機能をONにするとオーバーヘッドが増加するため、20%遅くなるそうです。

そこで、JIT（ジャスト・イン・タイム）コンパイラが重要となります。
Pythonがさまざまなプラットフォームでの依存性を低くして、JITコンパイラを実現することは非常に難しいことです。
そこで、2021年に発表された「コピー&パッチ」という手法のJITコンパイラで実装を進めるそうです。
この手法は30ページの論文で、以下のURLで参照できます。
また、同じ著者によるブログ投稿も参考になるとのことです。
このブログではLua言語にコピー&パッチの手法でJITをゼロから実装しています。

* [Copy-and-patch compilation: a fast compilation algorithm for high-level languages and bytecode](https://dl.acm.org/doi/10.1145/3485513)
* [Building a baseline JIT for Lua automatically](https://sillycross.github.io/2023/05/12/2023-05-12/)

コピー&パッチの手法ではWebAssemblyのLiftoffコンパイラより、5倍速くコードを生成し、50%コードが速いそうです。
また、LLVMと比較すると100倍コード生成が速く、15%コードが速いそうです。

そしてCPython版のコピー&パッチの実装を進めており、現在はビルド時には1000行の複雑なPythonコード、100行の複雑なCのコードとLLVMを使用しています。
また、実行時には400行のシンプルなCのコードと、生成されたシンプルな9000行のCのコードのみで、システム依存はないとのことです。
そして、X86、X86-64とARM64のWindows、macOS、Linuxをサポートしています。

パフォーマンスとしては冒頭に述べたmicro-opインタープリターでは20%遅かったのですが、JITでは現状はCPythonと同じパフォーマンスで、10%ほど目盛りが余分に必要となるそうです。

詳細については以下のPEP（Pythonの拡張提案）にも記載されているので、そちらも参照してください。

* [PEP 659 – Specializing Adaptive Interpreter](https://peps.python.org/pep-0659/)
* [PEP 744 – JIT Compilation](https://peps.python.org/pep-0744/)

試して見たい方は、CPython 3.13のコードで以下の様に実行するとJITが有効となったpythonがビルドされます。

```bash
> Pbuild/build.bat --experimental-jit
$ ./configure --enable-experimental-jit
```

めちゃめちゃ難しい内容のトークでした。
CPythonの高速化としてJITがどうなっていくのか、今後に注目していきたいと思います。

## How two undergrads from the other side of the planet are speeding up your future code

* [How two undergrads from the other side of the planet are speeding up your future code](https://us.pycon.org/2024/schedule/presentation/1/)
* スピーカー：Ken Jin、Jules Poon

スピーカーのKen Jin氏とJules Poon氏はタイトルにもあるとおり大学の学部生です。
シンガポールの大学の中でCPythonのバイトコードの最適化にチャレンジしているという内容です。
また、Ken Jin氏は2021年はCPythonのコアデベロッパーでもあるそうです。
世界にはすごい人がいるなと感じました。

```{figure} images/kenjin.jpg
:width: 400

Jules Poon氏（左）とKen Jin氏
```

まずは過去の経緯から説明がありました。
2022年以前からKen氏はFaster CPythonチーム（CPythonの高速化チーム）の外部協力者として活動していました。
2023年1月から8月にかけて、2人は実験的なPyLBBV（CPython with lazy basic block versioning）の実装を進め、2023年12月まで第2弾の実装を進めました。
そして、このPyLBBVの最終バージョンのCPython 3.13への組み込みをKen氏が実施しました。
この日のトークではこの最終バージョンについて語るそうです。

背景としてCPythonはPythonをC言語で実装したものです。
そしてCPythonはバイトコードのスタックマシーンであり、Python言語をコンパイラでバイトコードに変換し、そのバイトコードをスタックに積んで処理しているというものです。
例として `(a + b) * c` というコードではどのようにバイトコードが生成され、スタックでどのように処理が行われるかの説明がありました。

```
 2 LOAD_GLOBAL  0 (a)
14 LOAD_GLOBAL  2 (b)
26 BINARY_OP    0 (+)
30 LOAD_GLOBAL  4 (c)
42 BINARY_OP    5 (*)
```

上記のバイトコードでは`a`、`b`、`c`の変数の型がわからず、`BINARY_OP` は動的に型を調査するため、処理が遅くなります。
そこでCPython 3.11のSpecialized Interpreterによって、`LOAD_GLOBAL_MODULE` や `BINARY_OP_ADD_INT` などの特殊なバイトコードによって処理を高速化しています。

CPython 3.11でのバイトコードの最適化は1つから2つのバイトコードに対して行われます。
CPython 3.13以降では実行時によく遭遇する型を学習し、より広い範囲で最適化を実施します。
これは新しいアイデアではないが、メンテナンスしやすく実装することが難しいとのことです。

CPython 3.13以降ではバイトコードからTraceを生成し、そのTraceがTier 2 Optimizerで最適化が行われるそうです。このTrace OptimizationsではKen Jin氏によって以下の最適化が実装中とのことです。協力者にはMark Shannon氏、Guido van Rossum氏、Peter Lazorochak氏がいます。それぞれ簡単に紹介します。

* Guard Elimination （3.13で一部実装済み）
* True Function Inlining （作業中）
* Deferred Object Creation （作業中）
* Register allocation/top of stack caching （作業中）

Guard Eliminationは、`a += b + b + b`というコードを実行するときに、`b`がintである場合に`(b + b) + b`を実行する前に両方の値がintかをチェックするGuardを削除するというものです。

True Function Inliningは、関数呼び出しにオーバーヘッドがあるのでインライン化して1つの大きい関数にするというものです。

Deferred Object Creationは、`[0, 1, 2, 3][3]`がリストを生成せずに`3`を返すというものです。
他にも `filter(lambda x: x%2, [1, 2, 3, 4, 5])`で中間のリストを生成せずにフィルターを返すというアイデアもあるそうです。

Register allocation/top of stack cachingは、スタックの上位にあるいくつかの項目をレジスターにキャッシュするというものです。これは、メモリーへのアクセスは遅く、レジスターへのアクセスはより速いためです。

最後になぜ2人がこの活動をしているかについての話がありました。
Ken氏は大学に入る前からCPythonでの活動を開始していたそうです。
大学の1学期で2人はMark Henz氏のもとでプログラミング言語実装を受講し、最初の実験的なPyLBBV実装をしました。
この開発を夏も続け、次の年にはManuel Rigger氏が2人のアドバイザーとなったそうです。
このように大学が提供している学生のメンターシップを最大限に利用しましょうと語っていました。
また、自分が必要とするクラスを取りましょうとも語っていました。

JITに続きめちゃくちゃ内容が難しいトークでした。
こんなすごいCPythonの実装を、シンガポールの大学生が行っているということに、非常に驚きました。
また、CPythonが地道に高速化するためにいろいろなことを行っていることを知りました。

トークが終わった後に2人にあいさつさせてもらい、「日本から来てPyCon JPをやってます。ぜひプロポーザルを出してね、旅費のサポートもあるよ！」とアピールしておきました。
PyCon JP 2024に2人の名前があったら個人的には胸アツです。

## Unlocking the Parallel Universe: Subinterpreters and Free-Threading in Python 3.13

* [Unlocking the Parallel Universe: Subinterpreters and Free-Threading in Python 3.13](https://us.pycon.org/2024/schedule/presentation/128/)
* スピーカー：Anthony Shaw

* 丸めた紙(pickle)を会場に投げてタスクを実行するイメージを伝える。面白い
* Python 3.13 でGILをdisableにできる
* Python 3.13を `./configure --disable-gil --experimental-gil` でbuild
* hypercornの後ろにFlaskでログイン画面作って、リクエストを素早く処理できるようになった

## Keynote: Sumana Harihareswara

* 動画: [Keynote Speaker - Sumana Harihareswara - YouTube](https://www.youtube.com/watch?v=JE5u5mUT6gQ)

* PyPI(?)のプロジェクトマネージャーとして、サイトを更新していったはなし?

## Steering Council Panel

* 動画: [Python Steering Council Panel - YouTube](https://www.youtube.com/watch?v=81ZpbKdlvh0)

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

* 動画: [Python Software Foundation Update - YouTube](https://www.youtube.com/watch?v=RXQWud5y__A&t=168s)

* Deb Nicolson
* PyLadies Community Awards
  * 63,000 USD
  * 84名のノミネーション
  * PyLadies GhanaのAbigainlさん
  * PyLadies BerlinのJessica Greeneさん
  * PyLadies TokyoのMaaya Ishidaさん
* Fiscal Sponsores

## Closing

* 動画: [PyCon US 2024 Closing - YouTube](https://www.youtube.com/watch?v=05VZ5-YXBGQ)

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
