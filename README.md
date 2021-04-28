# cpc-hp [![Build Status](https://travis-ci.com/YNUCPC/cpc-hp.svg?branch=master)](https://travis-ci.com/YNUCPC/cpc-hp)


横浜国立大学競技プログラミング部のホームページのソースです。
ホームページは[こちら](https://ynucpc.github.io/)

## 目次

- [ディレクトリ構造](#ディレクトリ構造)
- [必要なもの](#必要なもの)
- [準備](#準備)
- [ブログの記事の書き方](#ブログの記事の書き方)
- [その他](#その他)

## ディレクトリ構造

```
./
├.editorconfig      # エディタの設定ファイル
├.gitignore         # gitの設定ファイル
├.gitmodules        # gitの設定ファイル
├.travis.yml        # Travis CIの設定ファイル
├README.md          # これ
├config.toml        # ホームページの設定ファイル
├archetypes/        # 記事のテンプレート
├content/           # サイトのコンテンツ
├data/              # トップページのデザインとか
├i18n/              # 多言語対応用
├layouts/           # レイアウト用のhtmlファイル群
├static/            # 画像,css,jsはココ
└themes/            # サイトに適用するテーマ
```

## 必要なもの

- [Hugo](https://gohugo.io/)
- [git](https://git-scm.com/)
- Webブラウザ

## 準備

**より詳しい説明は[こちら](/content/blog/howtopost.md)にあります**

1. Hugoをインストール([参考](https://gohugo.io/getting-started/installing/))\*
1. gitをインストール([参考](https://git-scm.com/book/ja/v2/%E4%BD%BF%E3%81%84%E5%A7%8B%E3%82%81%E3%82%8B-Git%E3%81%AE%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB))
1. ローカルにリポジトリをクローンする
```
git clone --recursive https://github.com/YNUCPC/cpc-hp.git
```

\*Hugoのインストールをapt-getで行うとバージョンが合わない場合があるようです。

## ブログの記事の書き方
#### 記事更新用のブランチを作成  
```
git checkout -b blog
```
#### 記事のファイルを作成
```
hugo new blog/post_name.md
```
#### content/blog/post_name.mdが作成されるので、エディタで編集する
#### 上手く出来てるか確認
```
hugo server
```
`http://localhost:1313`にアクセスすると確認できます
#### 上手く出来てたらコミットしてプッシュ！
```
git add content/blog/post_name.md
git commit -m "Add new post"
git push origin blog
```
#### Pull Requestを立てる
#### 誰かがmasterにマージする
#### おわり

## その他

記事にはMarkdown記法が使用できます  
Hugoの[universal](https://github.com/devcows/hugo-universal-theme)というテーマを使用しているので、
詳しい機能は[デモサイト](http://themes.gohugo.io/theme/hugo-universal-theme/)と
そのソースコードを見比べるとわかります

サンプルの記事もあるので、記法について参考にしてください。  
サンプルの記事はdraft属性がtrueになっていますが、以下のコマンドを実行すると
draft属性がtrueになっている記事も確認することが出来ます。
```
hugo server -D
```

また、Shortcodesという機能も使用することが出来ます。  
Shortcodeについては[こちら](https://gohugo.io/content-management/shortcodes/)を参考にしてください。

#### gitについて

- 簡単な（？）説明 https://anond.hatelabo.jp/20190203175803
- もうちょっとちゃんと知りたい人は[サルでもわかるgit入門](https://backlog.com/ja/git-tutorial/)とかを読むと良いかもしれません
- コマンドよりGUIの方が良いという人は、[Sourcetree](https://ja.atlassian.com/software/sourcetree)や[GitKraken](https://www.gitkraken.com/)などを使うと良いと思います

#### ホームページの仕組みについて

静的サイトジェネレータのHugoで作ったページを[Github Pages](https://pages.github.com/)で公開しています。  
masterブランチにcommitすると、[Travis CI](https://travis-ci.org/)が自動的に[ynucpc.github.io](https://github.com/YNUCPC/ynucpc.github.io)リポジトリに[デプロイ](https://www.weblio.jp/content/%E3%83%87%E3%83%97%E3%83%AD%E3%82%A4)してくれます。
