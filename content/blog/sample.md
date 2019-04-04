---
title: "Sample"
date: 1024-02-16
draft: true
tags: ["sample tag1", "sample tag2"]
categories: ["sample category"]
author: sample author
images: ["img/banners/logo.png"]
---

サンプル記事
サンプル記事だよ
サンプル記事

<!--more-->

↑moreより下は一覧ページからは見えない  
`<!--more-->`より上が「要約」部分になり、一覧ページに表示されます  
要約は`<!--more-->`が無くてもHugoが自動で作ってくれますが、  
中途半端な所で切れたりします。
<!--
改行は行末に半角スペースを2つ入れるとできます
ちなみにこれはコメントで、記事には表示されません
-->

* * *

# 目次
- [記事のファイル最上部について](#記事のファイル最上部について)
- [Markdown記法のサンプル](#Markdown記法のサンプル)
- [Shortcodesのサンプル](#Shortcodesのサンプル)
- [数式のサンプル](#数式のサンプル)

* * *

# 記事のファイル最上部について
```
title: ←記事のタイトルです
date: ←記事を書いた日付です
draft: ←下書きか否か。trueの場合下書きになり、表示されなくなります。
tags: ←記事のタグです。何個でも指定できます
categories: ←記事のカテゴリです。こちらも何個でも指定できます
author: ←記事の著者です。一人だけ指定できます。
images: ←記事のサムネイルです。/staticディレクトリ以下にある画像ファイルを指定するとサムネイルが設定され、記事一覧ページに表示されます。また、twitter cardにも使用されます。一応複数指定でき、1枚目がサムネイルとして使用されます。2枚目以降はtwitter cardなどで使用されます。
```

* * *

# Markdown記法のサンプル

記事にはMarkdown記法（及びHTMLタグ）が使用できます  
Markdown記法については[こちら](https://qiita.com/Qiita/items/c686397e4a0f4f11683d)（QiitaにおけるMarkdownの話なので、一部異なります）

Markdown記法のうち使いそうなものを以下にピックアップしておきます

# サンプル見出し
## サンプル見出し2

- サンプル箇条書き
    - サンプルネスト箇条書き
        - もっとネスト
        - もっとネスト2
    - サンプルネスト箇条書き
- サンプル箇条書き

1. サンプル番号付きリスト
1. サンプル番号付きリスト2番目
    1. サンプル番号付きネストリスト

> サンプル引用
>
> 引用サンプル
>
>> 引用の引用

```C++
#include<bits/stdc++.h>
using namespace std;

int main(){
    cout << "C++ Sample" << endl;

    return 0;
}
```

```Python
import matplotlib.pyplot as plt

def main():
    print("Python Sample")
    return

if __name__ == "__main__":
    main()
```

```
普通のテキスト
```

    普通のテキスト（タブ）

行中に入れる場合は`printf("sample\n");`こんな感じ

![画像サンプル](/img/blog/sample/logo2.png)  
`/static/img/blog/sample/logo2.png`を読み込んでいます  
画像ファイルを`/static`以下に置くとこのように読み込むことができます

*サンプル斜体* _italic sample_  
**太字サンプル** __bold sample__  
***太字斜体サンプル*** ___italic bold sample___

* * *

- - -

_ _ _

[サンプルリンク](https://ynucpc.github.io/)
[見出しにリンク](#サンプル見出し2)

|列１|列2|列3|
|:--|--:|:--:|
|left|right|center|
|サ|ン|プル|

---

Markdownなので、HTMLタグも使用できます  
<ruby>
HTML<rt>えいちてぃーえむえる</rt>
</ruby>
のサンプル

* * *

# Shortcodesのサンプル

Hugo Shortcodesという機能を用いてHTMLを生成することができます。  
Hugo Shortcodesについては[こちら](https://gohugo.io/content-management/shortcodes/)（あまり使わないので読まなくても大丈夫です）

画像はMarkdown記法の他、Shortcodesを用いて↓のようにも書けます（幅を指定するときなど）

{{< figure src="/img/blog/sample/logo.png" width="130" >}}

ツイートの引用は、URLの末尾にあるツイートのIDを使用します。  
`https://twitter.com/ynu_cpc/status/742345216347099136`を引用する場合

{{< tweet 742345216347099136 >}}

別のページへのリンクを張るとき、リンク先のページのファイル名を使って以下のように書けます

[別のページへのリンク（絶対パス）]({{< ref "/about.md" >}})  
[別の記事へのリンク（相対パス）]({{< relref "first-post.md" >}})

* * *

# 数式のサンプル

$\KaTeX$を用いて数式を書くことが出来ます。KaTeXについては[こちら](https://katex.org/)  
おおよそLaTeXと同じ感覚で書けるはずですが、
未対応の機能があったり若干コマンドが違ったりしてクセがあります  
一方で、MathJaxと比べ高速に数式を描画することができます

$$
    e^{i \pi} + 1 = 0
$$

文章中に$10^{10^{10^{10}}}$とか\\( a_{b_i} \\)

\\[
    \frac{d}{dx} F(x) = \frac{d}{dx} \int_{a}^{x} f(t)dt
\\]

複数行の数式はaligned環境が使用できます（改行の仕方がトリッキーなので注意）
$$
\begin{aligned}
a_1 + a_2 + \cdots + a_N & = M \\\ ~
\sum _{i=1} ^{N} a_i & = M
\end{aligned}
$$
<!--
本来はバックスラッシュ2つで改行になるはずですが、
なぜか"\\\ "としないと改行になりません。
テキストエディタの設定によっては末尾の空白が消えてしまうため、チルダを入れています
-->

数式にエラーが合った場合、赤文字でエラーを指摘してくれる場合があります
$$
x_{n+1} = x_n - \fraq{f(x_n)}{f'(x_n) - \frac{f(x_n)f''(x_n)}{2f'(x_n)}}
$$

正しくは↓（ベイリー法の漸化式です）

$$
x_{n+1} = x_n - \frac{f(x_n)}{f'(x_n) - \frac{f(x_n)f''(x_n)}{2f'(x_n)}}
$$
