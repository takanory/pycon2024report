# スプリント

カンファレンスのあとは開発スプリントです。
これはCPythonを含むPython関連のオープンソースのプロジェクトに参加し、一緒に開発をするというイベントです。
PyCon US 2024のスプリントは5月20日（月）から23日（木）の4日間開催されます。
筆者は1日目のみフルで参加しました。

プロジェクトの一覧はこれが全てではないですが、以下のページで確認できます。

[Development Sprints - PyCon US 2024](https://us.pycon.org/2024/events/dev-sprints/)

会場に行くとどの部屋にどのプロジェクトがあるかを書いてあるので、これを見て参加したいプロジェクトの部屋に行きます。
たとえばPython CoreはRoom 320であることがわかります。

```{figure} images/sprints-board.jpg
:width: 200

スプリントの部屋割りボード
```

## PyScriptスプリント

筆者は昨年に引きつづきPyScriptスプリントに参加しました。
リーダーも昨年と同じFabio Pliger氏でした。
あいさつをして、[GitHub Issues](https://github.com/pyscript/pyscript/issues)の中から「good first issue」が付いている中で、でできそうなものを探します。

```{figure} images/pyscript.jpg
:width: 400

PyScriptスプリントのテーブル（筆者の左隣がFabio氏）
```

そして簡単なドキュメントのリンク切れを修正するPull Requestを作成し、無事にMergeされました。
ちょっとでも貢献できてよかった。

* [refs #2068 fix links on CONTRIBUTING.md by takanory · Pull Request #2072 · pyscript/pyscript](https://github.com/pyscript/pyscript/pull/2072#pullrequestreview-2068088733)

## スプリントの様子

会場を歩いていると、廊下にあるテーブルにみんながステッカーを広げていました。
さながらステッカー交換所のようです。
参加者が津照れている小さいお子さんが喜んでステッカーを集めていました。
こういうのは万国共通なんですね。

```{figure} images/stickers.jpg
:width: 400

たくさんのステッカー
```

また横を見ると日本から参加した青野さん（1日目に登壇）が、Gudio氏とPaul Everitt氏と立ち話をしていました。
「Python会の重鎮と立ち話してる！！」と思って盗撮しておきました。
こういうシーンが普通にあるのもPyCon USのすごい所だなと思いました。

```{figure} images/koudai-with-guido.jpg
:width: 200

Guido氏、Paul Everrit氏と会話している青野さん
```

[Memray](https://github.com/bloomberg/memray)の部屋をのぞいてみると、寺田さんがIssueと格闘していました。
あとで話を聞いてみると、時間切れで途中までしかできなかったが、他の人が引き継いでくれて解決したそうです。

```{figure} images/memray-sprints.jpg
:width: 400

Memberと格闘する寺田さん
```

* [Prevent the test suite from rendering Textual apps to the screen while running · Issue #600 · bloomberg/memray](https://github.com/bloomberg/memray/issues/600)

## さまざまな人との出会い、再会

ランチはランチボックスが提供されました。
ランチが提供されるだけありがたいです。
メインはチキンサラダでポテチとリンゴがまるごと1つ付いてくるのがアメリカっぽいなと思います。
ランチを食べていると隣の人から「LTで日本語の話をしてたよね？面白かったよ」といった声をかけてもらいました。
「ありがとうございますー」とあいさつを交わして名前を確認してみると、なんとPyCon US 2023のキーノートスピーカーだったNed Batchelder氏でした。
そこかしこに大物がいて、PyCon USやべーなと思いました。

```{figure} images/sprint-lunch.jpg
:width: 200

ランチボックスの中身
```

* 参考：[#01 PyCon US 2023への道、カンファレンス前夜祭から1日目セッションへ | gihyo.jp](https://gihyo.jp/article/2023/05/pycon-us2023-001)

スプリントでは久しぶりの人との再会もできました。
Eric Matthes氏は筆者が翻訳をした[書籍](https://gihyo.jp/book/2020/978-4-297-11570-8)の原著者です。
「[第3版](https://ehmatthes.github.io/pcc_3e/)出てますねー。」みたいな話をしました。
Hynek Schlawack氏は向こうから「覚えてる？」と声をかけてくれました。
Hynek氏は[PyCon JP 2015](https://pycon.jp/2015/ja/talks/keynote/)のキーノートスピーカーとして日本に来てくれました。
「日本楽しかったよー」ととても日本に対していい思い出があるようで「また来てくださいねー」という話をしました。
こんな感じで、繰り返しPyCon USに参加していると、少しずつ知り合いの和が拡がっていっていることを感じ、それもうれしいなと思いました。

```{figure} images/eric.jpg
:width: 200

Eric Matthes氏
```

```{figure} images/hynek.jpg
:width: 200

Hynek Schlawack氏
```

## 最後のパーティー

今日のスプリントで最後までいるアジアメンバーで飲みに行こう！ということで、検索してよさそうだなと思った[Church Brew Works](https://churchbrew.com/)に行くことにしました。
このビール醸造所兼レストランは本物の教会だった建物を再利用しています。
ステンドグラスやパイプオルガンがそのまま残っており、とても素敵な建物でした。
ステンドグラスと同じマークのビールグラスがかっこいいです（このグラスは自分へのお土産としても飼いました）。

```{figure} images/glass.jpg
:width: 200

ステンドグラスと同じ柄のビールグラス
```

日本、韓国、台湾、インドのコミュニティメンバーと楽しい会話をしながら、筆者の充実したPyCon US 2024が終了しました。
このお店は気に入ったので、また来年も来よう！と強く思いました。

```{figure} images/cheers.jpg
:width: 200

乾杯！！
```

## おわりに

PyCon US 2024のレポートは以上です。
今年もまた非常に充実したイベントでした。アジアからの参加者も増えて、来年はもっと増えるといいなと思っています。
個人的にはPyCon USで初めてのライトニングトークをできたことが印象深いです。
フルのトークは過去に採択されたことはあるんですが、コロナでオンライン化、自身がコロナで不参加と、リアル登壇をいつか...と思っています。

筆者が行っているYouTubeライブ、PyCon JP TVでもPyCon US 2024について紹介しています。
寺田さんの写真を中心としたレポートなので、異なった目線からの感想もあるので、ぜひご覧になってください。

<iframe width="560" height="315" src="https://www.youtube.com/embed/2wNirevfyuE?si=WOcFOwv_qR4tGxFX" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

オフィシャルの発表動画は、PyCon USのYouTubeチャンネルで公開予定です。
以下のページで確認してください。

* [PyCon US - YouTube](https://www.youtube.com/@PyConUS/featured)

筆者のPyCon US 2024中のツイート（ポスト）をTogetterにまとめました。
こちらももしよかったら見てください（飲んでいるところが多いですが）。

* [PyCon US 2024 - Togetter](https://togetter.com/li/2398268)

-----

帰りはシカゴ乗り換えですが、飛行機の都合でシカゴに2泊しました。
シカゴの[IT'SUGAR](https://itsugar.com/)というお菓子屋さんには、日本から輸入した抹茶キットカットが12.99ドル（約2,100円）で売っていました（日本だと380円くらい）。
抹茶キットカットの運び屋として、一財産が築けるかもしれません。

```{figure} images/kitkat.jpg
:width: 200

12.99ドルの抹茶キットカット
```

また、本場のシカゴピザ（Deep Dish Pizzaと言うらしい）を初めて食べました。
友だちのJasonさんおすすめの[Pequod's Pizza](https://pequodspizza.com/chicago/)に行きましたが、おいしいけど、サイズがヤバかったです。
写真だとわかりにくいですが、日本で食べたことのあるシカゴピザの2倍くらいのサイズ感でした。
大人3人ではまったく食べきることができず、半分以上を持ち帰りました（次の日の朝も食べました）。

```{figure} images/chicago-pizza.jpg
:width: 400

本場のシカゴピザ
```

