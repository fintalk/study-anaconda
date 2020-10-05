# study anaconda
anaconda (miniconda) を使った環境構築方法

## はじめに

python のインストール方法として
1. python.org https://www.python.org/ からダウンロードしてインストールする
1. Anaconda https://www.anaconda.com/products/individual をインストールする
1. もともとPCにインストールされている（Mac/Linux）

という方法があります．

どのインストール方法でも構いませんが，Fintalkでは pandas / numpy / jupyter をつかった株式分析をメインに行うので，その環境が一度に揃う <font color=red>**Anaconda の軽量版 Miniconda**</font>を使います．

### なぜ miniconda 

anaconda は，分析をするためのライブラリがいわゆる全部入りなので，すぐには必要のないライブラリも入っています．とても大きくなってしまうので必要最小限の miniconda をいれて必要時に適切なインストールをすればOK

### 大まかな流れ

1. miniconda インストール
1. 仮想環境の作成（初回のみ）
1. 仮想環境に入る（毎回）
1. 必要なライブラリをインストールする（初回のみ）

### 仮想環境とは

しばしば，「環境がぶつかって動かなくなった」みたいな（アホ）コメントをインターネッツでお見かけしますが，まさにその環境がぶつかって動かなくなるという情弱行動を起こさない用にするための一般素養が，仮想環境構築です．

イメージとしては，

> Pythonを実行する時は毎回必ずインストールした場所からPythonを実行すること

です．そして

> そういう場所を複数作って構わない

ということを覚えておいて下さい．その場所のことを仮想環境と呼びます．

## install 

+ windows: `install/windows/install.md`
+ mac: `install/mac/install.md` 

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








