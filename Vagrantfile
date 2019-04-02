# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure("2") do |config|
  config.vm.hostname = "vagrant-local-awslinux-2018"
  config.vm.box = "mvbcoding/awslinux"
  config.disksize.size = '16GB'

  config.vm.synced_folder ".", "/vagrant", nfs: true
  config.vm.synced_folder "C:/work/workspace/hello_app/", "/home/hello_app", nfs: true
  
  config.vm.network :private_network, ip: "192.168.33.12"

  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--memory", 2048]
    # XXX improve network speed. http://qiita.com/s-kiriki/items/357dc585ee562789ac7b
    vb.customize ["modifyvm", :id, "--natdnsproxy1", "off"]
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "off"]
    vb.name = "local-awslinux-2018_ip_12"
  end

  config.vm.network :forwarded_port, guest: 3000, host: 3000
  config.vm.network :forwarded_port, guest: 3001, host: 3001
  config.vm.network :forwarded_port, guest: 3002, host: 3002
  config.vm.network :forwarded_port, guest: 3003, host: 3003
  config.vm.network :forwarded_port, guest: 5432, host: 4432
  config.vm.network :forwarded_port, guest: 1080, host: 1080
end
