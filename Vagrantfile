# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "chef_aem_author"
  config.vm.box_url="file:///C:/Users/cyberlync/Documents/cylysetup/bento/builds/centos-7.2.virtualbox.box"
  config.vm.hostname="aem-author"
  config.vm.network "forwarded_port", guest: 80, host: 8081
  config.vm.network "forwarded_port", guest: 4502, host: 4502
  config.vm.network "private_network", ip: "192.55.30.55"

  config.vm.provision :chef_client do |chef|
    chef.chef_server_url = "https://api.chef.io/organizations/cyly"
    chef.validation_key_path = "./.chef/cyly-validator.pem"
    chef.validation_client_name = "cyly-validator.pem"
    chef.node_name = "authorNode"
  end
end
