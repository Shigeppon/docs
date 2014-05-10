# 概要
Vagrantで作成した仮想環境に対してChef-Solo(Kine-Solo)を使って環境設定をする。

## 管理サーバーへ必要なソフトのインストール
* chef/knife-soloのインストール  

```bash
$ gem install chef
$ gem install knife-solo
```

## ノード用リポジトリの準備
* knife solo init  

```bash
$ knife solo init chef-repo
$ cd chef-repo
$ git init
$ git add .
$ git commit -m "initial commit"
```

## ノードの作成
* knife solo prepare  

```bash
$ knife solo prepare <host>
```

## cookbookの作成
* knife cookbook create

```bash
$ knife cookbook create hello -o site-cookbooks
```

## レシピの反映

```bash
$ knife solo cook test01
```
## 嵌ったこと
### not_ifが効かない
* 概要
gitをインストールするレシピを作成し、既に特定のバージョンがインストールされている場合にはインストールを行わないようにしたいため、`not_if`を使ってみたがインストールスクリプトが動いてしまう。
* 解決方法
gitへのパスをフルパスにしたところ想定通りに動くようになった。
デフォルトで入っていたgitが使われていたのだと思うが、原因はまだわからない。
* 修正前

```bash
not_if "git --version | grep -q '1.8.4'"
```
* 修正後

```bash
not_if "/usr/local/bin/git --version | grep -q '1.8.4'"
```

* 参考URL
[chef install and update programs from source](http://stackoverflow.com/questions/8530593/chef-install-and-update-programs-from-source)

## Berkshelf
[Berkshelf v3入門](http://qiita.com/DQNEO/items/9adcbd69ecaa62fbef41)

## user管理をchefでやってみる
* 参考URL
[さくらVPSの初期設定をChefSoloを使ってやってみた](http://tsuchikazu.net/vps_chef_solo/)
