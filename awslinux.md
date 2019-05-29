```
vagrant up
vagrant ssh
```

swith to root user
```
sudo su
```

yum update
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


postgresql96 install
```
sudo yum install -y postgresql96 postgresql96-server postgresql96-libs postgresql96-contrib

sudo service postgresql96 initdb
sudo service postgresql96 start
sudo chkconfig postgresql96 on

#confirm
sudo -u postgres -i psql -c 'SELECT version();'
```

eidt postgresql conf file
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
¥d
gzip -cd /path/to/dump.gz | psql -d "DBNAME"
exit

```



ruby install
```
git --version

#if git hasnt installed yet
sudo yum install -y git

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

```



```
//
sudo yum -y install postgresql96-devel
sudo yum install -y devtoolset-7-gcc-c++ devtoolset-7-make devtoolset-7-build
sudo yum -y install gcc72-c++.x86_64
scl enable devtoolset-7 bash

gem install pg -- --with-pg-config=/usr/bin/pg_config

//
cd path/to/mentough_common/
cp config/settings.local.yml.sample config/settings.local.yml


cd path/to/MTOP2/
cp config/database.yml.example config/database.yml
cp config/settings.local.yml.sample config/settings.local.yml

bundle install

rails db:migrate

//
cd path/to/mentough/
cp config/database.yml.sample config/database.yml
cp config/settings.local.yml.sample config/settings.local.yml

bundle install


cd path/to/MTOP2
rails s -b 0.0.0.0

//open other bash window
cd path/to/mentough
rails s -b 0.0.0.0 -p 3001

http://127.0.0.1:3000
```



```
#PhantomJS

cd /tmp
sudo yum install -y fontconfig freetype freetype-devel fontconfig-devel libstdc++
#wget https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-1.9.8-linux-x86_64.tar.bz2
wget https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-2.1.1-linux-x86_64.tar.bz2

sudo mkdir -p /opt/phantomjs
bzip2 -d phantomjs-2.1.1-linux-x86_64.tar.bz2
sudo tar -xvf phantomjs-2.1.1-linux-x86_64.tar --directory /opt/phantomjs/ --strip-components 1
sudo ln -s /opt/phantomjs/bin/phantomjs /usr/bin/phantomjs

phantomjs /opt/phantomjs/examples/hello.js


#Japanese Fonts
sudo yum install -y ipa-gothic-fonts.noarch
sudo yum install -y ipa-mincho-fonts.noarch
```
