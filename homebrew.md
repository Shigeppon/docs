# 概要
ruby製のmacパッケージ管理ツール
## MacPortsとの違いは
* 依存関係でインストールされるソフトが少ない  
MacPortsは依存するソフトを新規にインストールするが、Homebrewは既にあるものはそれを使うように設計されている。
* インストールユーザー  
MacPortsはスーパーユーザーで実行する必要があるが、Homebrewは一般ユーザーでインストールすることが出来る。
* インストールされるディレクトリ  
MacPortsは/opt/localにインストールされるが、Homebrewは/usr/local/以下にインストールされる。

## インストール方法
[Ruby on Rails 3.2 を Mac OS X にインストールする手順をかなり丁寧に説明してみました](http://www.oiax.jp/rails/zakkan/rails_3_1_installation_on_macosx.html)
[2012-11-27 Mountain Lion に Ruby 1.9.3 & Rails 3.2.8 をインストールした](http://d.hatena.ne.jp/ke-16/20121127)  
homebrewの利用準備

# 使い方
## パッケージ状態の診断
```bash
$ brew doctor
```
## update  
```bash
$ brew update
```
# 参考サイト  
* [ＨｏｍｅＢｒｅｗの仕組みについてまとめておく](http://takuya-1st.hatenablog.jp/entry/20111224/1324750111)  
インストール方法から基本的な使い方まで。ここ見れば十分。
* [Homebrewの導入と使い方](http://tech.caph.jp/2011/04/06/homebrew%E3%81%AE%E5%B0%8E%E5%85%A5%E3%81%A8%E4%BD%BF%E3%81%84%E6%96%B9/)  
コマンド一覧と簡単な説明がある

