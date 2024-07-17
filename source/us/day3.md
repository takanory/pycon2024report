# カンファレンス3日目

PyCon US 2024レポートの3回目は、カンファレンス3日目とスプリントの様子をお伝えします。
カンファレンス3日目はCPythonのコア実装についてトークを中心に聴きました。
またクロージングでは驚きの表彰がありました。
スプリントでは1日開発を行って、筆者のPyCon USが終了しました。

## ライトニングトーク

* 動画: [Lightning Talks - May 19, 8pm - YouTube](https://www.youtube.com/watch?v=qXr--LBHWtY)

カンファレンス3日目のライトニングトークは朝にのみ行われます。
ここで、毎年恒例のPyCon、Pythonイベント紹介のライトニングトークがあります。
これは世界各国のPyConやPython関連イベントを、1イベント1枚のスライドで、リレー形式で紹介をするライトニングトークです。
PyCon JP 2024の紹介は共同座長である吉田さんが行いました。
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
いくつかの企業がブースを出しており、就職を希望している人が企業の担当者と直接話をするというものです。
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
また、Ken Jin氏は2021年からCPythonのコアデベロッパーでもあるそうです。
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

スピーカーのAnthony Shaw氏はCPythonをはじめさまざまなOSSの開発者であり、[CPython Internals](https://realpython.com/products/cpython-internals-book/)の著者でもあります。
日本のPyConにも参加したことがあり、PyCon APAC 2023ではPython 3.12のサブインタープリターについての発表をしていました。

```{figure} images/anthony.jpg
:width: 400

Anthony Shaw氏
```

最初のこのトークの前提条件として、いくつかのトークやドキュメントが提示されました。
JITのトークについてはこの記事で紹介したものです。

* [PyCon US 2023 - Eric Snow talk on sub interpreters](https://www.youtube.com/watch?v=3ywZjnjeAO4)
* [EuroPython 2022 - Sam Gross talk on free-threading](https://www.youtube.com/watch?v=9OOJcTp8dqE)
* PyCon US 2024 - "Sync vs Async in Python" happening right now
* PyCon US 2024 - Building a JIT compiler for CCython
* PyCon US 2024 - Overcoming GIL with sub interpreters and immutability
* "Parallelism and Concurrency" chapter from [Python Internals](https://realpython.com/products/cpython-internals-book/)
* My Masters Thesis [doi.org/10.25949/23974764.v1](https://doi.org/10.25949/23974764.v1)

最初に丸めた紙をPickleされたデータに見立てて、それを会場に投げて処理してもらって並列でタスクを実行する例について説明していました。なかなか面白いアプローチです。

Pythonでの並列実行についてスレッド、コルーチン、マルチプロセッシング、サブインタープリターの4つを提示し、それぞれの特徴メリットデメリットについて紹介しました。
複数のCPUコアを使用する場合はマルチプロセッシングかサブインタープリターとなります。

CPython 3.11まではプロセス全体にGILが1つだけありましたが、3.12からはインタープリターごとにGILが存在するようになります。
Python 3.12で4コアCPUで200桁と2000桁のπの計算を例で見てみると、スレッドは200桁だと速い（0.04秒）ですが2000桁だと一番遅く（2.37秒）なります。
サブインタープリターでは200桁だと0.05秒ですが、2000秒だと0.63秒とかなり速く処理されます。
マルチプロセッシングでは処理のオーバーヘッドがサブインタープリターより少し遅くなります。
サブインタープリターは「オーバーヘッドが少なくメモリを共有しているマルチプロセッシング」のようなものと述べられていました。

ここからフリースレッドの話になりますが、Python 3.13からはGIlを無効にできるようになります。
GITを削除するためには以下の手順で進めるそうです。現在は3番目のステップの最中で、時間がかかります。

1. GILを削除する
2. メモリ確保とガベージコレクターを変更する
3. GILが存在するすべてのCのコードを修正する

Python 3.13のベータ版でGILを有効/無効にしたものでπを2000桁まで計算する場合で速度を比較してみると、スレッドは高速（2.41秒→0.75秒）になりましたが、サブインタープリター（0.76秒→0.99秒）とマルチプロセッシング（1.2秒→1.57秒）では少しずつ遅くなります。
GILをオフにすると、現状は少し遅くなります。

まとめとして、マルチプロセッシングに対してサブインタープリターはよりよい解決策となるということ、フリースレッディングはデータ交換のためのスレッドプールより良い解決策となるということが語られました。
ただし、Pythonはスレッドを安全に使うためにGILに依存してました。
そのため、GILを削除すると予測しない方法で壊れてしまう可能性があるとのことです。

GILの削除はすぐにはデフォルトにならないと思いますが、CPythonのコアが徐々に変わっていっているということが理解できました。

## Steering Council Panel

* 動画: [Python Steering Council Panel - YouTube](https://www.youtube.com/watch?v=81ZpbKdlvh0)
* スピーカー：Barry
 Warsaw、Emily Morehouse、Pablo Galindo Salgado、Thomas Wouters、Gregory P. Smith

Python Steering Councilは投票によって選ばれた5名による委員会で、Python言語とCPythonインタープリターの品質を安定性の維持や、PEP（Python拡張提案）の決定をPythonのコア開発者やPSFと連携して行っています。
Steering Council Panelはこの5名の委員が現在や今後のPythonについて共有します。

```{figure} images/council.jpg
:width: 400

Steering Councilメンバー
```

Steering Council Panelは毎年投票によって選出されます。
Guido氏がBDFLを退任したときに、コア開発者が集まって議論しガバナンスモデルを提案しました。
そして結果として現在のSteering Councilモデルとなりました。
ガバナンスモデルについては以下のPEPに書いてあります。

* [PEP 13 – Python Language Governance](https://peps.python.org/pep-0013/)

現在のCouncilメンバーは以下の所属となっており、所属もバラバラです。
同じ会社のメンバーは2名までという制限があるそうです。

* Thomas Wouters - Google
* Pablo Galindo Salgado - Bloomberg
* Gregory P Smith - Employer TBD
* Emily Morehouse - Cuttlesoft
* Barry Warsaw - NVIDIA

PSFの資金を使用してCPythonの開発のためにさまざまな活動を行っています。
Developers in ResidenceとSecurity Developer in Residenceは、PSFがフルタイムで雇用する技術者で、現在5名います。
新たにSteering Councilの秘書を雇ったそうです。たしかにいろいろな作業がありそうなので、秘書がいると助かりそうです。
また、年次のコアデベロッパースプリントを開催しているそうです。
年に1回、世界中のコアデベロッパーが集まり、一週間CPythonの開発を行います。

Steering Councilと連携してさまざまなワーキンググループが活動しているそうです。
Ptyhonドキュメントの編集委員会、C APIのワーキンググループ、型ヒントのガバナンスが紹介されました。
詳細は以下のPEPを参照してください。

* [PEP 732 – The Python Documentation Editorial Board](https://peps.python.org/pep-0732/)
* [PEP 731 – C API Working Group Charter](https://peps.python.org/pep-0731/)
* [PEP 729 – Typing governance process](https://peps.python.org/pep-0729/)

次に2024年10月にリリース予定のPython 3.13について説明がありました。
Python 3.13では主要な新機能、新言語仕様、新モジュールはありません。
大きな変更点としては、[PEP 594](https://peps.python.org/pep-0594/)による使われていない標準ライブラリの削除、多くの非推奨の関数とクラスの削除、プライベートC関数の削除があります。

型ヒントでの変更は以下です。

* [PEP 696 – Type Defaults for Type Parameters](https://peps.python.org/pep-0696/)
* [PEP 702 – Marking deprecations using the type system](https://peps.python.org/pep-0702/)
* [PEP 705 – TypedDict: Read-only items](https://peps.python.org/pep-0705/)
* [PEP 742 – Narrowing types with TypeIs](https://peps.python.org/pep-0742/)

またPython 3.13では新しい対話モードが導入されました。
シンタックスハイライト、複数行の編集やペーストに対応しています。

他にJITコンパイラについても紹介されました。

最後にCPythonでGILをオプションにする件について説明がありました。

* [PEP 703 – Making the Global Interpreter Lock Optional in CPython](https://peps.python.org/pep-0703/)

長いゴールとしては、フリースレッドのビルドのみとなるのは5年以上先とのことです。
後方互換性の維持をすること、またサードパーティのコードをGILがないビルドに対応させる必要があることが語られました。
「これはPython 4ではない」ということを強調して伝えていました。

```{figure} images/notpython4.jpg
:width: 400

This is not going to be Python 4
```

フリースレッド機能は3つのフェーズに分けて進めるとのことです。
フェーズ1ではビルドオプションで可能になり、デフォルトではインストールされません。
フェーズ2はAPIとABIが安定した時点からとなり、コミュニティでのテストなどのサポートが必要です。
フェーズ3ではフリースレッドでのビルドがデフォルトとなりますが、当初は無効化も可能にします。将来的にはGILありのビルドの削除についても議論するとのことです。

かなり丁寧にフリースレッドについて進めるということが認識できました。
また、Python 4の予定がないことを強調して伝えていたことが印象的でした。
  
## Python Software Foundation Update

* 動画: [Python Software Foundation Update - YouTube](https://www.youtube.com/watch?v=RXQWud5y__A&t=168s)
* スピーカー：Deb Nicolson、Lynn Root

クロージングの前にPSF UpdateとしてPSFの活動の話がありますが、最初に「PyLadies Community Awards」についての話がありました。
壇上にはPyLadiesのChairであるLynn Root氏がいます。
PyLadiesは女性向けのPythonコミュニティで、現在世界中に250以上の支部があります。
また、昨夜のPyLadiesオークションでは60,000ドルの寄付を集めました。
これはいままでの最高記録だそうです。

そして10月に開催された[PyLadiesCon](http://conference.pyladies.com/)のあとにCheuk Ting Ho氏が「Outstanding PyLady Award」について提案し、実施することになったそうです。
初めてのOutstanding PyLady Awardには84件のノミネートが集まり、その中から3名の受賞者が選ばれLynn Root氏から紹介、表彰されました。

1人目のAbigail Dogbe氏は2017年にPyLadies Ghanaを立ち上げ、彼女とそのコミュニティはリベリア、エチオピア、ザンビアなど8つのPyLadies支部に影響を与えたそうです。他にもDjangoCon USでの基調講演なども行っているそうです。
2人目のJessica Greene氏はベルリンのPyLadies支部を6年以上運営し、インドのデリーなど他の支部にも影響を与えたそうです。他にもPython Pizza Hamburgの運営もしているそうです。
最後に3人目のMaaya Ishida氏は[PyLadiesの東京支部に](https://tokyo.pyladies.com/)10年以上係わっており、日本全国のPyLadiesとつながることを目的とした[PyLadies Caravan](https://tokyo.pyladies.com/caravan/index.html)も主催しています。またPyCon Hong Kongで基調講演を行っており、[PyCon JP Associationの理事](https://www.pycon.jp/committee/board.html)でもあります。

PyCon JPやPython界隈で筆者も一緒に活動しており友人でもあるMaayaさんが、初めてのPyLady Awardを受賞する1人となりました。
ものすごくびっくりしましたし、いままでの継続的な活動が認められたんだと思う、とても喜ばしいことだと感じました。

```{figure} images/pylady-award.jpg
:width: 400

左からPyLady Awardを受賞したMaaya氏、Jessica氏、Abigail氏
```

最後にスポンサーと、今年のPyCon USのChairであるMariatta氏へ感謝を述べて、次のChairであるElaine氏を紹介しました。
そしてPSFのスタッフが壇上に揃い、参加者から拍手が送られました。
ちなみに、左から3人目の青いシャツの人が、私に「Hoopy Frood」のリボンをくれたSalt氏です。

```{figure} images/psf-staff.jpg
:width: 400

PSFスタッフのみなさん
```

````{admonition} Outstanding PyLady Award
こんにちは。Maaya([@maaya8585](https://twitter.com/maaya8585))です。最後のコラムでは、Outstanding PyLady Awardにまつわるお話です。
今年はPyLadiesの新しい取り組みとして、Outstanding PyLady Awardが設立され、その授賞式がPyCon US内で行われました。授賞式の様子についてはすでに本記事内で紹介されているので、私からは受賞式までのアレコレを書きたいと思います。

私の元にPyLadies Global Council からメールが届いたのは3月の半ばのこと。PyLadiesの設立者であるLynn Rootさんから直接メールが届きました。「Outstanding PyLady Award 2024を受賞しましたよ！おめでとう！PyCon US 2024の中で授賞式をやるのでぜひ来てください」とのこと。もうびっくりです。2024年の1月から2月にかけてノミネーションを行っていたことは知っていましたが、まさか自分自身が受賞するなんて夢にも思っていなかったのです。

実はこの受賞のお知らせをもらうまではPyCon US 2024には参加する予定がなかったのですが、せっかくいただいた賞の授賞式があるとのことで、スケジュールを調整して慌ててPyCon USに参加することにしました。

PyCon US 参加初日にLynn Rootさんとお会いし、受賞者用のピンバッチをいただきました。このピンバッチをネームタグにつけてPyCon USに参加していたのですが、以外とみなさん気づいてくださり、「そのアワードは何？」「すごいね！おめでとう！」など会話のきっかけになったり、お褒めの言葉をいただいたりして、初参加の身としては大変ありがたいツールとなりました。

```{figure} images/award_pin.jpg
:alt: Award ピンバッチはネームタグの上の方に装着しました。かわいい。
:width: 400

Award ピンバッチはネームタグの上の方に装着しました。かわいい
```

Outstanding PyLady Awardの授賞式自体はPyCon US クロージング付近ではありましたが、PyLadies オークションやPyLadies LunchonなどのPyCon US内で企画されていたPyLadiesイベントの中でも、本アワードの内容と受賞者のアナウンスをしていただきました。ほめられ慣れてない系の人間なので、お祝いの言葉や拍手をいただくたびに恥ずかしさ80％嬉しさ20％くらいの気持ちだったのですが、直接祝っていただけたことやたくさんの方に話しかけていただいてお友達が増えたことなどを思い返すと、受賞できてよかったな、PyCon US来てよかったな、と嬉しい気持ち100%で今を迎えています。

```{figure} images/award_gem.jpg
:alt: 宝石型のトロフィーをいただきました。Lynnさん曰く「PyLadiesのメインカラーの赤にしたかったんだけど、そうするとRubyになってしまうから・・・」とのことで青になったそうです。
:width: 400

宝石型のトロフィーをいただきました。Lynnさん曰く「PyLadiesのメインカラーの赤にしたかったんだけど、そうするとRubyになってしまうから・・・」とのことで青になったそうです
```

今回の受賞およびPyCon US 2024への参加を通じて、様々な国のPyLadies事情を聴いたり、意見交換したりできたことも大変有意義でしたし、いままでオンライン上でしか会ったことのなかったPyLadiesのみなさんとも直接お話ができたことそのものが貴重な体験でした。

今回は個人として受賞させていただいていますが、当然一人で成せたものではなく、毎月一緒にイベント運営したりイベントに参加してくれるPyLadies Tokyoのみなさん、一緒にPyLadies Caravanを盛り上げてくれてるみなさん、やりたいと思ったことをできるようサポートしてくださるPyCon JPのみなさんなどなど、たくさんの方のおかげでいただけた賞だと思っています。本当にありがとうございました。引き続きPythonコミュニティを盛り上げられたらいいなと思います。これからもよろしくお願いします。

詳細についてはPyLadiesのブログも参照してください。

* [Inaugural Winners of the Outstanding PyLady Award – PyLadies](https://pyladies.com/blog/Inaugural-Winners-of-the-Outstanding-PyLady-Award/outstanding-pylady-winners/)
````

## Closing

* 動画: [PyCon US 2024 Closing - YouTube](https://www.youtube.com/watch?v=05VZ5-YXBGQ)

クロージングではChairのMariatta氏から、予算、トーク数、登録者数などを2023年と比較して報告が行われました。
登録者数は2736名、実際に参加した数は2551名、初参加は1752名だそうです。
65%が初参加とのことで、初参加の比率が高いなと感じました。
Travel Grant（旅費支援）は351,436 ドル（約5600万円）と、ものすごい金額です。
筆者も旅費をTravel Grantを受け取っており、非常に助かっています。

```{figure} images/attendees.jpg
:width: 400

PyCon US 2024の参加者数
```

そしてPyCon US 2025と2026のChairであるElaine Wong氏にバトンタッチされ、今後のPyCon USについての紹介が行われました。
PyCon US 2025はピッツバーグで5月中旬のほぼ同じ時期に開催されます。

```{figure} images/elaine.jpg
:width: 400

Elaine Wong氏
```

そしてPyCon US 2026はカリフォルニア州のロングビーチで開催されることが発表されました。
ロサンゼルスからアクセスしやすいので、これはディズニーランド（の中のスターウォーズ）に行くしかないな、と個人的に思いました。

```{figure} images/longbeach.jpg
:width: 400

PyCon US 2026の開催場所はロングビーチ！
```

こうして、PyCon US 2024の3日間のカンファレンスは無事に終了しました。
  
## アジアメンバーでビールパーティー

この日は韓国のSeongsoo Choから「クロージングが終わったらみんなで飲みに行こう！」という連絡がありました。
調べてみたところ提案されたピザの店は午後8時に閉まってしまうので、ちょっと遠いけど[Aslin Beer CoのPittsburgh Taproom](https://www.aslinbeer.com/pittsburg)に行くことになりました。
最終的には、日本、台湾、韓国メンバーを中心に20人以上が集まって、みんなでワイワイとビールを飲んで交流しました。
明日帰国する人もいるので、大人数で集まって飲むのもこの日が最後です。
みんなでPyCon USの思い出や、また会おうねという話をしました。

```{figure} images/aslin-beer.jpg
:width: 400

みんなでワイワイとビール
```

このお店は結構広く、別のテーブルにはラテン系のPyCon US参加者のテーブルができていました。
ヨーロッパからの参加者もいるため、寺田さんがEuroPythonにも参加する青野高大さんを紹介していました。
青野さんはそのままそっちのテーブルに居座って、こちらのテーブルには戻ってきませんでした。
ラテンのノリと性格が合うのかも知れません。
