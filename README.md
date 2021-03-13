# study anaconda
anaconda (miniconda) を使った環境構築方法

## はじめに

python のインストール方法として
1. python.org https://www.python.org/ からダウンロードしてインストールする
1. Anaconda https://www.anaconda.com/products/individual をインストールする

という方法があります。（mac や linux はもともとインストールされていることもあります。）

どのインストール方法でも構いませんが，Fintalkでは pandas / numpy / jupyter をつかった株式分析をメインに行うので，その環境を手軽に備えることができる Anaconda の軽量版 **miniconda** を採用することにしました。

### なぜ miniconda 

Anaconda は，分析をするためのライブラリが大量に入っている「全部入り」状態なのでとてもスペースを食ってしまいます。

いっぽう，minicondaは， python と conda (パッケージ管理システム) しか入っていません。自分に必要なライブラリを適宜入れていけばよく，非力なマシンでも問題ありません。よって Fintalk では miniconda を採用することにしました。

### conda と pip 

python には パッケージ管理システムとして [pip](https://www.python.jp/install/windows/pip.html) が標準装備されています。

パッケージ管理システムとは，ソフトウェアのインストールやアンインストールを管理してくれるツールです。

ではなぜ今回 pip ではなく、conda を選んだのかというと，condaはソフトウェア同士の依存関係を管理してくれるからです。

conda でソフトウェアをインストールする時，すでにインストールされているソフトウェアとの関係を確認してくれます。もしインストールが問題を起こす可能性がある場合は事前に警告してくれます。

一方，pip は，依存関係を確認せずインストールします。そうすると時々，「インストールしたら動かなくなった」事件が起きることがあります。それに付き合うのは面倒なので， conda にしました。

しかし，しばしば conda では提供されていないが pip では提供されているソフトウェアがあります。それは pip でインストールするしかありません。


### インストールと環境構築までの大まかな流れ

1. miniconda インストール
1. 仮想環境の作成（初回のみ）
1. 仮想環境に入る（毎回）
1. 必要なライブラリをインストールする（初回のみ）

### 仮想環境とは

しばしば，「環境がぶつかって動かなくなった」みたいな（アホ）コメントをインターネッツでお見かけしますが，そのような情弱行動を起こさないようにするための一般教養が，仮想環境構築です。

イメージとしては，

> Pythonを実行するための場所を用意すること

です。そして

> そのような場所を複数作って構わない。

ということを覚えておいて下さい。その場所のことを仮想環境と呼びます。

## install 

+ windows: https://github.com/fintalk/study-anaconda/tree/main/install/windows
+ mac: https://github.com/fintalk/study-anaconda/tree/main/install/mac
+ linux: https://github.com/fintalk/study-anaconda/tree/main/install/linux

## 環境構築

### はじめに
+ [ターミナル]もしくは[Anaconda prompt]をここではまとめて **ターミナル** と称します。
+ **windows**：Anaconda promptであって command prompt や Anaconda Powershellでは無いことに気をつけてください
    ![](https://i.imgur.com/dmwQ6Yi.png)
+ ターミナルでインプットするコマンドの前には `$` もしくは `>` を付けています。それがついていない場合は出力例です。
+ ターミナルでインプットするコマンドは `$` もしくは `>` 以降のコマンドだけインプットして下さい
+ `#` はコメントです。

### 仮想環境作成
1. ターミナル起動
1. 現時点でのPythonの path を確認
    + Python の path とは： 今開いているのターミナルで実行出来るPythonがインストールされているディレクトリ
    
    ```bash
    # mac / linux 
    $ which python
    ```
    
    ```bash
    # windows
    > where python
    ``` 
1. **仮想環境作成**
    anaconda/miniconda で仮想環境を作るには，`conda create` というコマンドを実行します。実行コマンドは：
    ```bash
    $ conda create --name <仮想環境名> python=<pythonのバージョン>
    ``` 

    例：py38という名前で，python3.8の環境を作成する。
    ```bash
    $ conda create --name py38 python=3.8
    ``` 
    + 名前は任意です。なんでも構いません。よく使う名前は，install する python のバージョンや，特定の作業名（web-scraping ) など。
    + いくつでも仮想環境を作成することが出来ます。私は python3.6，3.7，3.8と3つ別々に環境を作っています。

### 仮想環境に入る
仮想環境を作成後，**仮想環境に入ってはじめてその環境のPythonを使用**できます。これはターミナルを立ち上げるたびに毎回必ず入らなくてはいけません。よってまず「**ターミナルを立ち上げたら毎回仮想環境に入るクセ**」を付けて下さい。    

（注：bashやエディタの設定等で，仮想環境に自動で入る設定がありますが，まずは自分で入るクセを付けて下さい。そういうのをめんどくさがる人は，たいてい後で必ず「環境がぶつかって動かなくなった」みたいな（アホ）コメントを言ってきがち。）

1. 環境へ入る
    ```bash
    $ conda acitivate <仮想環境名>
    ```
    ```bash
    # 例
    $ conda activate py38
    ```
1. path を確認。先程 `現時点でのPythonの path を確認` で確認したパスとは違う、今作った仮想環境へのパスが表示されるはずです。
    ```bash
    # mac / linux 
    $ which python
    ```
    ```bash
    # windows 
    > where python
    ``` 
    この，`which python` や `where python` もクセ付けると幸せになると思います。
    

### 必要なライブラリをインストール

1. 仮想環境に入る
1. [Anaconda Cloud](https://anaconda.org/) で目的のライブラリを検索。 もしくは、 `anaconda install <ライブラリ名>` でググる。
1. `To install this package with conda run:` で示されたコマンドを仮想環境で実行
1. anaconda で提供されていない場合
    1. 仮想環境に入っている pip でインストールする
    1. https://pypi.org/ で目的のライブラリを検索。もしくは`pip install <ライブラリ名>` で検索
    1. `pip install xxxxxxxx` で示されたコマンドを仮想環境で実行

### 作成済みの仮想環境リストを表示

`conda env list` で作成した仮想環境リストを取得できます。また、現在のターミナルで有効な仮想環境には、 `*` マークがついています。例：

```bash
$ conda env list
# conda environments:
#
base                     /home/username/miniconda3
env_zipline              /home/username/miniconda3/envs/env_zipline
py36                     /home/username/miniconda3/envs/py36
py37                  *  /home/username/miniconda3/envs/py37
```

### 作成した仮想環境を削除したい場合

```bash
# conda remove -n <仮想環境名> --all
# 例
$ conda remove -n py37 --all
```

### miniconda 自体をアンインストール
+ windows [Uninstalling conda](https://docs.conda.io/projects/conda/en/latest/user-guide/install/windows.html#uninstalling-conda)
+ mac [Uninstalling Anaconda or Miniconda](https://docs.conda.io/projects/conda/en/latest/user-guide/install/macos.html#uninstalling-anaconda-or-miniconda)

## 練習

### 仮想環境構築
1. ターミナル もしくは コマンドプロンプトを新しく開いて下さい（以下、呼称はターミナルに統一します）
1. `py37` という名前の仮想環境をPython3.7で作成して下さい。
1. `py37` 仮想環境に入って下さい
1. 現在のターミナルでpython への path を確認して下さい。
1. 以下のライブラリをインストールして下さい。※一部 conda ではインストールできないライブラリがあります。
    + numpy 
    + jupyter
    + beautifulsoup
    + requests-html
1. 一度ターミナルをクローズして下さい
1. 再度 ターミナルをオープンして、仮想環境に入り、pythonのインタプリタに入って、上記ライブラリを import してみてください。エラーがでなければ、練習問題は終りです。

## 仮想環境でよくあるミス

### 仮想環境に入ったつもりで入っていない
ターミナルを開いたら必ず `where python` もしくは `which python` でどの python を実行しようとしているか常に確認してください。

### 配布された jupyter notebook にマジックコマンドがある

たとえば， https://github.com/noguhiro2002/100knocks-preprocess_ForColab-AzureNotebook/blob/master/preprocess_knock_Python_Colab.ipynb の最初のセルに， pip でライブラリをインストールするコマンドがあります。
```python
# pipでオリジナルの解答に必要なライブラリーをインストール
!pip install --upgrade pip
!pip install -U pandas numpy scikit-learn imbalanced-learn
```

こういうセルを見かけら，実行する前にコメントアウトして下さい。

そして，仮想環境下で conda でインストールして下さい。















