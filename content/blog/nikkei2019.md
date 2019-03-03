---
title: "全国統一プログラミング王決定戦2019 本戦参加記"
date: 2019-03-03T13:05:13+09:00
draft: false
tags: ["AtCoder"]
categories: ["コンテスト参加記"]
---

Writer: NOSS

全国統一プログラミング王決定戦本戦(2019/2/17)に参加してきました。

## 会場

会場は[東京ドームホテル](https://www.tokyodome-hotels.co.jp/)の地下1F「天空」でした。

<img src = "https://user-images.githubusercontent.com/28915482/53691170-6d185280-3dbb-11e9-9ab7-a5ce22c6dffa.JPG" width="300">

<blockquote class="twitter-tweet" data-lang="ja"><p lang="ja" dir="ltr">会場はこんな感じ！電源も1人につき1つあるよ！ <a href="https://t.co/3RJqpxwDB8">pic.twitter.com/3RJqpxwDB8</a></p>&mdash; chokudai(高橋 直大)🍆🍡 (@chokudai) <a href="https://twitter.com/chokudai/status/1096941216652873728?ref_src=twsrc%5Etfw">2019年2月17日</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>


受付を済ませて談笑をしているとコンテストの時間になったので急いでPCの準備を整えてコンテストに臨みました。

## コンテスト

[コンテスト](https://atcoder.jp/contests/nikkei2019-final)

### A - Abundant Resources (200)

[A問題](https://atcoder.jp/contests/nikkei2019-final/tasks/nikkei2019_final_a)

長さNの数列Aがあります。1以上N以下のkについて長さkの区間和の最大値を求めてください。

- 1 ≦ N ≦ 3000
- 1 ≦ A<sub>i</sub> ≦ 10<sup>9</sup>

累積和の前処理をO(N)で行うことで区間和をO(1)で求められます。あとは各kについてN-k+1回ループを回して全探索すればよいので全体計算量はO(N<sup>2</sup>)です。

[提出結果](https://atcoder.jp/contests/nikkei2019-final/submissions/4297753)

### B - Big Integers (200)

[B問題](https://atcoder.jp/contests/nikkei2019-final/tasks/nikkei2019_final_b)

制約をよく見ると、A,B<K なのでA,BはK進数の各桁の値を表していることがわかります。つまりK進数の大小比較をすることになるのでN,Mが異なるならその大小、同じなら上位桁から見ていくようにします。

[提出結果](https://atcoder.jp/contests/nikkei2019-final/submissions/4298116)

### C - Come Together (300)

[C問題](https://atcoder.jp/contests/nikkei2019-final/tasks/nikkei2019_final_c)

H行W列の各マスに駒が置いてあります。このうち(R<sub>i</sub>,C<sub>i</sub>)にあるK個の駒を取り除きます。1回の操作で1つの駒を上下左右の1マス隣に移動できるとき、すべての駒を1つのマスに集めるのに必要な最小操作回数を求めよ。

- 1 ≦ H,W ≦ 10<sup>5</sup>

まず、マンハッタン距離の定義から移動をx方向とy方向に分離できます。x方向のみを一致させることを考えるとi列目にある駒の個数をA<sub>i</sub>としてすべてをj列目に集めるためには

A<sub>0</sub> * j + A<sub>1</sub> * (j-1) + ... + A<sub>j-1</sub> * 1 + 0 + A<sub>j+1</sub> * 1 + ... + A<sub>W-2</sub> * (W-2-j) + A<sub>W-1</sub> * (W-1-j)

の操作が必要になります。ここでよく見ると一次関数を2つ合わせたの形をしていることに気づきました。累積和を2回とると一次関数になるのでこれを順方向と逆方向の2つ作っておくとj列目を境に左右をそれぞれO(1)で求められるようになります。よってjをN回ループしてその最小値を求められます。y方向についても同様に求められるのでx方向とy方向の最小値の和が答えになります。

[提出結果](https://atcoder.jp/contests/nikkei2019-final/submissions/4298534)

### D - Deforestation (500)

[D問題](https://atcoder.jp/contests/nikkei2019-final/tasks/nikkei2019_final_d)

N本の竹があります。時刻0ですべての竹の長さは0です。時刻が１経過するごとに長さは1増えます。M回の操作を行います。i番目の操作は時刻 T<sub>i</sub>に行われ、この操作では番号がL<sub>i</sub>以上R<sub>i</sub>以下の竹をすべて伐採します。 高さxの竹を伐採するとき、x点を得ます。 また、伐採された竹は高さが0になりますが、その竹はこれ以降も伸び続けます。

M回の操作で得る得点の総和を求めてください。

- 1 ≦ N,M ≦ 2*10<sup>5</sup>
- 1 ≦ T<sub>i</sub> ≦ 10<sup>9</sup>
- 1 ≦ L<sub>i</sub> ≦ R<sub>i</sub> ≦ N

操作の内容はRAQとRUQだとわかったものの遅延評価セグ木をライブラリにもっていないのでネットから探すことになりました。ちょうどRAQとRUQを両方実装されているものが見つからなかったので自分でこの2つを融合させることになりました... さすがにセグ木に追加機能を書けるほどデータ構造の素養も無いので比較的デバッグしやすい平方分割で実装しました。しかし実装ミスも多く4WAと100分間をかけてなんとかACしました。

[提出結果](https://atcoder.jp/contests/nikkei2019-final/submissions/4299647)

### E -Erasure (700)

[E問題](https://atcoder.jp/contests/nikkei2019-final/tasks/nikkei2019_final_e)

制約からみてDPが使えそうだなと思い、dp[i] = iまでをすべて消す通り のように置いて考えていました。ただ遷移がうまくいかなくて結局サンプル1しか通らず椅子を温めました。

#### 結果とコメント

結果はABCDの4完で173位でした。

Cは駒の位置の中央値が最小値になるのでそっちの考察が生えていればもう少し楽だったかなと思います。Dはライブラリの整備をしておくべきでした。それからもう少しEに時間をかけたかったという気持ちです。実力と言えば実力という結果だったと思います。

## トークショー & エキシビジョンマッチ

競技プログラミングをするとどんな能力を養えるのかの話やこれからどうすればいいのかという話まで聞けてとても楽しく参考なりました。PFNすごいなあ…

決勝上位3名によるエキシビジョンマッチがそれぞれのコーディング状況がモニターにライブされるというすごい新鮮な企画でした。超爆速でコードが生やされているのをみてこれが日本最速コーダーか...と驚きをこえて笑いしか出ませんでした。見ている僕の時間感覚のほうが壊れました。とても面白かったのでまた企画してほしいなと思います。

## 懇親会

会場に500人もいるとなるとひとを探すのも一苦労ですね。幸運にも知り合いの方やお話したかった人と会うことができたので良かったです。曰く料理のクオリティーはオンサイトでもトップクラスだそうです。(さすが日経コンテスト…) とてもおいしくいただきました。あともっと知り合い増やしたいという気持ちになりました。(皆さんよろしくおねがいします)

## 感想

お話をしていると色んな大学で最近競プロサークルができたり、あるいは今作ろうと頑張っているという話を度々聞いて競プロ盛り上がってるなあと感じました。だからこそここまで盛大なコンテストを開催することができたんだなと思います。ちょくだいさんが「今日がターニングポイントになる」とおっしゃっていましたがそういう場に本戦参加者として立ち会えたことを嬉しく思います。来年も開催されるならまた勝ち抜けるようにこれから一層精進をがんばります。

日本経済新聞社、AtCoder、協賛の皆様。このようなコンテストを開催してくださりありがとうございました。

<img src = "https://user-images.githubusercontent.com/28915482/53691236-ce8cf100-3dbc-11e9-85c8-6894ca221851.jpg" width="300">