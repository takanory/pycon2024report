# Day 2

## D&I Panel

* <https://us.pycon.org/2024/about/keynote-speakers/#dei-panel>
* Dima:2019にはじめてインドネシアでボランティア
* アビゲイルにはじめてDjango Girlsをガーナで開催。PyLadiesガーナを立ち上げ
* PyTxasは2007から開始。

* チャレンジは?
* アビゲイル: コミュニティをはじめるのは大変。メンバーに価値があるか耳を傾ける。リソースが問題。
* Dima: 最初は一人だった。人、スポンサー、お金を探した。PSFのGrantでお金を送ってくれた。Pythonコミュニティでのサポートがあった
* ブラジル: COVID-19でいくつかのグループが分かれた。安全な場所を作った

## Keynote: Simon Willison

* <https://us.pycon.org/2024/about/keynote-speakers/#simon-willison>
* LLMについて話したい
* AIじゃなくてImitation intelligence
* どのモデルを使うのがいい?→ふんいき
* MLCChatがおすすめ
* llm.datasette.io
* <https://pypi.org/project/vosk/>
* 以前は考えられないようにプロジェクトを素早く作成できるのを助けてくれる
* PSFの投票ページをDatasetteのプロジェクトでデータセットにする?

```{admonition} 挑戦と反省：PyCon US 2024登壇で得たもの

こんにちは、福田 隼也（@JunyaFff）です。ここでは、初めて参加の「PyCon US」で登壇してきた話をコラムで紹介します。
わたしカンファレンス2日目、朝10:30からRoom 301-305という部屋で「Event-Driven asyncio: A Case Study of Trio's API」というタイトルのトークをしました。

* [トーク概要 - PyCon US 2024](https://us.pycon.org/2024/schedule/presentation/142/)

```{figure} source/us/images/fukuda_talk_list.png
:width: 600
:alt: Room 301-305でのトーク一覧

Room 301-305でのトーク一覧。中段に「Event-Driven asyncio: A Case Study of Trio's API」というタイトルがあります。
```

事前にスタッフの方より控室には20分前に、トークする部屋には10分前に入るように言われており、時間通りに会場に入りました。司会の方に挨拶をした後に、パソコンやマイクの設定を行い、いざ会場を見渡すと、広い部屋に見慣れた日本からの参加者数名の方しかいない状況でした。おそろしい。

わたしのトークはカンファレンス2日目の午前中の1本目です。2日目の午前中は前日の夜遅くまで参加者の方々が交流していたりするため、トークの参加者が少ないことが多いのかもしれないと想像されるかもしれませんが、控室に入る前に少しのぞいたキーノートの会場は盛況な様子でした。

司会の方と「人が少ないね」と話をしていると時間になり、司会の方が壇上でトークの紹介をしてくれました。すると途中から会場に参加者が増えてきました。あとから聞いた話では、キーノートが予定の時間よりも終わる時間が少し遅かったようで、そこからの移動だったようです。一安心してトークを進めることができました。

```{figure} source/us/images/fukuda_started_talk.png
:width: 600
:alt: 開始直後の様子

開始直後の様子
```

わたしのトークは、Pythonの非同期プログラミングライブラリ「[Trio](https://github.com/python-trio/trio)」のAPIを使ったプロダクションでの事例とコードの紹介です。

Pythonの非同期といえば標準ライブラリである `asyncio` が有名ですが、 今回のトークではよりシンプルで使いやすい `Trio` にフォーカスしました。なぜ `Trio` が使いやすいのか、なぜプロダクションでの採用したのか、また `Trio` を拡張した `trio-util` の `AsyncValue` というAPIにフォーカスを当てて紹介しました。
今回のトークに合わせ公開した、 `AsyncValue` のasyncio版であるライブラリ `asyncio-util` についても触れました。

ご興味がある方は以下のリンクをみてみてください。

* [登壇資料 - Speaker Deck](https://speakerdeck.com/jrfk/event-driven-asyncio-a-case-study-of-trios-api-pycon-us-2024)
* [trio_util.AsyncValue - Document](https://trio-util.readthedocs.io/en/latest/)
* [asyncio-util - GitHub](https://github.com/jrfk/asyncio-util)

実は去年Euro Python 2023でトークをした時に、Pythonで非同期を利用されている方が多く驚いたのですが、「何に利用しているか」というのを聞くことができませんでした。その反省をふまえ、今回は「何に使っているか」というのを挙手で聞いてみました。すると、参加者の方々が挙手をしてくれました。Web、バッチ処理、ツール、などさまざまな用途で利用されていることがわかりました（ちなみにTrioのユーザーは確認できませんでした。）

```{figure} source/us/images/fukuda_talk.png
:width: 600
:alt: トーク中の様子

トーク中の様子
```

今回のトークはわたしの中でとても挑戦的な内容でした。 `AsyncValue` の紹介や、asyncio版であるライブラリ `asyncio-util` の公開、そしてそのトークをPyConの本場とも言えるUSで行うという点です。また、反省ももっとも多く得られたトークでもありました。いつも長くなってしまうトークの時間が極端に短く、準備不足が非常に目立ってしまいました。なによりききに来てくださった方に伝えたいことをすべて伝えることができなかったことがとても悔しいです。

はじめてのアメリカ、はじめてのPyCon USでの学びをたくさん持ち帰ることができ、多くの出会いがありました。また、機会を作ってカンファレンスに参加したいと思います。ありがとうございました。

```{figure} source/us/images/fukuda_after_the_talk.png
:width: 600
:alt: トーク終了後の様子

トーク終了後の様子
```









```

## CPython's Compilation Pipeline

* <https://us.pycon.org/2024/schedule/presentation/3/>
* Python 3.11から3.13でCPythonのパイプラインが変わった
* ユニットテスト、メンテナンスしやすくする
* 1: トーカナイザーでトークンに分割
* 2: トークンからASTを作る
* 3: optimizer。byte codeを最適化する
* 新しいPython API

```{admonition} (いい感じのコラムタイトルにしてね)
(yoshida担当)
PSF Memerb Lunchのはなしとか
```


## Lightning Talks

* CheukさんとAbigailさんがMC
* Pure Pythonをクラッシュさせる方法
* SoftSkill: レビューのコメントをChatGTPで優しくする
* NumPy 2.0.0の固定長文字列の話し

## PyLadies Auction

* 品数多過ぎ
* 金額はすごいことになってた



