# Day 1

## Welcome

* ChairのMariattaさんのオープニング
* 100+ボランティアのオーガナイザー
* Celebration
  * 973 Proposals
  * 登録 2738 + 395 online

* NVidia: 3年間のVisionalyスポンサー
* AWS: 2023にPyPIセキュリティのスポンサーの話しをした。Mikeさんが雇われていろいろ対応した
* Deb Nicholson
  * Python 300 milion / day, PyPI 384 bilion / year
  * 697,000 USD Grants
    * discordでGrants ProgramのOffice hour
* Fastly: 4.3EBを配信

## Keynote: Jay Miller

* PyCon USだと何人かの黒人しかステージで見たことがない
* どこかで発表した?→仕事を探している(そうかー
* WAKANDAになりたい?
  * <https://ja.wikipedia.org/wiki/%E3%83%AF%E3%82%AB%E3%83%B3%E3%83%80>
* コミュニティヒーローになりたい
  * 胸の前で腕を交差するポーズはどういう意味なんだろう
* women who codeはwhite women who code
* 2023では31人見つけられた
* Black Python Devs: 425 members
  * Gnome Foundationがサポート
  * North, South America, Africa, Europe
  * 世界中からのリダーグループ
* 4人のリーダーがはじめてPyCon USに参加。15,000 USD
* サポートするためにdonate、document、本を寄付、Black Python Devs
* 5,000 USDを目標
  * http://blackpythondevs.com/
* JetBrasinがインフラスポンサー

## Making Your Documentation Interactive with PyScript

* <https://us.pycon.org/2024/schedule/presentation/92/>
* py-editorはそれぞれ別のインタプリター
* environmentで共有できる
* URLをvirtual filesystemとして使える
* sphinx-pyscript のdirectiveで動かせる
  * +richでリッチになる
  * mkdocs-pyscript も同じ感じ
  
```{admonition} (いい感じのコラムタイトルにしてね)
このコラムは一般社団法人PyCon JP Association理事の寺田(@terapyon)がお届けします。

PyCon JP Associationは、PyCon APAC（アジア太平洋地域）のコミュニティの一員として活動をしています。
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
