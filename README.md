# kaken_parse_grants_masterxml

## 1. 設定ファイル作成

- config.ipynb

カレントディレクトリにconfig.iniが作られます。

これまでの試した人の意見として、いきなり引っ掛かりがちな箇所です。
別の方法として、適当なテキストエディタで直接入力して作っても差し支えありません。

## 2. bitbucketのKAKENマスタをパースしてローカルのMariaDBに保存するプログラム

- category_master.ipynb　…　研究種目マスタ
- institution_master.ipynb　…　研究機関マスタ
- section_master.ipynb　…　配分区分マスタ

## 3-1. KAKENデータベースからXMLファイルをダウンロードするプログラム

- kaken_zenkadai_download.ipynb

## 3-2. KAKENからダウンロードしたXMLファイルをパースしてローカルのMariaDBに保存するプログラム

- parse_grantaward_main.ipynb　…　部品1
- parse_grantaward_institution_from_grantlist.ipynb　…　部品2
- parse_grantaward_member_from_summary.ipynb　…　部品3
- parse_grantaward_integration.ipynb　…　3つの部品を統合する

1の設定ファイルさえ作れば、2と3は順不同です。
