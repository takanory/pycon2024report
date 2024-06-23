# カンファレンス2日目

カンファレンス2日目の様子をお伝えします。

## Diversity & Inclusionパネル

* スピーカー：Debora Azevedo、Dima Dinama、Jessica Greene、Jules、Mason Egger、Abigail Dogbe

2日目の朝はDiversity & Inclusionパネルです。
各国のコミュニティメンバーがパネリストとして登壇し、ディスカッションをするというよりは、それぞれの経験や考えを共有するということがメインに行われた印象でした。
アジアからはインドネシアのDima氏が登壇していました。
Dima氏はPyCon APAC 2023に参加してクロージングで「PyCon APAC 2024はインドネシア」とアピールしていたので、日本で見たことがある人もいると思います。
Dima氏は2019年にPyCon Indonesiaにボランティアとして参加し、2020年からリードオーガナイザーとして活動してきたとのこと。

```{figure} images/dima.jpg
:width: 400px

Dima氏
```

Abigail氏は0日目のパーティーで同じテーブルにいた方でした。
2017年にガーナで開催されたDjango Girlsに参加し、その後ガーナのPythonコミュニティやPyDataガーナに参加し、自らPyLadiesガーナを立ち上げたそうです。

挑戦したことや大変だったことは？という話では、Abigail氏はコミュニティを立ち上げるのは大変で、維持するのはもっと大変だということを語っていました。
Dima氏はPyCon始めたときにどうやってスポンサーや人を探すのかがわからなかった、PSFがカンファレンス開催に助成金を出してくれるのは本当に助かったと語っていました。
またブラジルではCOVID-19後、多くの小さなコミュニティが孤立し分裂している問題があるそうです。
またカンファレンスが健全な場となるために、安全な場所を作る必要があるという話が印象的でした。

国を超えても似たような課題もあれば、まったく異なる課題もあると感じるパネルでした。

## Keynote: Simon Willison

2日目のキーノートスピーカーのSimon Willison氏はDjangoの共同作成者ですが、この日はDjangoについてではなくLLM（大規模言語モデル）について話したい！ということでトークが恥じましたました。

* LLMについて話したい
* AIじゃなくてImitation intelligence
* どのモデルを使うのがいい?→ふんいき
* MLCChatがおすすめ
* llm.datasette.io
* <https://pypi.org/project/vosk/>
* 以前は考えられないようにプロジェクトを素早く作成できるのを助けてくれる
* PSFの投票ページをDatasetteのプロジェクトでデータセットにする?

````{admonition} 挑戦と反省：はじめてのPyCon US 2024登壇で得たもの

こんにちは、福田 隼也（[@JunyaFff](https://twitter.com/junyafff)）です。ここでは、初めて参加の「PyCon US」で登壇してきた話をコラムで紹介します。
私はカンファレンス2日目に「[Event-Driven asyncio: A Case Study of Trio's API](https://us.pycon.org/2024/schedule/presentation/142/)」というタイトルのトークをしました。

事前にスタッフの方より控室には20分前に、トークする部屋には10分前に入るように言われており、時間通りに会場に入りました。司会の方に挨拶をした後に、パソコンやマイクの設定を行い、いざ会場を見渡すと、広い部屋に見慣れた日本からの参加者数名の方しかいない状況でした。

司会の方と「人が少ないね」と話をしていると時間になり、司会の方が壇上でトークの紹介をしてくれました。すると途中から会場に参加者が増えてきました。あとから聞いた話では、キーノートが予定の時間よりも終わる時間が少し遅かったようで、そこからの移動だったようです。一安心してトークを進めることができました。

わたしのトークは、Pythonの非同期プログラミングライブラリ「[Trio](https://github.com/python-trio/trio)」のAPIを使ったプロダクションでの事例とコードの紹介です。

Pythonの非同期といえば標準ライブラリである `asyncio` が有名ですが、 今回のトークではよりシンプルで使いやすい `Trio` にフォーカスしました。なぜ `Trio` が使いやすいのか、なぜプロダクションでの採用したのか、また `Trio` を拡張した `trio-util` の `AsyncValue` というAPIにフォーカスを当てて紹介しました。
今回のトークに合わせ公開した、 `AsyncValue` のasyncio版であるライブラリ `asyncio-util` についても触れました。

ご興味がある方は以下のリンクをみてみてください。

* [登壇資料 - Speaker Deck](https://speakerdeck.com/jrfk/event-driven-asyncio-a-case-study-of-trios-api-pycon-us-2024)
* [trio_util.AsyncValue - Document](https://trio-util.readthedocs.io/en/latest/)
* [asyncio-util - GitHub](https://github.com/jrfk/asyncio-util)

実は去年Euro Python 2023でトークをした時[^euro]に、Pythonで非同期を利用されている方が多く驚いたのですが、「何に利用しているか」というのを聞くことができませんでした。その反省をふまえ、今回は「何に使っているか」というのを挙手で聞いてみました。すると、参加者の方々が挙手をしてくれました。Web、バッチ処理、ツール、などさまざまな用途で利用されていることがわかりました（ちなみにTrioのユーザーは確認できませんでした。）

[^euro]: Euro Python 2023参加の記事を書かせていただきました。 [日本からひとりで参加した「EuroPython 2023」スピーカー体験レポート | gihyo.jp](https://gihyo.jp/article/2023/12/road2euro-python)

```{figure} images/fukuda_talk.png
:width: 200
:alt: トーク中の様子

トーク中の様子
```

今回のトークはわたしの中でとても挑戦的な内容でした。 `AsyncValue` の紹介や、asyncio版であるライブラリ `asyncio-util` の公開、そしてそのトークをPyConの本場とも言えるUSで行うという点です。また、反省ももっとも多く得られたトークでもありました。いつも長くなってしまうトークの時間が極端に短く、準備不足が非常に目立ってしまいました。なによりききに来てくださった方に伝えたいことをすべて伝えることができなかったことがとても悔しいです。

はじめてのアメリカ、はじめてのPyCon USでの学びをたくさん持ち帰ることができ、多くの出会いがありました。また、機会を作ってカンファレンスに参加したいと思います。ありがとうございました。

```{figure} images/fukuda_after_the_talk.png
:width: 400
:alt: トーク終了後の様子

トーク終了後の様子
```

````

## CPython's Compilation Pipeline

* <https://us.pycon.org/2024/schedule/presentation/3/>
* Python 3.11から3.13でCPythonのパイプラインが変わった
* ユニットテスト、メンテナンスしやすくする
* 1: トーカナイザーでトークンに分割
* 2: トークンからASTを作る
* 3: optimizer。byte codeを最適化する
* 新しいPython API

````{admonition} PyCon での PSFメンバーランチについて

一般社団法人PyCon JP Association理事の吉田（[@koedoyoshida](https://twitter.com/koedoyoshida/)）です。
このコラムではPSFメンバーランチについて紹介します。

PSFメンバーランチとは、PyCon US中のどこか一日カンファレンスランチの時間帯で、PyCon USを主催するPython Software Foundation（PSF）メンバーが集まってランチするサブイベントです。

例年ここではランチを取りながら、PSFのスタッフとボードメンバーから昨年の活動や会計に関する報告され、他のPSFメンバーと交流します。今年はPythonの生みの親のGuido van Rossum氏も参加していました。
今年は主にPSFのExecutive DirectorであるDeb Nicholson氏から説明がありました。

活動や会計報告と言うだけでは無味乾燥に思われるかも知れませんが、今年はプレゼンテーションの他、フルカラーの20ページほどの報告資料の冊子が準備され、大変分かりやすくなっていました。
特に配布物については昨年まではモノクロコピー数枚組の配布で読み解くのに少し苦労する部分はあったのですが、写真付きのカラー資料でとても分かりやすくなっていました。

```{figure} images/psfbooklet1.jpg
:width: 400

PSFの活動報告の冊子
```

PSFの収入の主要な物としては、年間スポンサーおよびPyCon USなどのイベントの参加者収入となります。また、主な支出としてはPyCon USの開催費用や遠方などからの参加者に対する費用の援助であるTravel Grant、スタッフ人件費、またPython開発者の保険料の支払いなどがあります。今年の報告を聞いて、読んで興味深かった点は、Travel Grantが世界、特にアジアなどの地域にもより公平に分配される傾向になってきたことや、アメリカでのインフレの進行によりスタッフ系のコストが増大していることです
（なお、PyCon JPでは一般社団法人PyCon JP Associationの理事を含め、有給でのスタッフはおらず、無償のボランティアにより運営されています)。

Travel Grantについては前年などにアジア地域を対象とした支出が少ないように思われる点を、以前のこの会議などで日本含めアジアのメンバーから主張してきたことが、反映されたのでは無いかと思います。

PSFメンバーランチはPSFのメンバーであれば、PyCon USの開催の少し前に登録案内が来て、それに登録すれば、無料で参加することができます。

PSFメンバーランチはその場で質問なども出来る貴重な機会です。
PyCon JPと関わりの深いイクバルさんなど多くの方が意見や質問を出していました。

```{figure} images/psflunchqa.jpg
:width: 400

メンバーランチでの質疑応答
```

PSFメンバーになる方法はいくつかありますが、例えば、月に5時間程度PythonやPyConについて継続して活動していることを認められれば、メンバーになることができます。
PSFメンバーを通じて、ボードメンバーの投票などPSFの活動に関わることが出来ます。
興味のある方は下記のページから詳細を確認してみてはいかがでしょうか？

* [Become a Member of the PSF](https://www.python.org/psf/membership/)

````


## Lightning Talks

* CheukさんとAbigailさんがMC
* Pure Pythonをクラッシュさせる方法
* SoftSkill: レビューのコメントをChatGTPで優しくする
* NumPy 2.0.0の固定長文字列の話し

## PyLadies Auction

2日目の夜はPyLadies Auctionです。
このイベントはコミュニティメンバーやスポンサーから提供された物品を、参加者がオークション形式で競り落とすというイベントです。
あつまったお金はすべて寄付金となり、PyLadiesの運営資金となります。
おいしい食事を食べながら、面白おかしく展開するオークションを見られるため、とても楽しいイベントです。

* 品数多過ぎ
* 金額はすごいことになってた



