# AWSLinux+Ruby on Rails環境構築

## 仮想マシンの新規作成
```
下記手順参照して、仮想マシンを起動する。
https://github.com/gilliandoi/guidebook/blob/master/Vagrant+VirtualBox環境構築.md
vagrantfile：
https://github.com/gilliandoi/guidebook/blob/master/Vagrantfile
```

## SSHログイン
```
vagrant ssh
```

## ルートユーザーに切り替え
```
sudo su
```

## yum UPDATE
```
vi /etc/yum.conf


//press a key switch insert mode, then goto 19th line
#releasever=latest
↓
releasever=latest

:wq

yum -y update
exit
```

## postgresql96インストール
```
sudo yum install -y postgresql96 postgresql96-server postgresql96-libs postgresql96-contrib

sudo service postgresql96 initdb
sudo service postgresql96 start
sudo chkconfig postgresql96 on

#confirm
sudo -u postgres -i psql -c 'SELECT version();'
```
設定ファイル変更：
```
sudo vi /var/lib/pgsql96/data/postgresql.conf 
listen_addresses = 'localhost'
↓
listen_addresses = '*' 
port = 5432

:wq

sudo vi /var/lib/pgsql96/data/pg_hba.conf 
//modify
# IPv4 local connections:
host    all         all         127.0.0.1/32          trust
host    all         all         0.0.0.0/0             trust
:wq

sudo service postgresql96 restart
//change password to 'postgres'
sudo passwd postgres

sudo su - postgres
psql
CREATE DATABASE "DBNAME";
¥l
¥q
gzip -cd /path/to/dump.gz | psql -d "DBNAME" ←dumpファイルからインポートの場合のみ必要
exit
```

## rubyインストール
```
git --version
git clone https://github.com/sstephenson/rbenv.git ~/.rbenv

git clone git://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build

echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bash_profile
echo 'eval "$(rbenv init -)"' >> ~/.bash_profile
source ~/.bash_profile

rbenv -v

sudo yum install -y openssl-devel readline-devel

rbenv install 2.4.4
rbenv global 2.4.4
ruby -v

gem install bundler
gem install rails
sudo yum install -y sqlite-devel

sudo yum -y install postgresql96-devel
sudo yum -y install gcc72-c++.x86_64

gem install pg -- --with-pg-config=/usr/bin/pg_config
```

## railsからプロジェクト作成
```
rails new hello_app
cd hello_app/
bundle install
rails s -b 0.0.0.0　←アプリ起動
※bundle installでExecJS::RuntimeUnavailableエラーが発生する場合、
　Gemfileにgem 'therubyracer'という記述を追加して、
　bundle update以降の手順を同様に実行する。
```

## 画面にアクセスして動作確認
http://localhost:3000/

## 参照サイト：
```
Rubyの実行環境構築 on Windows
https://qiita.com/3no3_tw/items/8c0bcf258370d91bf6e0

Ruby on rails
https://railstutorial.jp

nodejs
https://nodejs.org/ja/download/

railsからソース生成
https://techacademy.jp/magazine/7204
https://qiita.com/zaru/items/cde2c46b6126867a1a64
```


