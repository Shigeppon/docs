# vagrantを使ってみる
* vagrantのインストール

```bash
$ gem install vagrant
$ rbenv rehash

```
* vagrant用OSイメージのダウンロード

```bash
$ vagrant box add base http://developer.nrel.gov/downloads/vagrant-boxes/CentOS-6.3-x86_64-v20130101.box
```
* 仮想サーバーの起動

```bash
$ cd your/virtual/server/directory
$ vagrant init
$ vim Vagrantfile
Vagrant::Config.run do |config|
config.vm.box = "base"
config.vm.network :hostonly,"192.168.50.12"
$ vagrant up
```
## sshでアクセス出来るようにする
* ssh_configの変更

```bash
$ vim ~/.ssh/config
Host test01
    HostName        192.168.50.12
    IdentityFile    ~/.vagrant.d/insecure_private_key
    User            vagrant
```
