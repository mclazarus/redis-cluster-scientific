# -*- mode: ruby -*-
# vi: set ft=ruby :

vagrant_box = "rafacas/centos64-plain"

VAGRANTFILE_API_VERSION = "2"

Vagrant.require_version ">= 1.5.0"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.define "db01" do |db01|
    db01.vm.hostname = "db01"
    db01.omnibus.chef_version = :latest
    db01.vm.box = vagrant_box
    db01.vm.network :private_network, ip: "192.168.255.51"
    db01.vm.provision :chef_solo do |chef|
      chef.cookbooks_path = ["cookbooks", "site-cookbooks"]
      chef.data_bags_path = "data_bags"
      chef.roles_path = "roles"
      chef.json = {
      }
      
      chef.run_list = [ "role[redis-node]" ]
    end
  end

  config.vm.define "db02" do |db02|
    db02.vm.hostname = "db02"
    db02.omnibus.chef_version = :latest
    db02.vm.box = vagrant_box
    db02.vm.network :private_network, ip: "192.168.255.52"
    db02.vm.provision :chef_solo do |chef|
      chef.cookbooks_path = ["cookbooks", "site-cookbooks"]
      chef.data_bags_path = "data_bags"
      chef.roles_path = "roles"
      chef.json = {
      }
      
      chef.run_list = [ "role[redis-node]" ]
    end
  end

end
