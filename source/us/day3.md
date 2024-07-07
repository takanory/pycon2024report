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

スピーカーのAnthony Shaw氏はCPythonをはじめさまざまなOSSの開発者であり、[CPython Internals](https://realpython.com/products/cpython-internals-book/)の著者でもあります。
日本のPyConにも参加したことがあり、PyCon APAC 2023ではPython 3.12のサブインタープリターについての発表をしていました。

```{figure} images/anthony.jpg
:width: 400

Anthony Shaw氏
```

* [Parallel code with Python 3.12 sub-interpreters](https://2023-apac.pycon.jp/timetable?id=VNQKHW)

* 丸めた紙(pickle)を会場に投げてタスクを実行するイメージを伝える。面白い
* Python 3.13 でGILをdisableにできる
* Python 3.13を `./configure --disable-gil --experimental-gil` でbuild
* hypercornの後ろにFlaskでログイン画面作って、リクエストを素早く処理できるようになった

## Steering Council Panel

* 動画: [Python Steering Council Panel - YouTube](https://www.youtube.com/watch?v=81ZpbKdlvh0)
* スピーカー：Barry Warsaw、Emily Morehouse、Pablo Galindo Salgado、Thomas Wouters、Gregory P. Smith

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

他にJITコンパイラーについても紹介されました。

最後にCPythonでGILをオプションにする件について説明がありました。

* [PEP 703 – Making the Global Interpreter Lock Optional in CPython](https://peps.python.org/pep-0703/)

長いゴールとしては、フリースレッドのビルドのみとなるのは5年以上先とのことです。
後方互換性の維持をすること、またサードパーティのコードをGILがないビルドに対応させる必要があることが語られました。
「これはPython 4ではない」ということが強調して伝えられました。

```{figure} images/notpython4.jpg
:width: 400

This is not going to be Python 4
```

フリースレッド機能は3つのフェーズに分けて進めるとのことです。
フェーズ1ではビルドオプションで可能になり、デフォルトではインストールされません。
フェーズ2はAPIとABIが安定した時点からとなり、コミュニティでのテストなどのサポートが必要です。
フェーズ3でフリースレッドでのビルドがデフォルトとなりますが、当初は無効化も可能にします。将来的にはGILありのビルドの削除についても議論するとのことです。

かなり丁寧にフリースレッドについて進めるということが認識できました。
また、Python 4の予定がないことを強調して伝えていたことが印象的でした。
  
## Python Software Foundation Update

* 動画: [Python Software Foundation Update - YouTube](https://www.youtube.com/watch?v=RXQWud5y__A&t=168s)
* スピーカー：Deb Nicolson、Lynn Root

クロージングの前にPSF UpdateとしてPSFの活動の話がありますが、最初に「PyLadies COmmunity Awards」についての話がありました。
壇上にはPyLadiesのChairであるLynn Root氏がいます。
PyLadiesは女性向けのPythonコミュニティで、現在世界中に250以上の支部があります。
また、昨夜のPyLadiesオークションでは60,000ドルの寄付を集めました。
これはいままでの最高記録だそうです。

そして10月に開催された[PyLadiesCon](http://conference.pyladies.com/)のあとにCheuk Ting Ho氏が「Outstanding PyLady Award」について提案し、実施することになったそうです。
初めてのOutstanding PyLady Awardには84件のノミネートが集まり、その中から3名の受賞者が選ばれLynn Root氏から紹介、表彰されました。

1人目のAbigail Dogbe氏は2017年にPyLadies Ghanaを立ち上げ、彼女とそのコミュニティはリベリア、エチオピア、ザンビアなど8つのPyLadies支部に影響を与えたそうです。他にもDjangoCon USでの基調講演なども行っているそうです。
2人目のJessica Greene氏はベルリンのPyLadies支部を6年以上運営し、インドのデリーなど他の支部にも影響を与えたそうです。他にもPython Pizza Hamburgの運営もしているそうです。
最後に3人目のMaaya Ishida氏は[PyLadiesの東京支部に](https://tokyo.pyladies.com/)10年以上係わっており、日本全国のPyLadiesとつながることを目的とした[PyLadies Caravan](https://tokyo.pyladies.com/caravan/index.html)も主催しています。またPyCon Hong Kongで基調講演を行っており、[PyCon JP Associationの理事](https://www.pycon.jp/committee/board.html)でもあります。

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

こうして、PyCon US 2024は閉幕しました。

  
```{admonition} (いい感じのコラムタイトルにしてね)
(maaya担当)

PyLady Awardのはなしとか
```

## アジアメンバーでビールパーティー

* ビール飲みに行ったことを書く
* 別テーブルにラテン系が来た
* 寺田さんがこうだいさんを紹介した
