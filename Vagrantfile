# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box_url = "https://vagrantcloud.com/ubuntu/trusty64"
  config.vm.box = "ubuntu/trusty64"

  config.vm.hostname = "bim-service"
  config.vm.network :private_network, ip: "10.0.0.115"

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
  end

  if Vagrant.has_plugin?("vagrant-cachier")
    config.cache.scope = :machine
  end

  config.vm.synced_folder ".", "/vagrant", :nfs => true

  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "4096"]
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
  end

end
