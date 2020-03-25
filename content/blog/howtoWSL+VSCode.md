---
title: "WSL+VSCodeで競技プログラミング環境構築"
date: 2020-03-24T21:23:10+09:00
draft: true
tags: ["VSCode","Windows","環境構築"]
categories: ["競技プログラミング入門"]
author: "NOSS"
images: ["/img/banners/howtoWSL+VSCode.png"]
lastmod: 2020-03-24T21:23:10+09:00
---

ここでは競技プログラミング入門者向けにWindowsでC/C++の環境構築をする方法について紹介します。

<!--more-->

使用するのは Ubuntu と Visual Studio Code です。

比較的簡単に快適な環境が整うはずです。序盤が一番難しいと思いますが頑張りましょう。

Mac OSの方は[こちら](https://ynucpc.github.io/blog/2018/04/15/cp_vscode/)を参考にしてください。

### 環境

Windows 10

---

## Windows Subsystem for Linux

Windows Subsystem for Linux (以降 WSL) はWindows上でLinuxを動作させるためのものです。

LinuxとはいわゆるOSの1つですが、Linux上で提供されているソフトウェアがプログラミングやサーバー管理をする上で便利であるため、好まれて利用されています。

今回はC/C++で書かれたソースコードを実行できるようにするためにLinuxを導入します。

### WSL の有効化

まずはWSLを利用するため機能を有効化します。

#### PowerShell

画面下のタスクバーにある検索バーに`PowerShell`と入力すると「Windows PowerShell」が検索結果に現れるので右クリック->「管理者として実行する」をクリックします。ユーザーアカウント制御のダイアログが出てきたら「はい」をクリックします。

すると、コンソールが立ち上がります。管理者として起動できていればタイトルバーに「管理者」と表示されています。

<center>
{{< figure src="/img/blog/howtoWSL+VSCode/Windows PowerShell.png" width="600" caption="PowerShellのコンソール画面">}}
</center>

`PS C:/WINDOWS/system32>`と書かれた部分に以下のコマンドをコピー&ペーストしEnterを押します。

```powershell
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```

完了すると再起動を促されるので再起動します。これでWSLの有効化は完了です。

<!--
#### コントロールパネル
検索欄に`コントロールパネル`と入力しコントロールパネルを開きます。コンロールパネルを開いたら「プログラム」->「プログラムと機能」を選択し「Windowsの機能の有効化または無効化」を開きます。  
真ん中付近に「Windows Subsystem for Linux」という項目があるのでこれをチェックが入った状態にします。チェックが入っていることを確認したら「OK」をクリックしコントロールパネルを閉じます。
-->

### Bash on Ubuntuのインストール

Linuxのディストリビューションには様々ありますが、今回はUbuntuを使用します。

Microsoft Storeを開き検索バーに`ubuntu`と入力し検索します。

<center>
{{< figure src="/img/blog/howtoWSL+VSCode/Microsoft Store_0.png" width="600" caption="Ubuntuの検索結果" >}}
</center>

Ubuntu 18.04 LTSを選択し、「入手」からインストールします。

<center>
{{< figure src="/img/blog/howtoWSL+VSCode/Microsoft Store_1.png" width="600" caption="Ubuntu 18.04 LTS" >}}
</center>

うまくインストール出来なかった場合はWSLが有効になっているか確認してみてください。

参考: https://docs.microsoft.com/ja-jp/windows/wsl/install-win10

---

## Ubuntu側の準備

C/C++で書かれたソースコードを実行するためにはコンパイルを行い実行ファイルに変換する必要があります。ここではUbuntuに GCC というコンパイラ―をインストールします。

### Ubuntuの初期化

先ほどインストールしたUbuntuを起動します。

Ubuntuを初めて起動すると、Ubuntuで使用するユーザー名とパスワードの設定が求められます。**今後も度々パスワードの入力が求められることがあるのでわかりやすいパスワードにすることをおすすめします。** また、パスワードの入力中は何も表示されないため文字数が確認できないことに注意してください。

参考: https://docs.microsoft.com/ja-jp/windows/wsl/initialize-distro

### GCCのインストール

初期設定が完了したら、まず以下のコマンドを入力しパッケージを更新します。パスワードや許可が求められたら応じてください。

```bash
sudo apt update
sudo apt upgrade
```

Ubuntuでは更新やアップグレードは自動的に行われないので定期的に行いましょう。

続いてGCCをインストールします。

```bash
sudo apt install build-essential
```

最後に以下のコマンドを入力してGCCのバージョンが表示されればGCCがインストールされています。

```bash
gcc --version
```

確認ができたらコンソールを閉じます。これでUbuntu側の準備は完了です。

---

## Visual Studio Code の準備

Visual Studio Code (略して VSCode ) はプログラムを書くためのエディタです。

### VSCodeのインストール

公式サイト https://code.visualstudio.com/ にアクセスし、「Download for Windows」をクリックします。

するとページが切り替わりインストーラー(`VSCodeUserSetup-x64-x.xx.x.exe` x-xx.xは現在のバージョン) がダウンロードされます。

<center>
{{< figure src="/img/blog/howtoWSL+VSCode/VSCode HP_0.png" width="700" caption="VSCodeの公式HP" >}}
</center>

ダウンロードが完了すると Google Chrome の画面下部にファイルが表示されているのでクリックしインストーラーを起動します。あるいはダウンロード先のフォルダを開いて起動してもかまいません。

<center>
{{< figure src="/img/blog/howtoWSL+VSCode/VSCode HP_1.png" width="600" caption="ダウンロード完了画面" >}}
</center>

インストーラーを起動するとセキュリティの警告が出るかもしれませんがそのまま実行します。使用許諾契約書を確認し同意した後「次へ」をクリックします。

<center>
{{< figure src="/img/blog/howtoWSL+VSCode/setup_0.png" width="600" caption="使用許諾契約書に同意" >}}
</center>

インストール先のフォルダはデフォルトのまま「次へ」をクリック。

<center>
{{< figure src="/img/blog/howtoWSL+VSCode/setup_1.png" width="600" caption="インストール先の指定" >}}
</center>

スタートメニューにショートカット作成します。そのまま「次へ」をクリック。

<center>
{{< figure src="/img/blog/howtoWSL+VSCode/setup_2.png" width="600" caption="スタートメニューにVSCodeのショートカットを作成" >}}
</center>

デスクトップ上にショートカットアイコンを作成する設定とPATHの設定を行います。

- デスクトップ上にアイコンを作成する
- サポートされているファイルの種類のエディターとして、Codeを登録する
- PATHへの追加(再起動後に使用可能)

にチェックを入れて「次へ」をクリックします。

<center>
{{< figure src="/img/blog/howtoWSL+VSCode/setup_3.png" width="600" caption="デスクトップ上にVSCodeのショートカットを作成、PATHの追加" >}}
</center>

インストール内容の確認画面になります。「インストール」をクリックするとVSCodeのインストールが開始します。

<center>
{{< figure src="/img/blog/howtoWSL+VSCode/setup_4.png" width="600" caption="インストール内容の確認" >}}
</center>

完了したら「完了」をクリックしてインストール完了です。

---

## VSCodeの設定

VSCodeを起動します。

初めて起動すると次のような画面が表示されると思います。

<center>
{{< figure src="/img/blog/howtoWSL+VSCode/VSCode Welcome.png" width="600" caption="Welcome" >}}
</center>

デフォルトでは表示言語が英語になっているので扱いやすいように日本語化を行います。

### 日本語化

公式の拡張機能をインストールして日本語化を行います。

画面左端にあるアイコン欄から一番下のExtensionsをクリックします。(4つのブロックからなるマーク)

<center>
{{< figure src="/img/blog/howtoWSL+VSCode/VSCode extention_0.png" width="600" caption="Extentionsをクリック" >}}
</center>

すると、拡張機能一覧が表示されるので一番上の検索欄に`Japanese`と入力します。  
拡張機能一覧の上の方にMicrosoft製の「Japanese Language Pack for Visual Studio Code」という拡張機能があると思うのでこちらを「install」します。

<center>
{{< figure src="/img/blog/howtoWSL+VSCode/VSCode extention_1.png" width="600" caption="日本語化パッケージをインストール" >}}
</center>

日本語化を適用するためにはVSCodeを再起動する必要があります。「Would you like to change ... restart?」とメッセージで聞かれるので「Yes」をクリックするか、VSCodeを一度閉じてから再び起動します。これで日本語化は完了です。

<center>
{{< figure src="/img/blog/howtoWSL+VSCode/VSCode extention_2.png" width="600" caption="日本語化パッケージをインストール" >}}
</center>

以降では日本語化を前提に説明を続けます。

### 基本設定

メニューから「ファイル」->「基本設定」->「設定」を選択するとVSCodeの様々な設定を行うことができます。

<center>
{{< figure src="/img/blog/howtoWSL+VSCode/VSCode setting_0.png" width="600" caption="設定画面" >}}
</center>

ここではすべてを説明することはできないので必要最低限の設定を行います。

設定を開いた状態で右上のアイコンから「設定(JSON)を開く」をクリックし設定ファイルを開きます。

<center>
{{< figure src="/img/blog/howtoWSL+VSCode/VSCode setting_1.png" width="600" caption="右上のアイコン" >}}
</center>

設定ファイル(`settings.json`)を開いたら以下の設定を追加します。

```json
{
    "files.autoSave": "afterDelay",
    "terminal.integrated.shell.windows": "C:\\Windows\\System32\\bash.exe"
}
```

設定内容はファイルの自動保存を有効にし、VSCode上で開くターミナルを先ほどインストールしたUbuntuにしています。

設定の入力が完了していると次のようになっていると思います。

<center>
{{< figure src="/img/blog/howtoWSL+VSCode/VSCode setting_2.png" width="600" caption="settings.jsonの設定例" >}}
</center>

これで設定は完了です。

ここまででC/C++の環境構築は完了しました。おつかれさまでした。

---

## C++を書いてみよう

さっそくC++のソースコードを書いて実行してみましょう。

その前にまずC/C++の拡張機能をインストールします。日本語化のときと同様に拡張機能の検索バーに`c`と入力すると上の方にMicrosoft製の「C/C++」という拡張機能が出てくると思うのでこれをインストールします。

<center>
{{< figure src="/img/blog/howtoWSL+VSCode/cpp_0.png" width="600" caption="C/C++の拡張機能" >}}
</center>

拡張機能がインストールできたら上部のメニューから「ファイル」->「フォルダーを開く」から好きなフォルダーを開いてください。これからプログラムのファイルを置く場所になります。

<center>
{{< figure src="/img/blog/howtoWSL+VSCode/cpp_1.png" width="600" caption="フォルダーを開く" >}}
</center>

私は今回ユーザーフォルダー下に workspace というフォルダーを新しく作成して開きました。

フォルダーを開いたら左にエクスプローラーの欄に「新しいフォルダー」というボタンがあるのでこれを押します。するとフォルダーの名前入力欄が出るので `cpp-study` と入力してEnterを押します。

<center>
{{< figure src="/img/blog/howtoWSL+VSCode/cpp_2.png" width="600" caption="新しいフォルダー" >}}
</center>

続いて`cpp-study`のフォルダを選択した状態で「新しいファイル」のボタンを押します。ファイルの名前入力欄がでるので `hello.cpp` と入力してEnterを押します。

C++のソースコードファイルは `.cpp`という拡張子にするルールになっています。

<center>
{{< figure src="/img/blog/howtoWSL+VSCode/cpp_3.png" width="600" caption="新しいファイル" >}}
</center>

ファイルが作成できたら次のソースコードをコピー&ペーストしてください。

```cpp
#include <iostream>

using namespace std;

int main(){
    cout << "Hello, World!" << endl;
    cout << 1+2 << endl;
    return 0;
}
```

ここまでできたら下の画像のようになっているはずです。

<center>
{{< figure src="/img/blog/howtoWSL+VSCode/cpp_4.png" width="600" caption="ソースコードの記述まで" >}}
</center>

ソースコードが書けたらキーボードで (`Ctrl + @`) を押してください。

するとターミナルが開きます。設定でターミナルをUbuntuに出来ていれば「1:bash」のように表示されているはずです。

<center>
{{< figure src="/img/blog/howtoWSL+VSCode/cpp_5.png" width="600" caption="ターミナルの起動" >}}
</center>

それではソースコードのコンパイルを行いましょう。ターミナルに次のコマンドを入力します。

```bash
cd cpp-study
g++ hello.cpp
```

`cd`は Change Directory の略で現在いるディレクトリ(Windowsでいうフォルダー)を後ろで指定したものに変更します。

`g++`はGCCでコンパイルを行うためのコマンドです。後ろにコンパイルしたいファイルを指定して使用します。

しばらくするとコンパイルが終了し `a.out` というファイルがエクスプローラーの欄に表示されているはずです。  
これが実行ファイルになります。ターミナルに次のようにコマンドを入力して実行します。

```bash
./a.out
```

すると、

```text
Hello, World!
3
```

と表示されたのではないでしょうか。

これでプログラムが実行されていることが確認できました。Hello,World! や数式の部分を変更してから

```bash
g++ hello.cpp
./a.out
```

と、コンパイルと実行をした結果がどうなるか試してみてください。

参考: https://code.visualstudio.com/docs/cpp/config-wsl

## おわりに

これで自分のPCでC/C++が実行できるようになったと思います。

このままプログラミングの練習をしたい方は初心者向け問題集 [AtCoder Beginners Selection](https://atcoder.jp/contests/abs) に挑戦してみてください。

また、C++の基礎を学びたい方は [AtCoder](https://atcoder.jp/home) 提供のC++入門教材 [APG4b](https://atcoder.jp/contests/APG4b) に取り組むのがおすすめです。

それではよい競プロライフを！

#### 参考記事

- https://qiita.com/yo_kanyukari/items/37421f497b7ffaa75502
- https://qiita.com/AokabiC/items/e9312856f588dd9303ed#vscode%E5%81%B4%E3%81%AE%E8%A8%AD%E5%AE%9A
