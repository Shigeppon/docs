# CentOS6.5へgit1.9.0をインストールする
vagrantで作成したCentOS6.5のgitが1.7だったため、gitconfigにpush.simpleを指定してあるとwarningを出すので、
1.9にすることにした。
```bash
$wget https://git-core.googlecode.com/files/git-1.9.0.tar.gz
$ tar xvzf git-1.9.0.tar.gz
$ cd git-1.9.0
$ ./configure --prefix=/usr/local --with-curl
$ sudo yum install zlib-devel
$ sudo yum install perl-ExtUtils-MakeMaker
$ sudo yum install curl-devel
$ make
$ sudo make install
$ bash
$ git --version
git version 1.9.0
```

- --with-curl
rbenvをgit clone しようとしたら以下のエラーが出た。
```bash
$ git clone https://github.com/sstephenson/rbenv.git ~/.rbenv
fatal: Unable to find remote helper for 'https'
```
gitのコンパイル時にcurlライブラリをリンクできていなかったのが原因なので、curl-develをインストール後--with-curlをつけconfigureする。


# コマンド補完とbashへのブランチ表示
* git-completion.bashとgit-prompt.sh
[git/gitリポジトリ](https://github.com/git/git.git)
をダウンロードし.bashrcから読み込むようにする。

```bash
source ~/.git-completion.bash
source ~/.git-prompt.sh
GIT_PS1_SHOWDIRTYSTATE=true
export PS1='\[\033[32m\]\u@\h\[\033[00m\]:\[\033[34m\]\w\[\033[31m\]$(__git_ps1)\[\033[00m\]\$ '
```

# git add . と git add -uの違い
* git add .  
ファイルの更新と追加をインデックスへ反映する。
削除は反映しない。
* git add -u  
ファイルの更新と削除をインデックスへ反映する。
ファイルの追加は反映しない。
* git add -A  
追加、変更、削除全てをインデックスへ反映する。

## 参考URL
[Difference of “git add -A” and “git add .”](http://stackoverflow.com/questions/572549/difference-of-git-add-a-and-git-add)

# Macのgitを1.8にする
* homewbrewでインストール
```bash
$ git --version
git version 1.7.12.4 (Apple Git-37)
$ brew update
$ brew install git
$ git --version
git version 1.7.12.4 (Apple Git-37)
```
* pathの参照順序を変更  
/usr/local/binを最初へ
```bash
$ sudo vim /etc/paths
/usr/local/bin
/usr/bin
/bin
/usr/sbin
/sbin
```
ターミナルを再起動
```bash
$ git --version
git version 1.8.4
```

## 参考URL  
[mac標準ではなくhomebrewのgit1.8〜を使うためにやったこと](http://qiita.com/kony/items/ec5758b72f6799f209d3)

# GitHubで管理していない既存のGitリポジトリをGitHubに追加する
* GitHubでリポジトリを作成
今回はgit_testという名前にしてみる
* LocalのGitでリモートリポジトリの追加

```bash
$ cd local/repository
$ git remote add origin git@gihub.com:Shigeppon/git_test.git
$ git push origin master
```

## 参考URL
[[github] gitの使いかた](http://za.toypark.in/html/2009/02-19.html)
