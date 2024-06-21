# カンファレンス1日目

カンファレンス1日目です。
ホテルからカンファレンス会場への道は、過去に参加したクリーブランド、ソルトレイクシティよりちょっとだけ怖いなって感じがありました（特になにも事件はありませんでしたが）。
とはいえ、夜でも複数人なら全然問題なく歩ける感じです。

## Welcome と PSF Welcome

```{admonition} 削除予定
* video: <https://events.hubilo.com/pycon-us-2024/session/234271>
* https://stream.mux.com/InaO95Gqswk52RKZOd53BcXpla9cq5XQNuV006teK9Tk/high.mp4
* PSF Welcome video: <https://events.hubilo.com/pycon-us-2024/session/234272>
* https://stream.mux.com/9a0101sF8HlsCYHLvIbAGnQb024TvXxU5DQ26no007vT4jw/high.mp4
```

カンファレンスのオープニングは2023に続いてConference ChairであるMariatta（[@mariatta](https://twitter.com/mariatta)）氏からのあいさつです。
オープニングの最初の方で私もインタビューに参加した「PyCon USコミュニティメンバーからのメッセージ動画」が流れたんですが、ダイジェスト版のようで私は出ませんでした。残念（フルバーションはこちら→[Get ready for PyCon US 2024! Tips and tricks from our community.](https://www.youtube.com/watch?v=RL3HFj5SDqI&t=451s)）。

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

* <https://events.hubilo.com/pycon-us-2024/session/234181>
* https://stream.mux.com/9t6QfvsHKEtCc9vXfUK01gV1p14OEpC02ejLin5008d2Xc/high.mp4
* <https://us.pycon.org/2024/schedule/presentation/92/>
* py-editorはそれぞれ別のインタプリター
* environmentで共有できる
* URLをvirtual filesystemとして使える
* sphinx-pyscript のdirectiveで動かせる
  * +richでリッチになる
  * mkdocs-pyscript も同じ感じ
  
```{admonition} (いい感じのコラムタイトルにしてね)
このコラムは一般社団法人PyCon JP Association理事の寺田(@terapyon)がお届けします。

[PyCon JP Association](https://www.pycon.jp/)は、[PyCon APAC（アジア太平洋地域）](https://pycon.asia/)のコミュニティの一員として活動をしています。
PyCon APACは2010年から毎年、アジア太平洋地域のいずれかの国で開催しているイベントです。[昨年2023年は東京で開催](https://2023-apac.pycon.jp/)しました。[今年はインドネシアのYogyakarta](https://2024-apac.pycon.id/)で開催されます。

PyCon USにはコミュニティーブースがあり、昨年に引き続きPyCon APAC コミュニティーでもブースを設置しました。

私達のブースでは、APAC地域でPyConが多く開催されていることを紹介し、今年のPyCon APAC 2024が10月末にインドネシアで開かれていること、さらに興味を持ってくれた地域があれば、それぞれのPyConの特徴などを紹介しました。

各国でPyConの主催を中心的に行っているメンバーたちが集まり、日本はもちろん、韓国、台湾、インドネシア、インドの方々で時間のある時にはブースに居て説明員をするという形で行いました。
今年は、ブース用にTシャツを作りAPACチームとしての一体感を出すように運営しました。

![PyCon APAC Tシャツで記念撮影](images/booth-t-shirt.jpg)

ブースにはノベルティとして、各国からのお菓子が置かれブースに立ち寄ってくれた方に配布しました。日本からは抹茶のキットカットを持っていたのですが大変好評でした。他にもPyCon APAC 2024のステッカーを配布したり、PyCon APAC地域のイベントスケージュールが書かれた「折り紙」を配布しました。この折り紙を2枚使うと手裏剣ができあがり、PyCon JPとPyCon APACのWebサイトURLのQRコードがでるようにしたものも配布しました。折り紙は情報としてのチラシの役割と共に手裏剣になるというギミックに興味を持ってもらえました。

ブースには多くの方に立ち寄っていただき、APAC地域にこんなにPyConがあるのかという感想を多く聞けて良かったです。

![PyCon APAC ブース](images/booth-1.jpg)
```

## Ruff: An Extremely Fast Python Linter and Code Formatter, Written in Rust

* <https://events.hubilo.com/pycon-us-2024/session/234193>
* https://stream.mux.com/pKn4OXC9KG76tLx7puZCCXSUgdDqpsapE5lXfSPgtA8/high.mp4
* Ruffはlintとformatとcode transformer
* what makes ruff fast?
* tokenに分割、意味的な解釈
* Concurrency and parallelism
  * 全部のファイルを並行で処理できる
* Culture
  * データで判断
* 整数の扱いについて
  * Pythonはデカい整数が扱えるので
* noquaコメントの処理
  * 正規表現からLexarに変えて速くなった
* parser generatorから移行
  * parser用の専用コードからparser generatorでrustのコードを生成する
  * Pythonの変更に対応しやすくなった
  * パフォーマンスも良くなった

```{admonition} (いい感じのコラムタイトルにしてね)
(koxudaxi担当)

自分のトークのはなし
```

## Lightning Talks

* 自分がLT発表したはなし
* 他の人のLTにも少し触れる
