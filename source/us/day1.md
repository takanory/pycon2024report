# カンファレンス1日目

カンファレンス1日目です。
ホテルからカンファレンス会場への道は、過去に参加したクリーブランド、ソルトレイクシティよりちょっとだけ怖いなって感じがありました（特になにも事件はありませんでしたが）。
とはいえ、夜でも複数人なら全然問題なく歩ける感じです。

## WelcomeとPSFからの報告

```{admonition} 削除予定
* video: <https://events.hubilo.com/pycon-us-2024/session/234271>
* https://stream.mux.com/InaO95Gqswk52RKZOd53BcXpla9cq5XQNuV006teK9Tk/high.mp4
* PSF Welcome video: <https://events.hubilo.com/pycon-us-2024/session/234272>
* https://stream.mux.com/9a0101sF8HlsCYHLvIbAGnQb024TvXxU5DQ26no007vT4jw/high.mp4
```

カンファレンスのオープニングは2023に続いてConference ChairであるMariatta（[@mariatta](https://twitter.com/mariatta)）氏からのあいさつです。
オープニングの最初の方で「PyCon USコミュニティメンバーからのメッセージ動画」が流れました。
私もこのインタビュー動画に出演しており、自分が出るのを待っていたんですが、ダイジェスト版のようで私は出ませんでした。残念。
フルバージョンはこちらです（[Get ready for PyCon US 2024! Tips and tricks from our community.](https://www.youtube.com/watch?v=RL3HFj5SDqI&t=451s)）。

```{figure} images/opening.jpg
:width: 400px

Mariatta氏によるオープニング
```

今年の説明スライドは「PyCon US v2024 Release Notes」というタイトルで、ソフトウェアのリリースノートになぞらえているのがおしゃれだなと思いました。
オープニングではPSFのスタッフ、100名以上のボランティアの主催メンバーに感謝が述べられました。
プロポーザルの数は973件と過去最大とのこと、トークが通るのはかなり狭き門です（私も落ちました）。
参加登録は2738名+オンライン395名とこちらも過去最大に迫る数とのことです。

以下のスライドは「Hatchery Program」という今年実験的に行うイベントの紹介です。
FlaskCon、Documantation SummitなどがRoom 317で行われるという案内です。

```{figure} images/hatchery.jpg
:width: 400px

Hatchery Program
```

Mariatta氏によるあいさつに続いて、PSFのExecutive Directorである[Deb Nicholson](https://www.python.org/psf/records/staff/)氏からのオープニングトークです。
例年はPSFからの報告はクロージング前とかなので、このタイミングでPSFからの話があるのは意外でした。

まず、Pythonは1日に3億ダウンロード、PyPIは2023年は1年で3840億ダウンロードとすごい数がダウンロードされているという説明がありました。
また、助成金として2023年は697,000ドル（約1.1億円）とたくさんの金額で世界中のPythonコミュニティをサポートしているという説明がありました。
ものすごい金額です。

```{figure} images/grants.jpg
:width: 400px

PSFからの助成金
```

昨年東京で開催された[PyCon APAC 2023](https://2023-apac.pycon.jp/)もPSFから助成金のサポートを受けていました。
Pythonに関するミートアップやイベントの開催を考えている人は、[PSF Grants Program](https://www.python.org/psf/grants/)に申請してみることをおすすめします。

## Keynote: Jay Miller

```{admonition} 削除予定
* video: <https://events.hubilo.com/pycon-us-2024/session/234273>
* https://stream.mux.com/SyApTSMqX00ldiXsAhrzWZgriwSQlQbArwm015pmeH5dE/high.mp4
```

一番最初のキーノートはJay Miller氏によるものです。
Jay氏は2014年からPythonコミュニティに関わっているメンバーで、サンディエゴのPythonコミュニティメンバーでもあります。

Jay氏は自身も黒人であり以前からPyCon USに参加しているが「ステージで発表している黒人は数人しか見たことがない」という話からはじまりました。
黒人の参加者もそれほど多くなく、見つけたときに「どこかで発表をしたことはあるか？」と質問すると、返ってくる答えは「PyCon USに仕事を探しに来た」というものがほとんだそうです。
筆者も2023年を含めて過去3回PyCon USに参加しましたが、確かに黒人のスピーカーはほとんど見たことがないなと思いました。
  
```{figure} images/jay.jpg
:width: 400px

Jay Miller氏
```

そこで、黒人のPythonコミュニティのヒーローが生まれるとよいと考え、[Black Python Devs](https://blackpythondevs.com/)というコミュニティを立ち上げたとのことです。
このコミュニティはGnome Foundationのサポートを受けており、メインの活動はオンラインです。
現在は南北アメリカ、アフリカ、ヨーロッパなどから425名のメンバーが参加するコミュニティにまで育ったそうです。

世界に散らばるリーダーによって運営されており、PSFの助成金（Grants）により4人のリーダーがはじめてPyCon US 2024に参加したとのことです。
こういうところにも助成金が使われているのかと思いました。
また、トークの最後の方で「コミュニティをサポートするために寄付をしてほしい」という話がありました。
この寄付はPyCon USの会期中に目標額の5,000ドルを超えたようです。

筆者自身はアジア人として参加して、アジアからの参加メンバーは確かにそれほど多くないと感じていました。
もっとたくさん参加するといいなと思いますし、そのための動きがなにかできるとよいのかも知れません。
また、数年後のPyCon USでは黒人のスピーカーがたくさん増えているかも知れないなと思いました。

## Making Your Documentation Interactive with PyScript

* [Making Your Documentation Interactive with PyScript](https://us.pycon.org/2024/schedule/presentation/92/)
* スピーカー: Jeff Glass
* スライドとデモ: [Making Your Documentation Interactive with PyScript](https://jeff.glass/post/pycon-talk-2024/)

このトークでは、Sphinxなどで書いたHTMLのドキュメントに[PyScript](https://pyscript.net/)を導入し、インタラクティブなドキュメントにする方法について紹介していました。
PyScriptの基本的な動作原理と導入方法について解説し、次にpy-editorを紹介しました。
py-editorを導入するとHTMLの中でPythonコードを書いて実行することができるようになります。

* [Python editor - PyScript](https://docs.pyscript.net/latest/user-guide/editor/)

```{figure} images/pyscript.jpg
:width: 400px

PyScriptを導入
```

またpy-editorはそれぞれ独立したインタープリターが動作します（メモリ空間が別）が、environmentを使用すると共有できるようになります。
またconfigurationで設定すると任意のURLをファイルシステムのように使用できます。CSVファイルを読み込む例が紹介されていました。

Python製の静的サイトジェネレーターである[Sphinx](https://www.sphinx-doc.org/en/master/)、[MkDocs](https://www.mkdocs.org/)にそれぞれPyScriptを導入する拡張機能も紹介していました。

* [Sphinx PyScript documentation](https://sphinx-pyscript.readthedocs.io/en/latest/)
* [JeffersGlass/mkdocs-pyscript: Use PyScript in mkdocs](https://github.com/jeffersglass/mkdocs-pyscript)

私はSphinxでドキュメントを書いて公開することはよくあり、[Python Boot Camp Text](https://pycamp.pycon.jp/)にうまくPyScriptを入れられないかなと思いました。
今度ぜひ挑戦してみたいと思います。

PyScriptについてはPython Monthly Topicsの以下の記事も参考にしてください。

* [WebブラウザでPythonが動作する！PyScriptの詳解](https://gihyo.jp/article/2023/04/monthly-python-2304)
  
````{admonition} PyCon APACコミュニティブース
このコラムは一般社団法人PyCon JP Association理事の寺田([@terapyon](https://twitter.com/terapyon))がお届けします。

[PyCon JP Association](https://www.pycon.jp/)は、[PyCon APAC（アジア太平洋地域）](https://pycon.asia/)のコミュニティの一員として活動をしています。
PyCon APACは2010年から毎年、アジア太平洋地域のいずれかの国で開催しているイベントです。[昨年2023年は東京で開催](https://2023-apac.pycon.jp/)しました。[今年はインドネシアのYogyakarta](https://2024-apac.pycon.id/)で開催されます。

PyCon USにはコミュニティーブースがあり、昨年に引き続きPyCon APAC コミュニティーでもブースを設置しました。

私達のブースでは、APAC地域でPyConが多く開催されていることを紹介し、今年のPyCon APAC 2024が10月末にインドネシアで開かれていること、さらに興味を持ってくれた地域があれば、それぞれのPyConの特徴などを紹介しました。

各国でPyConの主催を中心的に行っているメンバーたちが集まり、日本はもちろん、韓国、台湾、インドネシア、インドの方々で時間のある時にはブースに居て説明員をするという形で行いました。
今年は、ブース用にTシャツを作りAPACチームとしての一体感を出すように運営しました。

```{figure} images/booth-t-shirt.jpg
:width: 400px

PyCon APAC Tシャツで記念撮影
```

ブースにはノベルティとして、各国からのお菓子が置かれブースに立ち寄ってくれた方に配布しました。日本からは抹茶のキットカットを持っていたのですが大変好評でした。他にもPyCon APAC 2024のステッカーを配布したり、PyCon APAC地域のイベントスケージュールが書かれた「折り紙」を配布しました。この折り紙を2枚使うと手裏剣ができあがり、PyCon JPとPyCon APACのWebサイトURLのQRコードがでるようにしたものも配布しました。折り紙は情報としてのチラシの役割と共に手裏剣になるというギミックに興味を持ってもらえました。

ブースには多くの方に立ち寄っていただき、APAC地域にこんなにPyConがあるのかという感想を多く聞けて良かったです。

```{figure} images/booth-1.jpg
:width: 400px

PyCon APACブース
```
````

## Ruff: An Extremely Fast Python Linter and Code Formatter, Written in Rust

* [Ruff: An Extremely Fast Python Linter and Code Formatter, Written in Rust](https://us.pycon.org/2024/schedule/presentation/22/)
* スピーカー: Charlie Marsh

このトークではPythonのリンター、フォーマッター、コード変換ツールである[Ruff](https://docs.astral.sh/ruff/)の中身について、作者自ら語るというものでした。
どのようにしてRuffを速くしているのか、ただRustを使っているだけではないさまざまな工夫があることが解説されました。

速くするためにすべてのファイルを並行で処理

全部のファイルを並行処理と並列処理で処理しているという説明がありました。
また、データでかならず判断するということで、実装した結果でパフォーマンスが上がったどうかを細かく計測していることが紹介されました。

改善の例として整数の解析処理について説明がありました。
Pythonでは整数の長さに制限がありませんが、Rustの整数は固定長です。
当初は整数の文字列を見つけたら `Vec<u32>` とベクター形式にして大きい整数に対応していましたが、常にこの形式で領域を確保するのは無駄です（ほとんどの整数は小さいため）。
そこで、整数の長さを見て通常は `u64` を使用して、大きな整数のときのみ `Vec<u32>` を使うように変更し、パフォーマンスを改善したとのことです。

```{figure} images/ruff.jpg
:width: 400px

整数の解析処理
```

他にも、`#noqa` のコメントを判別する方法を、正規表現から専用のLexarに変更してパフォーマンスが改善されたとのことです。
Pythonのパーサー（構文解析器）を専用コードからパーサーの生成ツールでRustのコードを生成するようにして、Pythonの変更にも対応しやすくなり、パフォーマンスも改善したとのことです。

Ruffは速いと思っていましたが、ただRustで書いただけじゃなく、地道に改善して今の爆速なツールになっているんだなと、非常に関心しました。
  
RuffについてはPython Monthly Topicsの以下の記事も参考にしてください。

* [新しい静的コード解析ツール「Ruff」をご紹介](https://gihyo.jp/article/2023/03/monthly-python-2303)

````{admonition} 初めて登壇の体験
このコラムは青野 高大([@koxudaxi](https://github.com/koxudaxi))がお届けします。

私は人生初のイベント登壇を経験しました。

トークの内容はデコレータと型アノテーションのベストプラクティスについてで、タイトルは「[Enhancing Decorators with Type Annotations: Techniques and Best Practices](https://us.pycon.org/2024/schedule/presentation/42/)」でした。

PyCon USには毎年多くのトークプロポーザルが提出されるため、トークが採用されるにはテーマ選びが非常に重要にです。
私は前回もプロポーザルを提出しましたが残念ながら落選してしまいました。そのため、今回は約二ヶ月間毎日テーマについて熟考しました。
私にとって、PyCon USでの登壇準備で最も難しい部分は、このプロポーザルの作成でした。

これまで社内のオンライン会議での発表は経験がありましたが、リアルイベントでのプレゼンテーションの経験はありませんでした。
スライドについてもオンラインとは勝手が違い、プロジェクターに映すためにフォントサイズを大きくしなければならず、サンプルコードをわかりやすく掲載するのに苦労しました。
また、私は人前で話すことが苦手ということもあり、トークが始まるまでは緊張と不安でいっぱいでした。
それでも、できる限りの準備をし、発表直前まで何度も予行練習を行いました。

実際に話し始めると会場の皆さんが熱心に私の話に耳を傾けてくれたおかげで、自信を持って最後までトークをやりきることができました。
登壇後もトークの話題をきっかけに、たくさんの人と交流を広げることができ、イベント中はとても楽しい時間を過ごせました。

これまでOSSのコントリビューターとして活動してきましたが、登壇を通じて、開発者として現場で直接役立つ知識を共有する重要性を改めて感じました。
GitHubでスターをもらうのも嬉しいですが、トークに対する直接のお礼や感想をいただけるとさらに嬉しいです。

私のトークを支えてくれた運営メンバーや友人、そして多くの来場者の方々に心から感謝いたします。

```{figure} images/koudai_aono_talk.jpg
:width: 400px

登壇中の様子
```

````

## ライトニングトーク

カンファレンスに参加していると、ランチ後の13:30頃に「Congrats! Your PyCon US lightning talk for Friday @ 6:00pm has been selected!」というタイトルのメールが届きました。
昨日ボードに書き込んでおいた私のライトニングトークが選ばれたようです！！うおおおおおおお！！

というわけで午後はトークは少しだけ聞いて、自分のライトニングトークの練習に時間を使うようにしました。
今回はスクリプト（台本）は用意せずにしゃべる、ということにチャレンジしてみました。
そのため、どういうことをどういう英語でしゃべるか、ということを覚えながら練習を繰り返しました。

発表内容は、単語がスペースで分割されていない、漢字の読みが複数種類あるといった、日本語の難しいところを最初に説明し、Pythonの日本語形態素解析ライブラリを使って日本語を学ぶときのサポートをできるかも？といったものです。スライドは以下に公開しています。

* スライド：[Learn Japanese 🇯🇵 with Python](https://slides.takanory.net/slides/20240517pyconus/)


```{figure} images/takanory-lt.jpg
:width: 400px

ライトニングトークで発表
```

Pythonのプログラムで日本語の分かち書きや、読みを取得するところ、Amazon Pollyで音声を取得するところをコード例で紹介し、最後にそれらを使った簡単なデモアプリで動作を見せました。
ライトニングトークの短い時間（5分）でのデモはドキドキですが、なんとか時間内にうまくできたと思います。
PCから音声を流すというところもバッチリできたと思います。
サンプルアプリは以下に置いてますが、[Streamlit](https://streamlit.io/)を初めて使ってみましたが、サクッとほしい感じのものが作れて便利だなと感じました（行きの飛行機の中でだいたい作りました）。

* デモアプリのリポジトリ：[takanory/learn-jp-with-python](https://github.com/takanory/learn-jp-with-python)

その後数人から「LTよかったよ」「面白かった」みたいに声をかけられたので、そういう意味でも発表してよかったなと思いました。

他のライトニングトークでは韓国のSoojin氏が、PyCon APAC 2023をきっかけにPyLadies Seoulをリブートした話がありました。
PyCon APAC 2023の中でPyLladies Tokyoが女性参加者と交流するイベントをやっており、そのつながりがきっかけとなって国を越えてひろがっていくのはとても良いなと思いました。

```{figure} images/soojin.jpg
:width: 400px

Soojin氏のライトニングトーク
```

## ほぼなにもないHappy HourとHelltown Brewing

この日のビールは企業主催のHappy Hourパーティに参加したんですが、行くのが遅くほぼ食事は終わっており、無料ビールもなくなっていました。
しょうがないので1杯だけ自分で払ってビールを飲んで、日本人数名と友人のJason一家とその友達と一緒に、[Helltown Brewing](https://www.helltownbrewing.com/)で飲み直すことにしました。
このお店は食事がないため、同行していたmaayaさんにUber eatsで肉とイモなどを頼んでもらい、なんとか飢えをしのぐことができました。

```{figure} images/ubereats.jpg
:width: 400px

揚げたトリと揚げたイモ
```

このお店にはボードゲームやカードゲームがいくつか置いてあり、デカいUNOをみんなでやりました。
UNOやるの久しぶりすぎてルールをあまり覚えておらず、他の人に「これ出していいの？」と確認しながらのプレイでしたが、飲みながらゲームするのなんか楽しいですね。

```{figure} images/uno.jpg
:width: 400px

デカいUNO
```

こんな感じでカンファレンス1日目は幕を閉じました。
