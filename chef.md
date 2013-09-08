# 概要
Vagrantで作成した仮想環境に対してChef-Solo(Kine-Solo)を使って環境設定をする。

## 管理サーバーへ必要なソフトのインストール
* chef/knife-soloのインストール
```bash
$ gem install chef
```

## ノード用リポジトリの準備
* knife solo init

## ノードの作成
* knife solo prepare
