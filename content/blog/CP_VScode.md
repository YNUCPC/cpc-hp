---
title: "VSCodeで始める競技プログラミング（環境構築編）"
date: 2018-04-15T14:42:07+09:00
draft: false
tags: ["VSCode", "環境構築", "macOS"]
categories: ["競技プログラミング入門"]
images: ["img/banners/vscode.png"]
---

入門者向けに競技プログラミングのはじめ方について説明します.  
使用するのはC++とVisual Studio Codeです.  
そこそこ簡単に競プロを始めるのを目指して紹介していきます.  

<!--more-->

### 環境
今回は, macOSで紹介していきます.  

# コンパイラのインストール
C++を実行形式に変換するために, C++用のコンパイラをインストールします.  
とは言ってもmacには,clangがデフォルトで入ってるはずです.  
以下のコマンドを実行して, `g++ not found`と出力されなければ,コンパイラは既に入っています.  
コンパイラが入っていた場合は次の**Visual Studio Code**のインストールに進んでください.  

```
which g++
```

コンパイラが入ってない場合は, ターミナルを起動します.  
ターミナルはFinderを開いて, よく使う項目 >> アプリケーション >> ユーティリティ と移動して, **ターミナル.app** をダブルクリックで起動できます.  

|{{< figure src="https://user-images.githubusercontent.com/19720977/38661080-909b4916-3e6a-11e8-994c-7ea89201f152.png" width="130" >}}|{{< figure src="https://user-images.githubusercontent.com/19720977/38661192-f6850294-3e6a-11e8-9bb2-6b380c0b95de.png" width="250" >}}|{{< figure src="https://user-images.githubusercontent.com/19720977/38661196-f9266a38-3e6a-11e8-9064-f1308c7de0cd.png" width="250" >}}|
|---|---|---|

ターミナルが起動したら, 次のコマンドを入力して**Return**を押します.

```
xcode-select --install
```

ウインドウが表示されたら**インストール**を押します.  
インストールが完了したらコンパイラのインストールは完了です.    

# VisualStudioCodeのインストール
Visual Studio Code(以下VSCode)は, Microsoftが開発したGUIのエディタです.　  
デバッグ, Gitクライアントとの統合, シンタックスハイライトなどの機能があり, 拡張機能が豊富です.  
競プロのような1つのファイルで完結するようなプログラムを記述する際はIDEよりもエディタの方が適しています.  

早速VSCodeをインストールしましょう.  
VSCodeの公式サイト(https://code.visualstudio.com/)のトップにある, 緑の**Download for Mac**(Macの場合)をクリックするとzipファイルがダウンロードされます.    
ダウンロードされたzipファイルを開くと, **Visual Studio Code.app** が出てきます.    
このappファイルをアプリケーションフォルダに移動すればインストール完了です.    

|{{< figure src="https://user-images.githubusercontent.com/19720977/38714153-d1f58318-3f0f-11e8-9c17-a516260b17dd.png" width="320" >}}|{{< figure src="https://user-images.githubusercontent.com/19720977/38714465-59355b22-3f11-11e8-9441-70c4099570be.png" width="320" >}}|
|:--:|:--:|
|VSCodeの公式サイトトップ|VSCodeのインストール|

# VisualStudioCodeの使い方
VSCodeを起動しましょう.  
起動直後は以下のような画面が表示されます.  
(前回開いていたウインドウの状態が復元する場合もあります)  
まず,フォルダを開く..クリックして適当なフォルダを選択します.  
今回はホームディレクトリ以下にCPPフォルダを作成して, そこを選択します.   
事前にターミナルで`mkdir -p ~/CPP`を実行してディレクトリを作っておきます.  

|{{< figure src="https://user-images.githubusercontent.com/19720977/38714714-6db0d666-3f12-11e8-9d1b-d0be16de239b.png" width="320" >}}|{{< figure src="https://user-images.githubusercontent.com/19720977/38714898-5bdc2ffc-3f13-11e8-8c4e-1c7b0b4c0b9e.png" width="320" >}}|
|:--:|:--:|
|起動直後|ディレクトリを開いた後|

先ほど開いたディレクトリ(~/CPP)はワークスペースのルートディレクトリになり, このディレクトリ以下でファイルを編集します.  
ファイルを新規作成するには, ワークスペースルートディレクトリ名横の**新しいファイル**をクリックします.  
ディレクトリを作成する場合は, その横の**新しいフォルダー**をクリックします.  

|{{< figure src="https://user-images.githubusercontent.com/19720977/38715220-d9518f62-3f14-11e8-9512-9117d8403204.png" width="320" >}}|{{< figure src="https://user-images.githubusercontent.com/19720977/38715221-d9874abc-3f14-11e8-9d21-0957e7beb120.png" width="320" >}}|
|:--:|:--:|
|新しいファイル|新しいフォルダー|

とりあえず,  **hello.cpp** というファイルを作成しましょう.  
 **新しいファイル** をクリックすると, ワークスペースルートディレクトリ以下にファイルが出現して, 名前を入力することができます.  
そこに **hello.cpp** と名前をつけて **return** を押すと, 右にエディタ画面が開きます.  
このエディタ画面でソースコードを記述します.  
とりあえず, **Hello, World** と出力するだけのソースコードを書いてみましょう.  

```cpp
#include <iostream>

int main(){
    std::cout << "Hello, World" << std::endl;
    return 0;
}
```

保存する場合は **⌘(command) + S** (commandを押しながらS) または上のツールバーから **ファイル>保存** です.  
ソースを保存したら, 早速実行してみましょう.  
**⌃(control)+⇧(shift)+@** を押すと統合ターミナルが開きます.    
起動直後はワークスペースルートディレクトリがカレントディレクトリになっています.  
以下のコマンドでファイルをコンパイルし, 実行できます.

```
g++ -std=c++11 hello.cpp
./a.out
```

1行目がコンパイルするコマンドです.   
コンパイルが完了すると, **a.out** という実行できるファイルが生成されます.  
-で始まる部分はオプションで, コンパイラの設定です.  
-std=c++11はC++11というバージョンのC++のソースコードをコンパイルするときに指定します.  
現在, 多くの競プロのオンラインジャッジではC++11またはC++14までに対応しているので, **-std=c++11** または **-std=c++14** を指定すれば大丈夫です.  
2行目で実行ファイルを実行しています.   
Hello, Worldと表示されれば大丈夫です.   

|{{< figure src="https://user-images.githubusercontent.com/19720977/38715308-555366c6-3f15-11e8-8585-816ab951eb7b.png" width="320" >}}|{{<figure src="https://user-images.githubusercontent.com/19720977/38715572-ee7accb2-3f16-11e8-8e30-43e79fa9cb3a.png" width="320" >}}|
|:--:|:--:|
|Hello.cpp|統合ターミナルを開いた状態|

# 拡張機能のインストール
VSCodeでは拡張機能をインストールすることでエディタをカスタマイズすることができます.  
快適に競プロをするために, 拡張機能を入れてみましょう.  

## C/C++
VSCode画面の一番左にアイコンが5つ縦に並んでいると思います.  
その一番下の **拡張機能** をクリックします.  
すると, 左タブに拡張機能選択画面が出現します.  
上のテキストボックス **Marketplaceで拡張機能を検索** の部分に **C/C++** と入力して **returnキー** を押して検索します.  
検索して一番上に出てきた, 同じ名前のものを **インストール** します.  
インストールが終了したら, 有効化するために **再度読み込む** をクリックするとVSCodeが再起動して拡張機能が有効化されます.  
今インストールしたのは言語サポートと呼ばれるもので以下のような機能を一括で提供してくれます.
* コードフォーマット
* 自動補完
* シンボルサーチ
* デバッグ機能のサポート

これらの機能については, 今回は説明を割愛します.  

|{{< figure src="https://user-images.githubusercontent.com/19720977/38716068-b2804310-3f19-11e8-975d-ea2ca16a1fd5.png" width="320" >}}|{{< figure src="https://user-images.githubusercontent.com/19720977/38716171-4b1a07aa-3f1a-11e8-81e1-57410dfef8d0.png" width="320" >}}|
|:--:|:--:|
|拡張機能画面|C/C++|

## C/C++ClangCommandAdapter
次に **C/C++ Clang Command Adapter** をインストールします.  
これは, C++の標準ライブラリなどの関数名補完をしてくれます.  
ちなみに, clangというコンパイラが必須です.  
(macの場合はデフォルトでclangなので大丈夫です)   
先ほどと同様に **C/C++ Clang Command Adapter** をインストールします.  
次に設定ファイルを編集します.
上のバーから **Code>設定>基本設定** を選択します.  
設定では2つのエディタが開きます.
左がデフォルトの設定で, 右が個人設定です.
基本的に設定を変更したい部分を左から右にコピーして編集します.  
右の設定が上書きされる形で設定が適用されます.  

テキストボックス**設定の検索**に**clang.executable**と入力します.  
すると, 左のエディタで一致する設定が現れます.  
左のエディタで該当する設定の行を選択すると, 鉛筆マークが出てきます.
それをクリックすると, 右のエディタに設定がコピーされます.  
そしたら, `"clang.executable": "clang++",`と修正してください.  
次に **clang.cxxflags** と検索して, 同様にコピーをして, ` "clang.cxxflags": [ "-std=c++14"],`と修正します.  
修正が完了したら, **⌘(command) + S** で設定を保存です.  

|{{< figure src="https://user-images.githubusercontent.com/19720977/38716588-7bd56ab8-3f1c-11e8-8a96-ca3417514f8e.png" width="320" >}}|{{< figure src="https://user-images.githubusercontent.com/19720977/38716622-cd627e52-3f1c-11e8-98a7-b3b837ee3239.png" width="320" >}}|
|:--:|:--:|
|C/C++ Clang Command Adapter|設定画面|

|{{< figure src="https://user-images.githubusercontent.com/19720977/38716872-08c0fe96-3f1e-11e8-940d-88a6fd67c2ca.png" width="680" >}}|
|:--:|
|設定例(右のエディタの16, 17行目を参照)

## CodeRunner
次に　**Code Runner** をインストールします.  
これは, ワンタッチでコンパイルをしてくれる機能です.  
同様に **Code Runner** と検索して同じ名前の機能をインストールしてください.  
C/C++ Clang Command Adapterと同様に設定を編集します.  
**code-runner.runInTerminal** と検索し編集します.
`"code-runner.runInTerminal": true,`と修正してください.  
次に **code-runner.executorMap** と検索し編集します.  
言語毎に設定するのですが, cppという行を探して, `"cpp": "cd $dir && g++ -O2 -std=c++14 $fileName && ./a.out",`と修正します.  
そして, **⌘(command) + S** で保存です.

|{{< figure src="https://user-images.githubusercontent.com/19720977/38717041-3a6fdaec-3f1f-11e8-91ca-3857d7cf97de.png" width="680">}}|
|:--:|
|設定例(右のエディタ21行, 26行を参照)|

ソースコードを開いている状態で, **⌃(control) + ⌥(option) + N** を押すとターミナルが開いて, コンパイル&実行してくれます.  

# 参考
* http://ecei-tohoku.github.io/ppa/docs/gcc_for_osx.html
* https://github.com/formulahendry/vscode-code-runner/issues/72
* https://www.bloguchi.info/1282
