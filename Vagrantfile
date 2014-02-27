# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "centos6.5"
  config.vm.network :forwarded_port, host: 8080, guest: 80
  config.vm.network :private_network, ip: "192.168.1.11"
  config.vm.provision "ansible" do |ansible|
    ansible.inventory_path = "provision/vagrant"
    ansible.playbook = "provision/site.yml"
    ansible.verbose = "v"
  end
  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "2048"]
    vb.customize ["modifyvm", :id, "--natdnsproxy1", "off"]
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "off"]
  end
end
