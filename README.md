# kaken_parse_grants_masterxml


## ファイルについて

- config.ipynb …　設定ファイルです
- category_master.ipynb　…　研究種目マスタです
- institution_master.ipynb　…　研究機関マスタです
- section_master.ipynb　…　配分区分マスタです
- kaken_zenkadai_download.ipynb …　KAKENデータベースからXMLファイルをダウンロードするプログラムです

以下、KAKENからダウンロードしたXMLファイルをパースしてローカルのMariaDBに保存するプログラム
- parse_grantaward_main.ipynb　…　部品1
- parse_grantaward_institution_from_grantlist.ipynb　…　部品2
- parse_grantaward_member_from_summary.ipynb　…　部品3
- parse_grantaward_integration.ipynb　…　3つの部品を統合する


## 0. 事前準備

- [Github Desktop](https://desktop.github.com/)をインストールしておく。
　
- [Anaconda](https://www.python.jp/install/windows/anaconda/install_anaconda.htm)をインストールしておく[^1]。
　[^1]:ディフォルト設定でOK

- [MariaDB] https://mariadb.org/)をインストールしておく[^2][^3][^4]。
 
  [^2]:[windowsの場合の設定](https://www.trifields.jp/how-to-install-mariadb-on-windows-2440)
  [^3]:MariaDBをインストールすると、HeidiSQLというGUIのDB管理ソフトウェアもインストールされる。MariaDBはコマンドラインで操作しても、HeidiSQLから操作してもOK。ユーザ名、パスワード、データベース名は、config.ipynbを使って ./config.ini として保存しておく。
  [^4]:ユーザー名はrootのままがお勧め。
 

1. [GithubのC4RAのリポジトリ](https://github.com/c4ra/kaken_parse_grants_masterxml)にアクセスし、右端にある「Clone or download」をクリック。

![C4RAレポジトリのClone](https://files.slack.com/files-pri/TB5TT043E-FBDMHR7UJ/step2.png)

2.「Open in Desktop」をクリック。
3. あらかじめインストールしておいたAnacondaに同報されている「Jupyter Notebook」を起動し、保存したGithubのC4RAのリポジトリを表示させる。

これで準備は完了です。


## 1. 設定ファイルを作成する

1. 「Jupyter Notebook」でcongig.ipynbを選択しRunを押す。（しばらく待っているとカレントディレクトリにconfig.iniが作られます。）

2. 作成された「config.ini」をエディタソフト（メモ帳でもvscodeなど）で開き、左辺のそれぞれの設定項目に対して、右辺に自分のIDやパスワードがちゃんと入っているか確認する。

3. （入っていなかった場合は）適当なテキストエディタで直接入力する。

※HeidiSQLの設定と合わせる必要があります！　
※これまでの試した人の意見として、いきなり引っ掛かりがちな箇所です。


## 2. bitbucketのKAKENマスタをローカルにパースする

1. GitHubの上部にあるメニューから「File>Clone a repository」を選択。
2. 「Clone a repository」というポップアップメニューが表示されるので、画面内の「URL」タブを選択後、Repository URL or GItHub user name and repositoryの欄に「https://bitbucket.org/niijp/grants_masterxml_kaken/
」を入力。「Clone」を押す。



## 3. KAKENマスタをパースしてローカルのMariaDBに保存する

1. それぞれのファイルに記載してある手順にしたがう
- category_master.ipynb　…　研究種目マスタ
- institution_master.ipynb　…　研究機関マスタ
- section_master.ipynb　…　配分区分マスタ

## 4-1. KAKENデータベースからXMLファイルをダウンロードする

0. anaconda promptからtqdmをインストールする[^5]。
[^5]:anaconda promptを立ち上げ、	<code><nowiki>conda install tqdm	</nowiki></code>と入力。しばらく待つと、Proceed ([y]/n)?と表示されるので、yを入力する。

1. 下記ファイルに記載してある「事前準備」に従い、CiNiiのwebAPI登録後発行されるappidを設定ファイルに書き込む。
　※configparserで別途appidを設定ファイルに書き込んでおく。は無視してOK。

2.「ここから本番」以降をRunする。
- kaken_zenkadai_download.ipynb

## 4-2. KAKENからダウンロードしたXMLファイルをパースしてローカルのMariaDBに保存する

1. それぞれのファイルに記載してある手順にしたがう
- parse_grantaward_main.ipynb　…　部品1
- parse_grantaward_institution_from_grantlist.ipynb　…　部品2
- parse_grantaward_member_from_summary.ipynb　…　部品3
- parse_grantaward_integration.ipynb　…　3つの部品を統合する

「1. 設定ファイルを作成する」の後は順不同です。
