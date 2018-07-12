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

- Github Desktopをインストールしておく。
　https://desktop.github.com/

- Anacondaをインストールしておく。
　https://www.python.jp/install/windows/anaconda/install_anaconda.html
　※ディフォルト設定でOK

- MariaDBをインストールしておく。
  https://mariadb.org/
  ※MariaDBをインストールすると、HeidiSQLというGUIのDB管理ソフトウェアもインストールされる。MariaDBはコマンドラインで操作しても、HeidiSQLから操作してもOK。ユーザ名、パスワード、データベース名は、config.ipynbを使って ./config.ini として保存しておく。
 

1. GithubのC4RAのリポジトリ（https://github.com/c4ra/kaken_parse_grants_masterxml ）にアクセスし、右端にある「Clone or download」をクリック。
2.「Open in Desktop」をクリック。
3. あらかじめインストールしておいたAnacondaに同報されている「Jupyter Notebook」を起動し、保存したGithubのC4RAのリポジトリを表示させる。

これで準備は完了です。


## 1. 設定ファイルを作成する

1. 「Jupyter Notebook」でcongig.ipynbを選択しRunを押す。（しばらく待っているとカレントディレクトリにconfig.iniが作られます。）

2. 作成された「config.ini」をエディタソフト（メモ帳でもvscodeなど）で開き、左辺のそれぞれの設定項目に対して、右辺に自分のIDやパスワードがちゃんと入っているか確認する。
　
※これまでの試した人の意見として、いきなり引っ掛かりがちな箇所です。
※別の方法として、適当なテキストエディタで直接入力して作っても差し支えありません。

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

1. 下記ファイルに記載してある手順にしたがう
- kaken_zenkadai_download.ipynb

## 4-2. KAKENからダウンロードしたXMLファイルをパースしてローカルのMariaDBに保存する

1. それぞれのファイルに記載してある手順にしたがう
- parse_grantaward_main.ipynb　…　部品1
- parse_grantaward_institution_from_grantlist.ipynb　…　部品2
- parse_grantaward_member_from_summary.ipynb　…　部品3
- parse_grantaward_integration.ipynb　…　3つの部品を統合する

「1. 設定ファイルを作成する」の後は順不同です。
