# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
	config.vm.box = "centos/6"

	config.vm.network "forwarded_port", guest: 80, host: 8000
	config.vm.network "private_network", ip: "192.168.33.10"
	# config.vm.network "public_network"

	config.vm.synced_folder ".", "/vagrant", mount_options: ['dmode=755','fmode=755']

	config.vm.provider "virtualbox" do |vb|
		vb.memory = "1024"
	end

	config.vm.provision :ansible_local do |ansible|
		ansible.playbook = 'playbook.yml'
		ansible.limit = 'all'
		ansible.verbose = true
		ansible.install = true
		ansible.inventory_path = "hosts"
	end
end
