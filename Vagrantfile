# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define "control" do |control|
    control.vm.box = "ubuntu/precise64"
    control.vm.network "private_network", ip: "192.168.33.10"
    control.vm.hostname = "control"
    control.vm.synced_folder ".", "/vagrant", type: "nfs"
    control.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--name", "control"]
      vb.memory = "1024"
    end
    control.vm.provision "shell", inline: <<-SHELL
      #sudo apt update -y
      #sudo apt install software-properties-common -y
      #sudo apt-add-repository --yes --update ppa:ansible/ansible -y
      #sudo apt install ansible
      sudo apt-get install software-properties-common -y
      sudo apt-add-repository ppa:ansible/ansible
      sudo apt-get update -y
      sudo apt-get install ansible -y
    SHELL
  end

    config.vm.define "web01" do |web01|
      web01.vm.box = "ubuntu/precise64"
      web01.vm.network "private_network", ip: "192.168.33.11"
      web01.vm.hostname = "web01"
      web01.vm.synced_folder ".", "/vagrant", type: "nfs"
      web01.vm.provider "virtualbox" do |vb|
        vb.customize ["modifyvm", :id, "--name", "web01"]
        vb.memory = "1024"
      end
    end

end
