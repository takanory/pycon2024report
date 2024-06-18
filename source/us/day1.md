# Day 1

## Welcome

* video: <https://events.hubilo.com/pycon-us-2024/session/234271>
* https://stream.mux.com/InaO95Gqswk52RKZOd53BcXpla9cq5XQNuV006teK9Tk/high.mp4
* PSF Welcome video: <https://events.hubilo.com/pycon-us-2024/session/234272>
* https://stream.mux.com/9a0101sF8HlsCYHLvIbAGnQb024TvXxU5DQ26no007vT4jw/high.mp4

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

* video: <https://events.hubilo.com/pycon-us-2024/session/234273>
* https://stream.mux.com/SyApTSMqX00ldiXsAhrzWZgriwSQlQbArwm015pmeH5dE/high.mp4

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
(terada担当)

APAC Boothのはなし
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
