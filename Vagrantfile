# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  
  config.vm.define :chef_aem_author do |author|
  author.vm.box = "chef_aem_author"
  author.vm.box_url="file:///C:/Users/cyberlync/Documents/cylysetup/bento/builds/centos-7.2.virtualbox.box"
  author.vm.hostname="aem-author"
  author.vm.network "forwarded_port", guest: 4502, host: 4502
  author.vm.network "private_network", ip: "192.168.30.55"

  config.vm.provision :chef_client do |chef|
    chef.chef_server_url = "https://api.chef.io/organizations/cyly"
    chef.validation_key_path = "./.chef/cyly-validator.pem"
    chef.validation_client_name = "cyly-validator"
    chef.node_name = "Node-Author"
    chef.environment = "development"
  end  
  end

  config.vm.define :chef_aem_publish do |publish|
  publish.vm.box = "chef_aem_publish"
  publish.vm.box_url="file:///C:/Users/cyberlync/Documents/cylysetup/bento/builds/centos-7.2.virtualbox.box"
  publish.vm.hostname="aem-publish"
  publish.vm.network "forwarded_port", guest: 4503, host: 4503
  publish.vm.network "private_network", ip: "192.168.30.60"

  config.vm.provision :chef_client do |chef|
    chef.chef_server_url = "https://api.chef.io/organizations/cyly"
    chef.validation_key_path = "./.chef/cyly-validator.pem"
    chef.validation_client_name = "cyly-validator"
    chef.node_name = "Node-Publish"
    chef.environment = "development"
  end  
  end

  config.vm.define :chef_jenkins_slave do |jenkins|
  jenkins.vm.box = "chef_jenkins_slave"
  jenkins.vm.box_url="file:///C:/Users/cyberlync/Documents/cylysetup/bento/builds/centos-7.2.virtualbox.box"
  jenkins.vm.hostname="jenkins-slave"
  jenkins.vm.network "forwarded_port", guest: 8080, host: 8181
  jenkins.vm.network "private_network", ip: "192.168.30.65"

  config.vm.provision :chef_client do |chef|
    chef.run_list = ["recipe[jenkins::java]", "recipe[jenkins::master]"]
  end  
  end
end
