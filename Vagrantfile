# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure('2') do |config|
	# https://app.vagrantup.com/suse/boxes/sles12sp1
  config.vm.box = "suse/sles12sp1"
  config.vm.box_version = "0.0.1"

	  # 1台目管理マシン（マシン名：master）
  config.vm.define "master" do |atomic|
     atomic.vm.hostname = "sl12sv01"
     #atomic.vm.synced_folder ".", "/vagrant", disabled: true
     #atomic.vm.network :forwarded_port, id: "ssh", guest: 22, host: 2222
     #atomic.vm.network "private_network", ip: "192.168.33.100", virtualbox__intnet: "intra"
	atomic.vm.network "private_network", ip: "192.168.33.100"
  end
  # 2台目 コンテナホスト（マシン名：node01）
  config.vm.define "node01" do |atomic|
     atomic.vm.hostname = "sl12sv02"
     #atomic.vm.synced_folder ".", "/vagrant", disabled: true
     #atomic.vm.network :forwarded_port, id: "ssh", guest: 22, host: 2223
     #atomic.vm.network "private_network", ip: "192.168.33.101", virtualbox__intnet: "intra"
	 atomic.vm.network "private_network", ip: "192.168.33.101"
	 atomic.vm.provider "virtualbox" do |v| 
        v.customize ["modifyvm", :id, "--memory", 512] 
		v.disksize.size = '100GB' 
        #v.name = "node01" 
    end
  end
end
