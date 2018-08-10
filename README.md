# kaken_parse_grants_masterxml


## ファイルについて

- config.ipynb …　設定ファイルです
- category_master.ipynb　…　研究種目マスタです
- institution_master.ipynb　…　研究機関マスタです
- section_master.ipynb　…　配分区分マスタです
- field_master.ipynb　…　研究分野マスタです
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

- [MariaDB](https://mariadb.org/)をインストールしておく[^2][^3][^4]。
 
  [^2]:[windowsの場合の設定](https://www.trifields.jp/how-to-install-mariadb-on-windows-2440)
  [^3]:MariaDBをインストールすると、HeidiSQLというGUIのDB管理ソフトウェアもインストールされる。MariaDBはコマンドラインで操作しても、HeidiSQLから操作してもOK。ユーザ名、パスワード、データベース名は、config.ipynbを使って ./config.ini として保存しておく。
  [^4]:ユーザー名はrootのままがお勧め。
 

1. [GithubのC4RAのリポジトリ](https://github.com/c4ra/kaken_parse_grants_masterxml)にアクセスし、右端にある「Clone or download」をクリック。

![C4RAレポジトリのClone方法](https://files.slack.com/files-pri/TB5TT043E-FBDMHR7UJ/step2.png "C4RAレポジトリのClone方法")

2.「Open in Desktop」をクリック。
3. あらかじめインストールしておいたAnacondaに同報されている「Jupyter Notebook」を起動し、保存したGithubのC4RAのリポジトリを表示させる。

これで準備は完了です。


## 1. 設定ファイルを作成する

1. 「Jupyter Notebook」でcongig.ipynbを選択しRunを押す。（しばらく待っているとカレントディレクトリにconfig.iniが作られます。）

2. 作成された「config.ini」をエディタソフト（メモ帳でもvscodeなど）で開き、左辺のそれぞれの設定項目に対して、右辺に自分のID、パスワード、データベース名がちゃんと入っているか確認する。

3. （入っていなかった場合は）適当なテキストエディタで直接入力する。

  ※HeidiSQLの設定と合わせる必要があります！　
  ※これまでの試した人の意見として、いきなり引っ掛かりがちな箇所です。


## 2. bitbucketのKAKENマスタをローカルにパースする

1. GitHubの上部にあるメニューから「File>Clone a repository」を選択。
2. 「Clone a repository」というポップアップメニューが表示されるので、画面内の「URL」タブを選択後、Repository URL or GItHub user name and repositoryの欄に「https://bitbucket.org/niijp/grants_masterxml_kaken/
」を入力。「Clone」を押す [^5]。

  [^5]:Cloneは、作業フォルダ（今回の場合は、0-1でGitHubからダウンロードしたしたC4RAレポジトリ**kaken_parse_grants_masterxml**のフォルダ内に作る。）


## 3. KAKENマスタをパースしてローカルのMariaDBに保存する

0. category_master.ipynb、institution_master.ipynb、section_master.ipynbを使うにはpymysqlがインストールされている必要があります。
  初めて使うときには、anaconda promptからpymysqlをインストールする[^7]。
  [^7]:anaconda promptを立ち上げ、
  `conda install -c anaconda pymysql` 
  と入力。しばらく待つと *Proceed ([y]/n)?* と表示されるので、yを入力する。

1. それぞれのファイルに記載してある手順にしたがう
- category_master.ipynb　…　研究種目マスタ
- institution_master.ipynb　…　研究機関マスタ
- section_master.ipynb　…　配分区分マスタ


## 4-1. KAKENデータベースからXMLファイルをダウンロードする

0. kaken_zenkadai_download.ipynbを使うにはtqdmがインストールされている必要があります。
　初めて使うときには、anaconda promptからtqdmをインストールする[^6]。
  [^6]:anaconda promptを立ち上げ、
  `conda install tqdm`
  と入力。しばらく待つと *Proceed ([y]/n)?* と表示されるので、yを入力する。

1. 下記ファイルに記載してある「事前準備」に従い、CiNiiのwebAPI登録後発行されるappidを設定ファイルに書き込む。
  ※configparserで別途appidを設定ファイルに書き込んでおく。は無視してOK。

2.kaken_zenkadai_download.ipynbの「ここから本番」以降をRunする。


## 4-2. KAKENからダウンロードしたXMLファイルをパースしてローカルのMariaDBに保存する

1. それぞれのファイルに記載してある手順にしたがう
- parse_grantaward_main.ipynb　…　部品1
- parse_grantaward_institution_from_grantlist.ipynb　…　部品2
- parse_grantaward_member_from_summary.ipynb　…　部品3
- parse_grantaward_integration.ipynb　…　3つの部品を統合する

「2. bitbucketのKAKENマスタをローカルにパースする」の後は順不同です。

## おまけ 編集したREADMEのGithubへのpull request方法

0. GitHubからC4RAレポジトリのCloneを作っておく
1. 真ん中のCurrent branchボタンから、新しいブランチを作成します。
2. その状態で、Jupyter Notebook等で目的のファイルを編集して保存する。
3. （GitHub Desktopに移動するとそうすると、左側に編集されたファイルのリストが表示されているはずなので）コミットのメッセージを適当に入力してコミットする（左下あたり）。
4. その後、右上のボタンPublish branchをクリック。（これでpushされる）
![pull request方法](https://c4ra.slack.com/files/UB6213MH9/FBEPDUVFZ/step3.png "C4RAレポジトリへのpull request方法")

5. ブラウザで GitHubのC4RAレポジトリに移動すると、自分が編集したファイルの横に「New pull request」というボタンが表示されているので、それをクリック。
6. 続いて「Create pull request」という緑色のボタンが表示されるのでそれも押しておく。（自分とは別の人がmergeしてくれます）
