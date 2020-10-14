# study anaconda
anaconda (miniconda) を使った環境構築方法

## はじめに

python のインストール方法として
1. python.org https://www.python.org/ からダウンロードしてインストールする
1. Anaconda https://www.anaconda.com/products/individual をインストールする
1. もともとPCにインストールされている（Mac/Linux）

という方法があります．

どのインストール方法でも構いませんが，Fintalkでは pandas / numpy / jupyter をつかった株式分析をメインに行うので，その環境を手軽に備えることができる <font color=red>**Anaconda の軽量版 Miniconda**</font>を使います．

### なぜ miniconda 

Anaconda は，分析をするためのライブラリが大量に入っている「全部入り」状態なのでとてもスペースを食ってしまいます．

いっぽう，minicondaは， python と conda しか入っていないので，自分に必要なライブラリを適宜入れていけばよく，非力なマシンでも問題ありません．よって Fintalk では miniconda を採用することにします．


### インストールと環境構築までの大まかな流れ

1. miniconda インストール
1. 仮想環境の作成（初回のみ）
1. 仮想環境に入る（毎回）
1. 必要なライブラリをインストールする（初回のみ）

### 仮想環境とは

しばしば，「環境がぶつかって動かなくなった」みたいな（アホ）コメントをインターネッツでお見かけしますが，そのような情弱行動を起こさない用にするための一般教養が，仮想環境構築です．

イメージとしては，

> Pythonを実行するための場所を用意すること

です．そして

> そのような場所を複数作って構わない．

ということを覚えておいて下さい．その場所のことを仮想環境と呼びます．

## install 

+ windows: https://github.com/fintalk/study-anaconda/tree/main/install/windows
+ mac: https://github.com/fintalk/study-anaconda/tree/main/install/mac

## 環境構築

### 仮想環境作成
1. command prompt もしくは terminal 起動
1. （もし miniconda 以外で python をインストールしている方は) 現時点でのPythonの path 確認
    + Python の path とは：現在のターミナルで実行する時に呼び出している python が格納されているディレクトリへのパスです
    ```bash
    # mac / linux 
    which python
    ```
    ```bash
    # windows 
    where python
    ``` 
1. 仮想環境作成
    anaconda/miniconda で仮想環境を作るには，`conda create` というコマンドを実行します．そこへ仮想環境名とPythonのバージョンを指定します．
    ```bash
    conda create --name <仮想環境名> python=<pythonのバージョン>
    ``` 
    例：py38という名前で，python3.8の環境を作成する．
    ```bash
    conda create --name py38 python=3.8
    ``` 
    + 名前は任意です．なんでも構いません．
    + 名前を変えれば，いくつでも仮想環境を作成することが出来ます．私は python3.6，3.7，3.8と3つ別々に環境を作っています．

### 仮想環境に入る
仮想環境を作成しても，仮想環境に入らないと以前のPythonを使用することになります．基本的には「**ターミナルを立ち上げるたびに毎回仮想環境に入るクセ**」をまず付けて下さい．    
1. 環境へ入る
    ```bash
    conda acitivate py38
    ```
1. path を確認．最初の確認したパスではなく，仮想環境下のPythonへのパスが出てきたハズです．
    ```bash
    # mac / linux 
    which python
    ```
    ```bash
    # windows 
    where python
    ``` 

### 必要なライブラリをインストール

1. 仮想環境に入る
1. [Anaconda Cloud](https://anaconda.org/) で目的のライブラリを検索。 もしくは、 ` anaconda install <ライブラリ名> ` で検索してみる
1. `To install this package with conda run:` で示されたコマンドを仮想環境で実行
1. anaconda で提供されていない場合
    1. 仮想環境に入っている pip でインストールする
    1. https://pypi.org/ で目的のライブラリを検索。もしくは`pip install <ライブラリ名>` で検索
    1. `pip install xxxxxxxx` で示されたコマンドを仮想環境で実行

## 練習

### 仮想環境構築
1. ターミナル もしくは コマンドプロンプトを新しく開いて下さい（以下、呼称はターミナルに統一します）
1. `py37` という名前の仮想環境をPython3.7で作成して下さい。
1. `py37` 仮想環境に入って下さい
1. 現在のターミナルでpython への path を確認して下さい。
1. 以下のライブラリをインストールして下さい
    + numpy 
    + jupyter
    + bueatifulsoup
    + requests-html
1. 一度ターミナルをクローズして下さい
1. 再度 ターミナルをオープンして、仮想環境に入り、pythonのインタプリタに入って、上記ライブラリを import してみてください。エラーがでなければ、練習問題は終りです。

## 仮想環境でよくあるミス

### 仮想環境に入ったつもりで入っていない
+ 確認方法：ターミナルを開いたら必ず `where python` もしくは `which python` でどの python を実行しようとしているか常に確認














