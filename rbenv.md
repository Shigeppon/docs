* インストール済み（切り替え可能な）rubyのバージョンを確認
```bash
$ rbenv versions
* 1.9.3-p392 (set by /Users/shigeo/.rbenv/version)
```
* インストール可能なrubyのバージョン
```bash
$ rbenv install --list
1.9.3-rc1
2.0.0-dev
2.0.0-p0
2.0.0-p195
2.0.0-p247
```
* 2.0.0-p247をインストール
```bash
$ rbenv install 2.0.0-p247
$ rbenv rehash
$ rbenv global 2.0.0-p247
```
* バージョンの確認
```bash
$ rbenv version
2.0.0-p247 (set by /Users/shigeo/.rbenv/version)
```

## 参考URL
* [rbenv で ruby のバージョン管理をする（Mac）](http://blog.twiwt.org/e/66a1d0)  
Homebrewを使ったrbenvのインストール、よく使うコマンドの説明など。
* [CentOSでsystem wideなrbenv+ruby-build環境を構築する](http://nomnel.net/blog/centos-system-wide-rbenv-and-ruby-build/)  
CentOSでのSystemWideなrbenv

* [CentOS 6.3にシステムワイドなrbenv+ruby-buildの環境を構築する手順](http://qiita.com/s-yamaz@github/items/c2377c45d6c4fbfd775f)  
sudo時にPATHを引き継ぐ設定

## shebang(シェバン)
rbenvにてrubyをインストールすると、rubyの実行ファイルが以下のようになり、シェルスクリプトでどのようにシェバンを指定するのかちょっとわからなかった。
```bash
$ which ruby
/Users/shigeo/.rbenv/shims/ruby
```
結局はenvユーティリティを使う事でOKだと思いだした。
```bash
$ cat hoge.rb
#!/usr/bin/env ruby
print "#{RUBY_VERSION¥n}"
```
