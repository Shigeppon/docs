# 概要
Vagrantで作成した仮想環境に対してChef-Solo(Kine-Solo)を使って環境設定をする。

## 管理サーバーへ必要なソフトのインストール
* chef/knife-soloのインストール  
```bash
$ gem install chef
$ gem install kinfe-solo
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

## cookbookの作成
* knife cookbook create <cookbookName> -o <cookbooksDirectory>
```bash
$ knife cookbook create hello -o site-cookbooks
```

