Vagrant + VirtualBox 環境構築

インストール手順：
Vagrant：
https://www.vagrantup.com/downloads.html
vagrant-vbguest：
vagrant plugin install vagrant-vbguest
VirtualBox：
https://www.virtualbox.org/wiki/Downloads
CentOS Boxファイル：
https://app.vagrantup.com/boxes/search

バージョン確認：
vagrant -v

仮想マシン構築例：
①Boxファイルを探して、コマンドが見つかれる。
　https://app.vagrantup.com/boxes/search
　新規作成用のコマンド：
　vagrant init mvbcoding/awslinux
　vagrant up

②フォルダー作成
　mkdir C:\Vagrant & cd C:\Vagrant
　mkdir awslinux & cd awslinux

③Vagrant初期化を実行
　vagrant init mvbcoding/awslinux

④Vagrantfile編集
　config.vm.network "private_network", ip: "192.168.33.10"
  '↑ここのコメントアウトを外す'

⑤仮想マシンを起動
　vagrant up
　vagrant box list

⑥SSHログイン
　vagrant ssh

Ruby環境構築：
https://github.com/ouin-tci/centos6.5/blob/master/awslinux.md

FAQ：
・/sbin/mount.vboxsf: mounting failed with the error: No such device
vagrant upで上記エラーが発生する場合、
vagrant plugin install vagrant-vbguest
vagrant vbguest --status
バージョン差異がある場合：
vagrant vbguest --do install
vagrant vbguest --status


参照サイト：
https://qiita.com/ozawan/items/160728f7c6b10c73b97e
http://motomichi-works.hatenablog.com/entry/2018/09/08/200927
