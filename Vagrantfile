# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "precise64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"
  config.vm.provider "virtualbox" do |v|
    v.customize ["modifyvm", :id, "--cpus", "2"]
    v.customize ["modifyvm", :id, "--memory", "1024"]
  end

  config.vm.define "zk" do |zk|
    zk.vm.hostname = "zookeeper"
    zk.vm.network  :private_network, ip: "192.168.50.4"
    zk.vm.provision :puppet, :module_path => "modules" do |puppet|
     puppet.manifests_path = "manifests"
     puppet.manifest_file  = "zookeeper.pp"
    end
  end

  config.vm.define "solr" do |solr|
    solr.vm.hostname = "solr"
    solr.vm.network  :private_network, ip: "192.168.50.5"
    solr.vm.provision :puppet, :module_path => "modules" do |puppet|
     puppet.manifests_path = "manifests"
     puppet.manifest_file  = "default.pp"
    end
  end
end
