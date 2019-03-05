---
title: "Howtopost"
date: 2019-03-05T13:12:52+09:00
draft: true
tags: []
categories: []
---

記事を投稿するまでの手順を紹介します

<!--more-->

# 目次

- [Hugoのインストール](#Hugoのインストール)
- [Gitのインストール](#Gitのインストール)
- [ローカルにリポジトリをクローンする](#ローカルにリポジトリをクローンする)
- [記事ファイルの作り方](#記事ファイルの作り方)
- [Markdownの書き方](#Markdownの書き方)
- [記事ファイルの投稿](#記事ファイルの投稿)

# Hugoのインストール

**Hugo**はMarkdownで書いた記事ををいい感じの見た目にしてくれるソフトです。  
主に記事ファイルの生成と実際の見た目がどうなるかを確認するのに使用します。

インストール方法は[こちら](https://gohugo.io/getting-started/installing/)の公式HPで紹介されています。  
自分の環境にあったものをインストールしてください。  
英語は難しい！という方はWindowsとmacOSについてはページの下に動画でインストール手順を紹介しているものがあるのでそちらを見るとわかりやすいかと思います。

- [macOSの動画](https://youtu.be/WvhCGlLcrF8)
- [Windowsの動画](https://youtu.be/G7umPCU-8xc)

インストール出来たら以下のコマンドで正しくインストールできたか確認してみてください。

```
hugo version
```

### Ubuntuでの注意

公式HPの紹介ではLinuxのUbuntuでのインストール方法として

```
sudo apt-get install hugo
```

のコマンドが紹介されていますがapt-getのHugoのバージョンが古すぎてここでは**使えない**可能性があります。(少なくともv0.17以上である必要があります) なので手動で最新版を入れる必要があります。

まず、[Hugo Releases](https://github.com/gohugoio/hugo/releases)で最新のdebパッケージをダウンロードします。  
例えば現在の私の状態ならば `hugo_0.54.0_Linux-64bit.deb` をダウンロードして適当な場所に保存します。  
そしたら保存した場所で以下のコマンドを実行します。

```
sudo apt install ./hugo_0.54.0_Linux-64bit.deb
```

debのファイル名は先ほどダウンロードしたものを指定してください。これで最新版のHugoがインストールできました。

参考(http://note.mokuzine.net/hugo-install-ubuntu-1604-lts/)

# Gitのインストール

**Git**はバージョン管理や複数人で作業するためのソフトです。  
インストール方法は[こちら](https://git-scm.com/book/ja/v2/%E4%BD%BF%E3%81%84%E5%A7%8B%E3%82%81%E3%82%8B-Git%E3%81%AE%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB)などで紹介されています。  
Gitの導入方法は様々なサイトで紹介されているので詳しい方法はそちらを参照してください。

Gitをインストール出来たら以下の初期設定をやっておきましょう。

```
git config --global user.name "Bob"
git config --global user.email example@example.com
```

# ローカルにリポジトリをクローンする

(ここから先はGitの知識を使用するのでわからなくなったときは[こちら](https://backlog.com/ja/git-tutorial/)を参考にして下さい。)

これから作業をするためにgithub上にあるソースを手元のPCにクローン(コピー)します。  
適当なディレクトリで以下のコマンドを実行するとそのディレクトリ下に`cpc-hp`というディレクトリがクローンされます。

```
git clone --recursive https://github.com/YNUCPC/cpc-hp.git
```

今後はこの`cpc-hp`ディレクトリ中で作業します。

# 記事ファイルの作り方

不具合を未然に防ぐためブランチというものに分けて更新を行います。  
まず記事更新用のブランチを作成するためのコマンドを実行します。

```
git checkout -b blog
```

これでblogというブランチを作成しそこに移動できました。  
いまどのブランチにいるかはbranchコマンドで確認できます。

```
git branch
```

また、ブランチを切り替える場合はcheckoutコマンドを使用します。例えばblogブランチに切り替えたいときは以下のようにします。

```
git checkout blog
```

blogブランチにいることを確認出来たら次に記事のファイルを作成します。

```
hugo new blog/post_name.md
```

`content/blog/post_name.md`が作成されるので、あとはこのファイルをエディタで編集していきます。

# Markdownの書き方

Markdown記法は[サンプル](./sample.md)を参考にしてください。  
実際にどう表示されるか確認したい場合は以下のコマンドを実行してから  
`http://localhost:1313` にアクセスすると確認できます。

```
hugo server
```

# 記事ファイルの投稿

記事が完成したらコミットしてからリモートにプッシュします。

```
git add content/blog/post_name.md
git commit -m "Add new post"
git push origin blog
```

Pull Requestを立てると誰かがmasterにマージしてくれます。

## お疲れさまでした...

最初の環境構築さえ乗り切ればあとはなんとかなります。  
分からないなーという場合は知っていそうな部員に聞きましょう。

by NOSS