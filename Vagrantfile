# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "precise64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"

  config.vm.network :private_network, ip: "10.0.121.3"
  config.vm.network :public_network if ENV["PUBLIC"]

  root = "/opt/src"
  config.vm.synced_folder ".", root, :nfs => true

  config.ssh.forward_agent = true

  cpus = 2
  memory = ENV["MEMORY"] ? ENV["MEMORY"] : "2048"

  config.vm.provider :virtualbox do |vb|
    vb.gui = true if ENV["DEBUG"]
    vb.customize ["modifyvm", :id, "--memory", memory]
    vb.customize ["modifyvm", :id, "--cpus", cpus]
  end

  config.vm.provision :ansible do |ansible|
    ansible.playbook = "home-server.yml"
    ansible.inventory_path = "inventory/dev"
    ansible.verbose = "v"
  end

  if defined? VagrantPlugins::Cachier
    config.cache.auto_detect = true
  end
end