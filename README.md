# cpc-hp [![Build Status](https://travis-ci.org/YNUCPC/cpc-hp.svg?branch=master)](https://travis-ci.org/YNUCPC/cpc-hp)


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

1. Hugoをインストール([参考](https://gohugo.io/getting-started/installing/))
1. gitをインストール([参考](https://git-scm.com/book/ja/v2/%E4%BD%BF%E3%81%84%E5%A7%8B%E3%82%81%E3%82%8B-Git%E3%81%AE%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB))
1. ローカルにリポジトリをクローンする
```
git clone https://github.com/YNUCPC/cpc-hp.git
```

## ブログの記事の書き方
1. 記事更新用のブランチを作成
```
git checkout -b blog
```
1. 記事のファイルを作成
```
hugo new blog/post_name.md
```
1. content/blog/post_name.mdが作成されるので、エディタで編集する
1. 上手く出来てるか確認
```
hugo server
```
`http://localhost:1313`にアクセスすると確認できます
1. 上手く出来てたらコミットしてプッシュ！
```
git add content/blog/post_name.md
git commit -m "Add new post"
git push origin blog
```
1. Pull Requestを立てる
1. 誰かがmasterにマージする
1. おわり

## その他

記事にはMarkdown記法が使用できます  
Hugoの[universal](https://github.com/devcows/hugo-universal-theme)というテーマを使用しているので、
詳しい機能は[デモサイト](http://themes.gohugo.io/theme/hugo-universal-theme/)と
そのソースコードを見比べるとわかります(そのうち説明追記します)
