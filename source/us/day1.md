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
(terada担当)

APAC Boothのはなし
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

````{admonition} 初めて登壇の体験
このコラムは青野 高大([@koxudaxi](https://github.com/koxudaxi))がお届けします。

私は人生初のイベント登壇を経験しました。

トークの内容はデコレータと型アノテーションのベストプラクティスについてで、タイトルは「Enhancing Decorators with Type Annotations: Techniques and Best Practices」でした。

PyConUSには毎年多くのトークプロポーザルが提出されるため、トークが採用されるにはトークテーマをよく考える必要があります。
私は前回もプロポーザルを提出しましたが残念ながら落選してしまいました。そのため、今回は二ヶ月ほどかけてトークのテーマについて毎日のように考えました。
個人的には、PyConUS登壇の一番の難所はトークプロポーザルの作成だと思います。

これまで社内のオンライン会議での発表は経験がありましたが、リアルイベントでのプレゼンテーションの経験はありませんでした。
スライドについてもオンラインとは勝手が違い、プロジェクタに映すためにフォントサイズを大きくしなければならず、サンプルコードをわかりやすく掲載するのに苦労しました。
また、私は人前で話すことが苦手ということもあり、トークが始まるまでは緊張と不安でいっぱいでした。
ただ、できるかぎりのことをやろうと思い発表直前まで練習を繰り返しました。おそらく3〜5回は予行練習をしたと思います。

実際に話し始めると会場の皆さんが熱心に私の話に耳を傾けてくれたおかげで、自信を持って最後までトークをやりきることができました。
登壇後もトークの話題をきっかけに、たくさんの人と交流を広げることができ、イベント中はとても楽しい時間を過ごせました。
今まではOSSのコントリビューターとして活動していましたが、イベント登壇を通じて開発者が実際に現場で使えるノウハウを共有することの重要性を再認識しました。
GitHubのスターをもらうのも嬉しいですが、直接トークのお礼や感想を言われる方がもっと嬉しかったです。

私のトークを支えてくれた運営メンバーや友人、そして多くの来場者の方々に心から感謝いたします。

```{figure} images/koudai_aono_talk.jpg
:width: 600

登壇中の様子
```

````

## Lightning Talks

* 自分がLT発表したはなし
* 他の人のLTにも少し触れる
